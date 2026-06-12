---
title: "Built in WIFI &amp; Ubuntu"
date: 2008-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Tex786 on 2008-05-06
Does anyone know that if the WIFI that is built into a dell inspiron laptop will work with ubuntu without having to search for drivers?

I know dell and ubuntu are good together but i am unsure about this.

thanks

---

### Post by agim on 2008-05-06
What is the wireless card on the computer?

---

### Post by samuelshi on 2008-05-07
I used Dell Latitude D630, and the type of the wireless card is Broadcom BCM4310.
I installed Ubuntu 804, and after I installed the ndiswrapper package , the wireless card works fine:)

---

### Post by undfined on 2008-05-07
What model computer and wireless card?

I have a Dell Inspiron 5150 with a broadcom driver I needed to google search for.  I was running Ubuntu 7.10 and had to tweak ndiswrapper to get it working properly.  I had an issue where I had to manually turn it on after booting up, but it worked fine.

I now have a Inspiron 1420n with Ubuntu 8.04 (hardy) and wireless works out of the box.  It takes some time after hibernation but a clean boot works as expected.

Good luck.

---

### Post by notwen on 2008-05-07
Dell's generally come w/ either a Intel or Broadcom based wireless chipsets.  Intel is very well supported, while Broadcom is kinda iffy.  The Intel chipsets should have restricted drivers, some can even use generic drivers.  With Broadcom you will more than likely need to use ndiswrapper in order to get it working using windows drivers.  

My Inspiron 1420n has the Intel 3945 wireless and worked out of the box.  Please provide us w/ more details in order to find out if your Dell's wireless will work or need some work in order to surf wirelessly.  (ie. Model and/or wireless chipset)  =]

---

### Post by virtual_zero on 2008-05-07
I have an Inspiron with Broadcom wireless and can confirm that the wireless works with 8.04

I've used ndiswrapper... also note that the order that the ssb and ndiswrapper modules are loaded had to be reversed.

The following worked for me and is copied from another forum post somewhere...

1) Create a file /etc/init.d/ndiswrapper

2) Paste in it this text:

#! /bin/sh

rmmod b44
rmmod b43
rmmod b43legacy
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe b44

############# end file ############

3) Set file access permissions:

sudo chmod 755 /etc/init.d/ndiswrapper

4) Check if permissions are ok. Type:

ls -l /etc/init.d/ndiswrapper

-rwxr-xr-x 1 root root 4388 2008-02-03 14:57 /etc/init.d/ndiswrapper

4) Create a symbolic link call S99ndiswrapper in the folder /etc/rc2.d, from /etc/init.d/ndiswrapper:

sudo ln -s /etc/init.d/ndiswrapper /etc/rc2.d/S99ndiswrapper

5) Reboot

---

### Post by caro on 2008-05-07
Inspiron e1505n here with Intel 3945 and works out of the box.

---

### Post by aikiwolfie on 2008-05-11
WiFi works fine out of the box on the M1330n.

---

