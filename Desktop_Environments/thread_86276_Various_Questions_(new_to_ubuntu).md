---
title: "Various Questions (new to ubuntu)"
date: 2005-11-04
forum: Desktop Environments
---

### Post by geir2rs1 on 2005-11-04
Hi All,
This is my first post to this forum
I am new to Ubuntu but no to linux. I have used SuSE Linux fo about 3 years.
I have not been satisfied with the package management system and that is why I will have a go for an updated debian based system. My installation is 2 days old and I do no not feel much older :) 
Comming from SuSE and Windows I feel a bit lost in the world of Debian and Gnome so pleae do not bite me off when I ask my silly questions (whisch probably have been asked 1000 times before) Hre they are:

1. How do I install debian packages not listed within synaptic (Opera we browser) :rolleyes: :confused:  I have allready downloaded a package. But then what...?

2. I know I have a firewall and that it is activated (I persume. It is Linux). But. Where is it, and how do I change settings? Open/Close ports etc.?

3. I have an external multimedia device using NTFS, so i also have two MS partitions. One containg win2000 on NTFS, and on FAT32.
How do I Read from the NTFS partition and how do I read/write to the FAT32 one?

These are my first questions. More will probably follow. 

I konw you can help:rolleyes: 

Geir

---

### Post by invalid on 2005-11-04
These are common questions and can be found an any of the ubuntu FAQ pages
[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

Cheers,
Cb

---

### Post by aysiu on 2005-11-04
[QUOTE=geir2rs1]
1. How do I install debian packages not listed within synaptic (Opera we browser) :rolleyes: :confused:  I have allready downloaded a package. But then what...?[/quote] [This link](http://www.psychocats.net/linux/installingsoftware.php) gives you a basic rundown on all the different ways to install software in Ubuntu.

> 
2. I know I have a firewall and that it is activated (I persume. It is Linux). But. Where is it, and how do I change settings? Open/Close ports etc.? Actually, I believe there is *not* a firewall in Ubuntu by default. You can install one through Synaptic, though, and I believe all ports are closed by default. You can read up more on the firewall issue in [this thread](http://ubuntuforums.org/showthread.php?t=54554).

> 
3. I have an external multimedia device using NTFS, so i also have two MS partitions. One containg win2000 on NTFS, and on FAT32. External devices should mount as readable by default. Maybe something's up with your /etc/fstab...

> 
How do I Read from the NTFS partition and how do I read/write to the FAT32 one? Generally, if they're partitions, you follow these directions:
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by Ampersand on 2005-11-04
1) If it's a debian package you've downloaded (one that ends in .deb), you an install it by opening a terminal, changing directory to the folder it's saved in (using the cd command), then running:

```
sudo dpkg -i packagename.deb
```

replacing packagename.deb with whatever the file is called (you'll be able to enter the first few letters of it, then press tab to complete it).

2) Firewalls aren't really my area, but Ubuntu by default doesn't have any open ports , so doesn't have a firewall installed. Get Firestarter from synaptic if you want to install a firewall (someone else will probably give you more details on this).

3) If you got to System - Administration - Disks from the menu at the top of your screen (if you've still got something similar to the default layout) you'll be able to set up where your disks are mounted.

---

### Post by geir2rs1 on 2005-11-04
This Is amasing!!!
First Reply after 1 (one minute) How is that!!!
Thanks for the link aysiu. It helped. I now have opera on my computer and it works!!

Ampersand: I will investigate your links.  They seemed to contain what I need. I will invwestigate more tomorrow ( I`m in Norway and it is close to bed time).

NO Firewall! I really thougth I needed one. All ports closed by default?? 
How do I open ports? how do I adminiter it? Applications that needs open ports?

Geir

---

### Post by geir2rs1 on 2005-11-04
Hi I`m back
Can`t find my way to bed because  I`m still playing whith Ubuntu. 
Another supid question.
How do I give Opera it right icon?  You all know how it looks like.. How do I get this on my desktop, Now it looks like a defau lUbuntu/Gnome icon. I awnt the "big" O. :smile: 

Thanks
Geir

---

### Post by mxyzptlk on 2005-11-04
all right here we go:

1. How do I install debian packages not listed within synaptic (Opera we browser)   I have allready downloaded a package. But then what...?

$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
$ sudo gedit /etc/apt/sources.list

find this section:

## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
 
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


replace with this:


## Uncomment the following two lines to fetch updated software from the network
deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy main restricted
 
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mx.archive.ubuntu.com/ubuntu](http://mx.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted

deb [http://splashy.alioth.debian.org/debian/](http://splashy.alioth.debian.org/debian/) unstable main

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) breezy java

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports main universe multiverse restricted

all you have to do is copy and paste from here (its my own list) change the <mx> for the mirror in your country example us (for USA)

after you replace you have to  do this:

sudo aptitude update

right after that you will see a small red light blinking in the upper corner of your desktop with an actualization message, just one click and a wizzard will appear just follow the instructions.

if you want to install more packages already downloaded go to system>administration>synaptics,     just checkbox (right click of your mouse) in the packages you want.  


2. I know I have a firewall and that it is activated (I persume. It is Linux). But. Where is it, and how do I change settings? Open/Close ports etc.?

according to the instructions upthere you will be able to install firestarter i also recommend you to read de pdf manual included, there are several options that matches your necesities.


3. I have an external multimedia device using NTFS, so i also have two MS partitions. One containg win2000 on NTFS, and on FAT32.
How do I Read from the NTFS partition and how do I read/write to the FAT32 one?


for your NFTS:

ASSUMING: /dev/hda1 is the NTFS partition
file to mout the partition /media/windows
users to this partitions belong to (gid=100)

we have two options

mount/unmount partitions read only MANUALLY 

sudo fdisk -l       to see your partitions

sudo mkdir /media/windows       create folder

mount partition

sudo mount /dev/hda1 /media/windows -t ntfs -o gid=100,umask=0007,fmask=0117,nls=utf8

(make sure its only one line hehe)

unmount partition

sudo umount /media/windows


the same but FAT (read/write)

mount partition

sudo mount /dev/hda1 /media/windows -t vfat -o gid=100,umask=0007,fmask=0117,utf8

unmount partition

sudo umount /media/windows


if you want to do this BOOTING (second option)

for the NFTS (read only)

sudo gedit /etc/fstab

then you have to add this line:

/dev/hda1 	/media/windows  ntfs 	auto,ro,exec,users,dmask=000,fmask=111,nls=utf8  0       0

(one line also) save it 


every time you boot your partition will be there

i also recommend to take a look to the virtual machine of VMware


For your multimedia device

what kind of device you have??

all i told you works

i have two discs in my box and a SATA disk with XP and i'm able to read the files open them and save in my ubuntu:smile: 


hope it helps

---

