---
title: "Remove Easy Breezy"
date: 2006-03-04
forum: Desktop Environments
---

### Post by opticyclic on 2006-03-04
I tried using Easy Breezy to install Azureus before I found Automatix and other ways to install it.

Now I want to remove Easy Breezy from my computer.

However, I don't fully understand what the install script has done.
Is it enough to just remove the $HOME/easybreezy and $HOME/easybreezy-logs directories and use smeg to remove the icon from the system tools menu?
```
#!/bin/bash
####################
# This utility is a script with a gui interface for selecting and installing
# common packages, not installed by default or in the repositories. 

# (c)2005 Venkat "robotgeek" Raghavan <venkatraghavan@gmail.com>
# Thanks to Nalioth for motivation, and support
# Thanks to kkhatman for the icon
# EasyBreezy is released under the GPL
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# as published by the Free Software Foundation; either version 2
# of the License, or (at your option) any later version.
# 
# Instructions for use:
# 1. Make sure you have dialog installed 'sudo apt-get install dialog'
# 2. Run the install script, by going to the EasyBreezy directory and typing
# ./install
# 3. Run from your menu System Tools -> Easy Breezy
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA  02111-1307, USA.
###################

# Non-root check
if ! [[ $UID = 0 ]]; then
    echo 'You should run the install using sudo. Try 'sudo ./install''
    exit 1
fi

echo "removing easybreezy v 0.33 and below"
rm -rf $HOME/easybreezy
rm -f $HOME/.local/share/applications/EasyBreezy.desktop
rm -f $HOME/.local/share/pixmaps/EasyBreezy.xpm
cat $HOME/.bashrc | sed  's/export PATH=$HOME\/easybreezy:${PATH}//g' > $HOME/.bashrc

install_dir=/usr/share/easybreezy
rm -rf $install_dir
rm -f /usr/local/bin/EasyBreezy

mkdir -p $install_dir
mkdir -p $HOME/easybreezy
chown -R $SUDO_USER $HOME/easybreezy

# Move the icon related stuff
cp -f conf/EasyBreezy.desktop /usr/share/applications/
cp -f conf/EasyBreezy.xpm /usr/share/pixmaps/

cp -f conf/apt.conf $install_dir/
#recreate a basic sources.list
echo "Creating a sources.list based on your location"
cat /etc/apt/sources.list | grep "breezy main restricted" | sed  's/breezy main restricted/breezy main restricted universe multiverse/g' | sudo tee $install_dir/sources.list

# copy arch specific things
if uname -r | grep -iq "powerpc"   
then
    # do ppc related stuff
    #echo "powerpc detected."
echo "deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free" | sudo tee -a $install_dir/sources.list
echo "deb http://deb.opera.com/opera etch non-free" | sudo tee -a $install_dir/sources.list

cp -f conf/EasyBreezy_ppc $install_dir/EasyBreezy
fi

if  uname -r | egrep -iq "386|686|k7" 
then
    # do x86 installation related stuff
    #echo "x86 detected"
echo "deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free" | sudo tee -a $install_dir/sources.list
echo "deb http://wine.sourceforge.net/apt/ binary/" | sudo tee -a $install_dir/sources.list
echo "deb http://deb.opera.com/opera etch non-free" | sudo tee -a $install_dir/sources.list

cp -f conf/EasyBreezy_x86 $install_dir/EasyBreezy
fi

if uname -r | grep -iq "amd64"   
then
    # do amd64 stuff
    #echo "amd64 detected"
cp -f conf/EasyBreezy_amd $install_dir/EasyBreezy
fi

ln -s  $install_dir/EasyBreezy /usr/local/bin/EasyBreezy

if ! dpkg -l dialog | grep -q "ii"
then
    echo "You must install 'dialog' for EasyBreezy to work. This install will install it for you. "
    sudo apt-get install dialog
fi
echo "*****"
echo "EasyBreezy has been installed. You may run EasyBreezy by simply typing \"EasyBreezy\" in a terminal, or by selecting \"System -> EasyBreezy\" from your menu." 
echo "*****"

```

---

### Post by Sutekh on 2006-03-05
I'm afraid I don't really know.   Is there an uninstall script in the folder where you extracted the Easy Breezy files?  It may be enough to just remove the folders and the menu entry.

Easy Breezy has become part of Easy Ubuntu.  Ask this question in the separate forum for [Easy Ubuntu]("http://ubuntuforums.org/forumdisplay.php?f=86") and hopefully robotgeek (the author), or someone else can help you out.

---

