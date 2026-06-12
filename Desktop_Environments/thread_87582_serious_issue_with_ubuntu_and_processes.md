---
title: "serious issue with ubuntu and processes"
date: 2005-11-08
forum: Desktop Environments
---

### Post by dpw2atox on 2005-11-08
i dont know why this happens but it randomly occurs with ubuntu. When i launch some apps such as wine or cedega, they go to an uninterruptible process and cant be killed. The only fix is to reboot. Now after i reboot the  pc they run fine for a little while and then they just stop working again.

here is the process output from the system monitor

wine      uninterruptible      1.2 MiB      0    /home/dave/.cedega/.winex_ver/winex-5.0/wine --setValue -force

Also the add applications gives me an error when i try and go from add applications to advanced mode. 

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.

However if I open a terminal and  launch synaptic manually then it  opens up.


This occured with ubuntu 5.10 32bit and 64bit withthe regular  kernel and the 686 smp kernel as well. This is also occuring with the dapper development release.


I have an Athlon 64 x2 3800+ (dual 2Ghz cpus), 1GB ddr400, A8N-SLI deluxe, 6600GT pci-e videocard, 74GB raptor HD, 300GB maxtor sata hd, sata dvdburner, ide-dvd drive.

my uname -a is
Linux colony 2.6.12-9-amd64-k8-smp #1 SMP Mon Oct 10 13:18:18 BST 2005 x86_64 GNU/Linux

im using the nvidia drivers in the repository, 76.67


Anyone know why this happens or have any solution? This started to occur during the 5.10 development process and has been an issue ever since. I didnt have this problem with 5.04 or with fedora core 4.

---

### Post by tspec on 2005-11-08
I'm actually getting the same error at the moment though I'm really running much, it's almost still a fresh install of ubuntu. Rebooting the computer doesn't help, it also locks me out of apt-get as well so I'm guessing aptitiude is the problem though I'm not actively running it.... I assume theres an easy way to view and kill processes running?

---

### Post by NewWithoutClue on 2005-11-08
The command line program "ps" will list the processes, ("ps -A"  to show all ). 
When your root you can use the "killall processname" to kill an application.

I don't know how to help you with your synaptic problems, sorry.

Regards,
Paul.

---

### Post by pjbgravely on 2005-11-08
try

$ps aux|less

find the PID of the program and use

$sudo kill -9 PID#

---

### Post by ceclsj on 2005-11-30
i was having the same problem...i did:

(in terminal)
sudo apt-get update

(this said that i needed to run - )
sudo dpkg --configure -a

so i did

then i again ran -
sudo apt-get update

apparently an install update got interrupted, and restarting it didn't help.  this fixed my problem

---

