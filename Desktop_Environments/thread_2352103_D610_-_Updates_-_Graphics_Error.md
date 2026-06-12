---
title: "D610 - Updates - Graphics Error"
date: 2017-02-09
forum: Desktop Environments
---

### Post by wad2 on 2017-02-09
Hello,
  I have been happily working with my d610, 32bit, 14.02.  Excited to be on it doing all types of development for last 6 months.   Recently did some updates.  It worked fine for about 3 days and now complains about the need for me to configure my graphics driver.   After going through many iterations of drivers, I finally found the recommendation drivers for Ubuntu xenial xorg.  Supposedly this would show some HAL layer in the rc. I don't see anything.  

  So now I get an error in the x11.log, lightdm.log, and syslog,  Starts xserver, lightdm authenticates ok, then errors out on the greeter.  I get a dbus socket file not found.  I can't get to my desktop.

My linux image 4.4.0-62-generic.

Any help would be greatly appreciated.

Regards,
Wes

---

### Post by QIII on 2017-02-09
Hello!

Information would be of great value to those who would like to help you.  Unfortunately, the devination of information via internet is a skill that is beyond most mortals.

Could you tell us exactly what it was that you did to get/install this driver?  What instructions did you follow?  What are the exact errors you are seeing in your logs?  Can you C&P the appropriate parts of the logs here between code tags?

We can only help to the extent that we have information to do so.

Thanks!

---

### Post by wad2 on 2017-02-09
Hello,

Thanks!
On boot.  Error is "The system is running in low graphics mode. You will need to fix"     No display in low graphics mode either.

Computer is D610, 32 bit, Ubuntu Trusty Tahr 14.04.  Intel Graphics card.  Latest patches applied.

I tried different graphics packages to update my graphics driver.  Udev, fglrx, and last one was Xenial.  

sudo apt-get install --install-recommends linux-generic-lts-xenial xserver-xorg-core-lts-xenial xserver-xorg-lts-xenial xserver-xorg-video-all-lts-xenial xserver-xorg-input-all-lts-xenial libwayland-egl1-mesa-lts-xenial 

Went through and configured each one with.
dpkg-reconfigure -a *   ... 
dpkg --list| grep xenial   (shows all in ii status)

My current terminal is the only access. I am able to start the network services and connect to my wifi via command line to get updates.  

**xorg.0.log**:  
No errors except missing some fonts.

**syslog**
started org.freedeskto.Accounts
lightdm main process terminated with status 1
plymout-ready startup main process terminate  status 1
activating service name='org.freedesktop.systemd1

**Auth.log**
Pam adding faulty module; pam_kwallet.so
pam lightdm-greeter:session opened for user lighdm
Linked  /tmp/.X11-unix/X to /run/user/...display
lightdm; pam_unix(lightdm-greeter:session) closed for user lightdm

**Lightdm.log**
Authenticated
Failed to start lightdm-greeter.
******This is where I suspect the error and where x11 is started.**** 
Some configuration with my display.

dmesg.log, gpu-manager.log, boot.log and udev had nothing interesting there.

Regards,
Wesley

---

### Post by wad2 on 2017-02-13
Hello just wanted to update.  I am able to get to my desktop via unity and xorg.  However ligbtdm still throwing error and blank screen.  I also upvraded to 16.  That was a snap.

 The lightdm just blank page.  The point being the correct driver is there for unity but not lightDM.  
Revards, Wesley

---

### Post by wad2 on 2017-02-17
All is well.  I have my lightdm screen backup.  It ended up being a permissions problem.   I had been trying to lock everything down and I had changed permissions on a key file. :-/    At least I learned alot. :-)

---

