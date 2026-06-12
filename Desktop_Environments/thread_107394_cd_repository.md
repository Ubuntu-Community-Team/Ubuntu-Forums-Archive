---
title: "cd repository"
date: 2005-12-22
forum: Desktop Environments
---

### Post by matthewstory on 2005-12-22
I've got my friend running a breezy partition on his PC, but it's a stand alone computer and he needs certain packages to do what he needs to do with it.  Just wondering if there is a way to put packages on a cd so that Synaptic can apt-get and install off the cd.  Thanks.

matt

---

### Post by Sutekh on 2005-12-22
Here's a link to do that;

[Ubuntu Wiki - Apt Move HOWTO]("https://wiki.ubuntu.com/AptMoveHowto")

---

### Post by Sef on 2005-12-22
The above link does not work.  Try this link: [https://wiki.ubuntu.com/AptMoveHowto?highlight=%28Move%29%7C%28How%29%7C%28to%29%7C%28Apt%29]("https://wiki.ubuntu.com/AptMoveHowto?highlight=%28Move%29%7C%28How%29%7C%28to%29%7C%28Apt%29")

---

### Post by Sutekh on 2005-12-22
Try it now, sorry

---

### Post by Sef on 2005-12-22
That's ok.  We all have messed up at times.  (including me :oops:)

---

### Post by towsonu2003 on 2005-12-22
I've got a collection of how to deal with local repos... from other threads... Posting here so that people can read (none of the below info is my creation):
> Offline repo CD:

**ONE WAY**
I used the following script in an empty directory to gather all the packages that I have installed in it:

#!//bin/sh
dpkg --get-selections | grep -v "deinstall" | awk '{print $1}' | xargs dpkg-repack

ps. make sure that you have dpkg-repack installed before, if not, sudo apt-get install dpkg-repack. Will take a while, but it will give you all the .deb packages fresh and clean. =)

Descriptions:

dpkg --get-selections 
print out the list of installed and removed packages


grep -v "deinstall" 

Get rid of the deinstalled ones


awk '{print $1}' 

Strip off everything other than the first part - you just get the package name.


xargs dpkg-repack

Run that through dpkg-repack which repackages installed packages into the deb file. dpkg-repack creates a .deb file out of a debian package that has already been installed. If any changes have been made to the package while it was unpacked (ie, files in /etc were modified), the new package will inherit the changes.

This utility can make it easy to copy packages from one computer to another, or to recreate packages that are installed on your system, but no longer available elsewhere, or to store the current state of a package before you upgrade it. 



You will end up with all of the extra packages along with the ones you already have on the cd.
**ANOTHER WAY TO DO**

I need too glean some experience from those who have been using linux for some time. I will endeavour to explain what I want to do (based on a pure debian method) and then perhaps you can suggest some (better) ways of accomplishing the same thing on Kubuntu. 

I have a PC running linux {L} that doesn't have a dedicated access to the internet and one that is running Windows {W} (and doesn't run linux) but has a permanent connection to the internet - Uh? Yes that one is at work  (Hence the time efficient automated process). 
The Debian procedure is a s followings: 
1.{W}Download the Packages from the mirror site using wget
wget -N -nd -c -O ftp.is.co.za_linux_distributions_ubuntu_archive_di sts_dapper_main_binary-amd64_Packages.gz [ftp://ftp.is.co.za/linux/distributions/ubuntu/archive/dists/dapper/main/binary-amd64/Packages.gz](ftp://ftp.is.co.za/linux/distributions/ubuntu/archive/dists/dapper/main/binary-amd64/Packages.gz)
2.{L}Add them to the apt folder in linux
3.{L}Use synaptic to select packages I want to install so that it completes a full dependency list and tells me what package downloads are required.
4.{L}Extract that list
dpkg --get-selections > ~/home/Programs/packages.txt
5.{L}Create wget script file
awk '{print "wget -N -nd " $2 " " $1}' < /home/Programs/packages.txt > /home/Programs/wget-script.bat
6.{W}Use that script file on the winows box to download all the required packages
wget-script.bat
7.{L}Copy the packages from a flash drive to the Linux box, to a folder
/debs/binary/DebianInstall/binary/
8.{L}Run dpkg scan to update the available packages
cd /debs/binary/DebianInstall/binary/
dpkg-scanpackages unstable /dev/null | gzip > unstable/Packages.gz
9.{L}Reload packages and use synaptic to install the packages
dpkg --set-selections < ~/home/Programs/packages.txt


dpkg-scanpackages is in the dpkg-dev package
**ANOTHER WAY: **

Step one Install the apt-move package
sudo apt-get install apt-move dpkg-dev
(Or just use synaptic) 
I change the setting in /etc/apt-move.conf from 
CONTENTS=no 
to 
CONTENTS=yes
So that a file with the contents of the packages will be created. 
Step two Download the packages you want to put on the cd
In this example, we are starting from a freshly-installed system. We need to clean out the cache of packages in /var/cache/apt/archive. If you have already installed other packages, be sure that you leave them there so that they are put on your custom cd. If unsure about what dependancies you already have installed, perhaps this can be done from the live cd? 
So, delete every package in /var/cache/apt/archives. Do not delete these files manually! Instead use: 
sudo apt-get clean 
And then install (or just download the xubuntu-desktop packages) 
sudo apt-get -d install xubuntu-desktop
This will put the packages in /var/cache/apt/archives. Apt-move will look there by default. 
Step three Run apt move to create the archive structure
Make sure you have enough disk space first. 
sudo apt-move get 
sudo apt-move move
sudo apt-move packages
It would seem that some ubuntu packages are not inserted into the packages.gz file by apt-move. Is this because of some ubuntu-specific reposiitory structure? You must delete the Packages.gz file and remake it with dpkg-scanpackages. Make the directory writable and then cd into it and run: 
cd /mirrors/debian/dists/stable/main/binary-i386

sudo dpkg-scanpackages ../../../../pool/ /dev/null > Packages
You can identify the cd by making a .disk directory and making an info file in it. 
Make the /mirrors/debian direcory writable and do 
mkdir /mirrors/debian/.disk 
echo "Custom packages" $(hostname) $(date +%y%m%d) > /mirrors/debian/.disk/info
Step four Burn the cd
Copy the contents of what is contained in /mirrors/debian to a cd. 
On a non-networked ubuntu machine, you can run synaptic, insert the cd and go into Synaptic -> Edit -> Add Cdrom and it will add the contents of the cd to your repositories. 
You can also do it from the command-line with 
sudo apt-cdrom add
  good luck reading ;)

---

