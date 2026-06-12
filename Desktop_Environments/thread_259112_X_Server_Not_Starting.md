---
title: "X Server Not Starting"
date: 2006-09-16
forum: Desktop Environments
---

### Post by Dana on 2006-09-16
I did not get caught in the big update snafu but Friday of this week I booted Ubuntu Dapper and X Server did not start and so far I have not been able to fix it. The only thing I did on my system was on Wednesday, the 13th, I used Synaptic to install libdiscover2 2.0.7-2.1ubuntu1. Don't know if this might be responsible for my woes. I was struggling to get my Memorex USB U3 memory stick to be consistently recognized. It is only picked up by the system in 1 out of 50 insertions or so. 

When I boot Dapper I see, "Failed to start the X Server. Likely it is not set up correctly. Would you like to view the x server output? But at that point I cannot exercise that option.

startx produces, 

creating new authority file /home/dbh/.serverauth.4814

xinit: Connection refused errno 111:unable to connect to x server.

xinit:no such process errno 3, server error.

Here is what I have tried so far to get X Server running again:

1 restored the xorg.conf_backup 
  no change

2 sudo dpkg-reconfigure xserver-xorg
  no change, error message: /usr/sbin/dpkg-reconfigure: xserver is broken or not fully installed

3 sudo apt-get update
  sudo apt-get upgrade
  sudo apt-get reboot
  no change

That is all I know to try. I did try to apt-get the libdiscover1-date package but apparently I don't have the name right because apt-get could not find it.

Any suggestions greatly appreciated. I'm stuck and this is the first serious problem I've had with Dapper.

Dana

---

### Post by Dana on 2006-09-17
Tonight did:

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10.4

xserver still does not start.

---

### Post by Shazaam on 2006-09-17
Try this...

sudo dpkg-reconfigure -phigh xserver-xorg


Loads a default xorg.conf
I have been using that when my nvidia experiments go bad :)

---

### Post by karamba_kid on 2006-09-17
You don't happen to be running the latest 686 flavor kernel with the latest nvidia-glx drivers, because if that's the case I couldn't get X server to start with that setup either.  This however may not be relevant because I think your startx error is different than the one I was getting with the 686 kernel.

---

### Post by Dana on 2006-09-17
Wish it were so but just running the vanilla 386 kernel and my ThinkPad uses ATI Rage Mobility.

Sitting here trying to figure out what do do next.

Dana

---

### Post by Dana on 2006-09-17
> **Shazaam said:**
> Try this...

sudo dpkg-reconfigure -phigh xserver-xorg


Loads a default xorg.conf
I have been using that when my nvidia experiments go bad :)

This returns something on the order of xserver.org not installed.

aptitude show xserver-xorg-core | grep Version
returns 1:1.0.2-0ubuntu10.4

So I don't know what is going on. dpkg-reconfigure still says xserver-org is broken or not fully installed... this after using apt-get to install 1.0.2-0ubuntu10.4.

After three nights of working on this I have gotten exactly nowhere.

Dana

---

### Post by Dana on 2006-09-28
Still have not regained a functional xserver.

How I remove x completely?

And then how do I apt-get a complete new installation of x?

---

### Post by amohanty on 2006-09-28
try:
**sudo apt-get remove xserver-xorg**
and then
**sudo apt-get install xserver-xorg**

Now the former may prompt you about removing ubuntu-desktop pkg too, just say  yes. ubuntu-desktop is only a dependency package ie it makes sure that certain set of packages are installed. You can install it again later.

HTH
AM

---

