# EP_Mirrors_8

下载脚本：
#!/bin/sh
mkdir md5sum
touch error.log
for i in `seq 0 6`
do
num=`printf "%02d" $i`
wget https://github.com/pbcresc/EP_Mirrors_8/raw/master/Extension_Installer.tar.gz$num
wget -P md5sum/ https://github.com/pbcresc/EP_Mirrors_8/raw/master/md5sum/Extension_Installer.tar.gz$num.md5
if [[ `md5sum Extension_Installer.tar.gz$num` != `cat md5sum/Extension_Installer.tar.gz$num.md5` ]];then
echo "Error: file Extension_Installer.tar.gz$num md5 different whith md5sum/Extension_Installer.tar.gz$num.md5!" >> error.log
fi
done
cat error.log

解压命令：
cat Extension_Installer.tar.gz* | tar -xvzf -
