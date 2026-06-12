---
title: "a few questions"
date: 2005-05-12
forum: Desktop Environments
---

### Post by proview on 2005-05-12
Well first of all i gotta say that ubuntu seems to beat all the linux distrubtions i have far seen

but there is a couple of things which still puzzle me
1) is it possible to install programs through ubuntu live because i know that dyneabolic for instance has an option which lets you install a nestfile on your hardrive and everytime you install a software it packs it into it
2)they say on the main website that there are over 1,000 programs in ubuntu but for some strange reason i have only seen less than a hundred on the livecd
why is that? and why there are no games?

---

### Post by dewey on 2005-05-12
Ubuntu is based off of debian, and uses dpkg as it's package management.  The hundreds of apps you read about, are contained on webservers, known as "Repositories".  It's incredibly simply, if you wanted, say, tuxkart, you would just type this in the command line.(Terminal)
```
apt-get install tuxkart
```
And it's installed, configured, and ready to go for you!  Also, some games are included on the default installation of ubuntu, like aislerot solitaire.  The rest, use apt-get or synaptic to obtain them.

---

### Post by calvinpriest on 2005-05-12
Proview,

Yes, you need to turn on your other repositories.  This can be done through the GUI Synaptic, but it's probably quicker just to do it as follows (and requires less typing for me :-):
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

After this is done, you can use Synaptic to install any of the 15,000 (?) or so packages in Ubuntu.  It's a nice GUI application, and it's in the menu under System->Administration->Synaptic Package Manager.

---

### Post by tom materene on 2005-05-12
This is truely what a good operating system for the masses should be.  The great thing about this Ubuntu or Kbuntu is the fact a new person can actually get things done with little or no Linux knowledge.  You can install just about anything imagined for linux and still have time to read and study command line.  Nothing is more important than command line !   I would say in my short time of using Linux that this one distro has done more to expand the numbers using it , than any other distro out there.  Just a very few little bugs that will be cleaned up soon and I will continue to do my pitch for Linux with Ubuntu at the very top.  Nuff said


Tom

---

### Post by Ali_Baba on 2005-05-13
I agree,im also a Linux newbie and Ubuntu has worked nicely. Apt-get and Synaptic packet manager are excellent programs. Its good that you dont have to be experienced to enjoy Linux. Ubuntu rocks :)

---

### Post by proview on 2005-05-13
First of all i would like to thank you for your responses 
and second
one of my questions still has not been answered
is it possible to install softwares in ubuntu live?
is there a way to create a sort of nestfile on the harddrive which every software or every configuration that i make will be saved there?

---

### Post by proview on 2005-05-13
anyones got an answer to my question?

---

### Post by tom materene on 2005-05-13
It is possible to access your windows partition and make a directory if you choose.  Your program mentioned is scripted to do that and does all the low level dirctory naming and making.  To do what you asked would require you to have a good understanding of Linux command line entries and also some programming skills.  If it is just a simple holding place for a file or program then you would use the following command line , note the different commands for NTFS or FAT32.

To make a windows media folder and mount it as /dev/hda1   and NTFS then the following three lines would be used,

sudo mkdir  /media/windows
sudo mount  /dev/hda1  /media/windows/ -t ntfs -0 unmask=0222
sudo unmount  /media/windows/

Everything in Linux is a file and must be mounted, after you get inside the partition then you can make a file and name it and put things into it.  In the end be sure to unmount as it says above.  These commands for the ntfs are a little confusing to me since it is used only allowing reading of all users.  The next example for FAT32 is for allowing reading and writing by all users.  I think maybe adding the v to ntfs would not work since the ntfs is a protected file system.
Anyway here is the code for the FAT32

sudo mkdir  /media/windows
sudo mount  /dev/hda1  /media/windows/ -t vfat -0 unmask=000
sudo unmount  /media/windows/

---

### Post by tom materene on 2005-05-13
I hit the submit button too soon.  :razz: 

I wanted to say that I wish I could try this out for you since I downloaded the Live CD to squash my curosity.  Unfortunately I don't have a windows system running on my Linux machine.  One thing I did want to point out is that the CDROM drive is usually locked down on a LIVE CD and you can't install anything from it.  If you are on line with the net then you could download things and install.  I don't know if any of this helps you or confuses you more.  There are limitations when using LIVE CD's for a reason of course.  They are like a new car brochure, just let's you look and see.   You always have the /ramdisk option to store things you work with on a live cd.


Hope it might clear up a few things

Tom

---

