---
title: "help with a reinstall"
date: 2008-12-19
forum: Desktop Environments
---

### Post by shogunmidas on 2008-12-19
is there anyway i can reinstall and keep my files that i have on my hard drive?

also, how do i put the ubuntu install on a separate partition?

---

### Post by taurus on 2008-12-19
Do you have a separate /home directory?

---

### Post by shogunmidas on 2008-12-19
im not sure exactly what you are asking... everything is on one partition, home/username/documents/porn/porn/porn. 

i have downloaded and added a bunch of things recently that i dont want to get deleted if i do a reinstall though, but because of the recent **** up the only way i can get ubuntu to run on my laptop is by the live user off of the dvd. so i cant very well just burn my new files off...

what do i do?

---

### Post by shogunmidas on 2008-12-19
is there any way i can move the files to a place where ubuntu wont overwrite it?

---

### Post by taurus on 2008-12-19
Do you have an empty partition on your harddrive where you can store your files?  Do you have access to a USB drive?

Open a terminal and post the output of this command from the LiveCD.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter L, not number one.

---

### Post by shogunmidas on 2008-12-20
i have already went through with the reinstall, but i did use my usb jumpdrives and got my files off.

a question though, when i did the install i used the guided install usea entire disk. someone on here was mentioning that i should put the ubuntu install on one partition and just have my data on the rest. how big should i make the ubuntu partition? and how do i let the ubuntu install know where to put the actual os, and where to save my data?

---

### Post by taurus on 2008-12-20
It depends on how large your harddrive is.  People recommend you have three partitions:  one for root filesystem (aka /), one for /home where all your personal files would go (easy if you plan to reinstall or upgrade later), and a smaller one for swap.  

You can use gparted from the LiveCD to do that.  Then when you get to the partition screen, just use the Manual option and tell the installer to mount whichever partition that you have to / and the other one to /home.  You don't have to worry about swap since the installer should know what to do with that.

And if you plan to reinstall later, you would mount the same partition to / and format it.  Mount the other one to /home BUT do not format it or all your files will be wiped out.

---

### Post by shogunmidas on 2008-12-20
> **taurus said:**
> It depends on how large your harddrive is.  People recommend you have three partitions:  one for root filesystem (aka /), one for /home where all your personal files would go (easy if you plan to reinstall or upgrade later), and a smaller one for swap.  

You can use gparted from the LiveCD to do that.  Then when you get to the partition screen, just use the Manual option and tell the installer to mount whichever partition that you have to / and the other one to /home.  You don't have to worry about swap since the installer should know what to do with that.

And if you plan to reinstall later, you would mount the same partition to / and format it.  Mount the other one to /home BUT do not format it or all your files will be wiped out.

so the os would go on / ,how large does it need to be? im using ubuntu on a 200gb laptop, so the smaller the partition the better. what im not sure about though, how to i tell the manual partition where to put / and where to put /home?

---

