---
title: "How-To install thunar-shares-plugin in xfce 4.10/4.12"
date: 2013-04-26
forum: Desktop Environments
---

### Post by dentaku65 on 2013-04-26
I really like to have in my box a simply way to share/unshare directories and have control on it directly in Thunar; I'm using Quantal Xubuntu.
Even if is possible to use a "custom actions" in order to share/unshare like stated here [http://ubuntuforums.org/showthread.php?t=1845244&p=11505823#post11505823]("http://ubuntuforums.org/showthread.php?t=1845244&p=11505823#post11505823") I don't like this kind of option.

Since that Xfce have in xfce-goodies a plugin to use samba inside Thunar [http://goodies.xfce.org/projects/thunar-plugins/thunar-shares-plugin]("http://goodies.xfce.org/projects/thunar-plugins/thunar-shares-plugin") but seems that is not mantained anymore (or simply does not works), here a way to install it from the source.

Install dependencies:
```
sudo apt-get install libglib2.0-dev xfce4-dev-tools libgtk2.0-dev libthunarx-2-dev libthunar-vfs-1-dev build-essential samba
```

Create a working directory and get the source:
```
mkdir $HOME/thunar_plugin
```
```
cd $HOME/thunar_plugin
```
```
wget http://archive.xfce.org/src/thunar-plugins/thunar-shares-plugin/0.2/thunar-shares-plugin-0.2.0.tar.gz
```
```
tar xvzf thunar-shares-plugin-0.2.0.tar.gz
```
```
cd thunar-shares-plugin-0.2.0
```

Patch the source and compile/install:
```
sed -i "s|\(thunarx-\)1|\12|g" configure{,.in} thunar-plugin/Makefile.{am,in}
```
```
sed -i "s|get_vfs_info|get_file_info|" libshares/libshares-util.c
```
```
./configure --prefix=/usr --enable-static=no
```
```
make
```
```
sudo make install
```

Configure Samba (thanks to ArchLinux wiki [https://wiki.archlinux.org/index.php/Samba#Creating_user_share_path]("https://wiki.archlinux.org/index.php/Samba#Creating_user_share_path")):
```
sudo -s
```
```
export USERSHARES_DIR="/var/lib/samba/usershares"
```
```
export USERSHARES_GROUP="sambashare"
```
```
mkdir -p ${USERSHARES_DIR}
```
```
groupadd ${USERSHARES_GROUP}
```
```
chown root:${USERSHARES_GROUP} ${USERSHARES_DIR}
```
```
chmod 01770 ${USERSHARES_DIR}
```

Then edit /etc/samba/smb.conf and under [COLOR="#FF0000"][global] [/COLOR]section paste the following and save:
> usershare path = /var/lib/samba/usershares
usershare max shares = 100
usershare allow guests = yes
usershare owner only = False

Add your user to the Samba group replacing "[COLOR="#FF0000"]your_username[/COLOR]":
```
usermod -a -G ${USERSHARES_GROUP} [COLOR="#FF0000"]your_username[/COLOR]
```

Reboot. Done!
You should have the Share tab inside the Thunar Properties of a directory 

[ATTACH=CONFIG]241800[/ATTACH]

---

