---
title: "Netzero.deb"
date: 2006-03-17
forum: Desktop Environments
---

### Post by kemah201 on 2006-03-17
Hello:

I am trying to install a Lindows/Linspire version of NetZero dialup internet access on my ubuntu box. I have run *dpkg -i netzero.deb* and the archive was extracted to /opt/nzclient. A shortcut is supposed to be created on the Desktop but it has not appeared. The program may not be compatible with Ubuntu but would someone please look at the contents of the /opt/nzclient folder and advise me if there is something else I need to do?

opt/nzclient:

-rwxr-xr-x  1 root root    281 2003-11-14 19:13 accel.mkr
drwxr-xr-x  2 root root   4096 2006-03-17 09:43 cache
-rwxr-xr-x  1 root root 234073 2003-11-12 16:00 cache.obj
drwxr-xr-x  2 root root   4096 2006-03-17 09:43 dat
-rwxr-xr-x  1 root root     56 2003-11-04 14:05 dialerr.sh
-rwxr-xr-x  1 root root   6151 2003-09-26 23:51 dialjar.jar
-rwxr-xr-x  1 root root    468 2003-09-26 23:51 emltmplt.dat
drwxr-xr-x  2 root root   4096 2006-03-17 09:43 help
drwxr-xr-x  6 root root   4096 2006-03-17 09:43 images
drwxr-xr-x  2 root root   4096 2006-03-17 09:43 lib
-rwxr-xr-x  1 root root      9 2003-11-11 10:57 mdminit
-rwxr-xr-x  1 root root     70 2003-11-20 23:09 NetZero.ini
-rwxr-xr-x  1 root root      1 2003-11-12 16:00 NetZeroIni.ctl
-rwxr-xr-x  1 root root  35584 2004-02-24 13:42 nzppp
-rwxr-xr-x  1 root root 219171 2003-09-26 23:51 phn.dat
drwxr-xr-x  2 root root   4096 2006-03-17 09:43 pool
-rwxr-xr-x  1 root root    255 2003-11-14 20:17 runclient.sh
-rwxr-xr-x  1 root root  74283 2003-11-12 16:00 shellui.obj
-rwxr-xr-x  1 root root   7085 2003-11-12 13:47 zcastsu.zip

Thanks.

---

### Post by kemah201 on 2006-03-17
Does anyone know of a dialup ISP that has a Ubuntu compatible software?

---

### Post by taurus on 2006-03-17
I guess you can run either "dialerr.sh" or "dialjar.jar" if you want to use it!!!

---

### Post by djheadley on 2006-03-17
Do you have Java installed?  When you do, you will run the runclient.sh script.  Good Luck.
BTW, I'm running netzero.

---

### Post by kemah201 on 2006-03-20
OK, I downloaded the java runtime environment from Sun. But I'm not sure if I just downloaded the plug-in for Firefox or Java for the OS. I am still not able to run runclient.sh. What do I need to download to get NetZero to work? Please advise.

Thanks.

---

### Post by kemah201 on 2006-03-20
OK, I am able to run runclient.sh now but all I get is a message, "DM set to off." Please help!

Thanks.

---

### Post by djheadley on 2006-03-20
Unless I have just re-booted the computer (dual boot with Windows), I have to run Netzero 2 times to get it to work, I don't know why.

---

### Post by kemah201 on 2006-03-20
I still can't get past the "DM set to off" error message. Also, how do I configure the modem. I have a modem installed that device manager finds but under Modem Connection under Network Settings, it says "The interface ppp0 is not configured." I try to configure it but the "OK" button is always grayed out when I click "Enable Connection." It also won't autodetect the modem. Please help!

---

### Post by djheadley on 2006-03-20
I'm using an external modem and found out it was ttyS3 and to make sure I didn't mess anything up, I copied the runclient.sh to nz.sh.

Here's what I did:

Choose "system" then "Administration" then "Networking" (enter password).  You will see a modem listed and it will say not configured.  Click on "Properties" then "Modem" then "Autodetect" to find out what your modem is (mine is ttyS3).

sudo gedit /opt/nzclient/runclient.sh
     (asks for your password)
Add folowing line:
ln -s /dev/ttyS3 /dev/modem     (if ttyS3 is your modem)
after the line:
#!/bin/sh
then save the file as nz.sh

installing Netzero.deb should have put an entry on your Applications menu, it might be under "Internet".  If not, you'll have to create it.

To edit the Applications menu, choose "Applications" then "System Tools" then "Applications Menu Editor". Find where the entry for Netzero is in the left column (if it isn't there then double click on "Internet" in the left column and look in the right column).   If it is there then Double Click on it and enter:
sudo bash /opt/nzclient/nz.sh in the "Command" area. Save it.  I don't think it's necessary to reboot but I did because I had to go into Windows for some reason before I tried to get online again.  Sometimes I have to run the sh file 2 times but it works.  Let me know how you come out.

---

### Post by kemah201 on 2006-03-20
I will have to try it on my desktop at home because I can't even autodetect my modem on my laptop here at work.

---

### Post by djheadley on 2006-03-22
Did you get it to work?

---

