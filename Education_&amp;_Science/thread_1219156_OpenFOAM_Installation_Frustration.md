---
title: "OpenFOAM Installation Frustration"
date: 2009-07-21
forum: Education &amp; Science
---

### Post by sumontro on 2009-07-21
I am trying to install OpenFOAM-1.5 on my desktop, which runs Ubuntu 9.04. I followed the installation instructions but I keep getting hung up on the last step. I try to source the bashrc file first, but it gives me this output. 

[B]sumontro@ubuntu:~$ source $HOME/OpenFOAM/OpenFOAM-1.5/etc/bashrc

Warning in /home/sumontro/OpenFOAM/OpenFOAM-1.5/etc/settings.sh:
    Cannot find /home/sumontro/OpenFOAM/ThirdParty/gcc-4.3.1/platforms/linux installation.
    Please install this compiler version or if you wish to use the system compiler,
    change the WM_COMPILER_INST setting to 'System' in this file

bash: ./home/sumontro/OpenFOAM/OpenFOAM-1.5/etc/bashrc: No such file or directory[/B]

then I change the compiler to system and this is what I get

[B]sumontro@ubuntu:~$ source $HOME/OpenFOAM/OpenFOAM-1.5/etc/bashrc
bash: ./home/sumontro/OpenFOAM/OpenFOAM-1.5/etc/bashrc: No such file or directory[/B]

I have no idea what I am doing wrong. I am an extremely new user to Linux and I have very little programming experience. However, I need to get OpenFOAM working. I would really appreciate the help.

---

### Post by dandiwijaya on 2009-10-19
try this script bro...!!!

#!/bin/bash
# Created by Mads Reck (madstmp (a-t) gmail.com)
# September 2009
# Revision 03
#
echo "-----------------------------------------------------"
echo " 32 BIT VERSION"
echo "   32 BIT VERSION"
echo "     32 BIT VERSION"
echo "-----------------------------------------------------"
echo "Making sure that you have all needed libraries"
echo "-----------------------------------------------------"
echo "Apparently we need to run apt-get multiple times to  "
echo " be SURE that everything is installed                "
sudo apt-get install flex git git-core build-essential python-dev libqt4-dev libreadline5-dev wget zlib1g-dev
sudo apt-get install flex git git-core build-essential python-dev libqt4-dev libreadline5-dev wget zlib1g-dev
sudo apt-get install flex git git-core build-essential python-dev libqt4-dev libreadline5-dev wget zlib1g-dev
cd ~
mkdir OpenFOAM
cd OpenFOAM
echo "------------------------------------------------------"
echo "Downloading ThirdParty stuff"
echo "------------------------------------------------------"
wget [http://downloads.sourceforge.net/foam/ThirdParty-1.6.General.gtgz?use_mirror=mesh](http://downloads.sourceforge.net/foam/ThirdParty-1.6.General.gtgz?use_mirror=mesh)
wget [http://downloads.sourceforge.net/foam/ThirdParty-1.6.linuxGcc.gtgz?use_mirror=mesh](http://downloads.sourceforge.net/foam/ThirdParty-1.6.linuxGcc.gtgz?use_mirror=mesh)
echo "------------------------------------------------------"
echo "Untarring - this takes a while..."
echo "------------------------------------------------------"
tar xfz ThirdParty-1.6.General.gtgz 
tar xfz ThirdParty-1.6.linuxGcc.gtgz
echo "------------------------------------------------------"
echo "Retrieveing OpenFOAM..."
echo "------------------------------------------------------"
ln -s  ~/OpenFOAM/ThirdParty-1.6 ~/OpenFOAM/ThirdParty-1.6.x
git clone git://repo.or.cz/OpenFOAM-1.6.x.git 
cd OpenFOAM-1.6.x/
git pull
. ~/OpenFOAM/OpenFOAM-1.6.x/etc/bashrc 
echo . ~/OpenFOAM/OpenFOAM-1.6.x/etc/bashrc >> ~/.bashrc
echo "------------------------------------------------------"
echo "Compiling OpenFOAM...output is in make.log"
echo "------------------------------------------------------"
 ./Allwmake >make.log 2>&1
echo "------------------------------------------------------"
echo "Checking installation - you should see NO criticals..."
echo "------------------------------------------------------"
foamInstallationTest

---

### Post by jeneverboy on 2009-10-20
Hey,

I followed this installation guide step-by-step:
[http://energy.tf.itb.ac.id/index.php/lang-en/cfd]("http://energy.tf.itb.ac.id/index.php/lang-en/cfd")
had no problems.

I am a new user of linux also. I found the examples in the OpenFOAM directory to be very useful.

Good luck!

---

### Post by Hachi-Roku on 2009-11-27
Anyone use that script posted??? feedback?? it looks pretty comprehensive!

Ive just installed OF and i cant even open the installation test file due to permissions.
i try to open it as root and still doesnt work.

Anyone come across this problem?

---

### Post by Hachi-Roku on 2009-11-28
So i wickedly modified the script (as i'd already dl'd the zip files tec) and ran it.
Been in the 'compiling' stage now for about 2 hours. up to line 7050 in make.log so i guess thats understandable. hopefully it finishes soon.

Massive thanks for the script! Ill post back if i get a working copy of OF at the end of it.

---

