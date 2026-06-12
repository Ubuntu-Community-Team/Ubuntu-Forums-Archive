---
title: "Big problem with Beryl"
date: 2007-02-07
forum: Desktop Environments
---

### Post by Mets on 2007-02-07
I recently tried to install Beryl on Ubuntu, and something went terribly wrong during setup.  I followed the official setup guide for 3D graphics found at [https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html).  I have an ATI card, so I used those instructions, and installed the fglrx driver as it says.  I then "followed the remaining instructions" on screen, and thought I had everything setup.  Then, I restarted, and it said that the Xserver had failed and that it wouldn't boot.  It just takes me to a black screen with a cursor.  It's not even a command line.  Does anybody know how to fix this?

---

### Post by raul_ on 2007-02-07
What version of Beryl did you install?

---

### Post by Mets on 2007-02-07
I didn't even get that far, I got stuck on the drivers for it.  I attempted to install xorg-driver-fglrx, which is step 1) for installing Beryl.

---

### Post by raul_ on 2007-02-07
Did you do the "sudo dpkg-reconfigure xserver-xorg" thing? Does GRUB load?

---

### Post by Mets on 2007-02-07
I did not do "sudo dpkg-reconfigure xserver-xorg," I simply restarted when the installation told me too.

GRUB does load, and a lot of Ubuntu seems to load, but when it tries to start Xserver I get a million warnings about how it isn't configured right and how it won't run, and then I get a black screen with a cursor that will do nothing.  Is there a way to restore my old config?  I know the install program made a backup before it rebooted, but I don't remember the name.  I didn't change it so I'm guessing it was the default.  Rescue mode might work I guess, I haven't tried.  I'm on my old windows installation right now (I know, I know, but it wasn't like I had a choice).  I can access my linux file system from here though, browse for things, and change any config files if I was directed as to what to do.

---

### Post by mcduck on 2007-02-08
> **raul_ said:**
> Did you do the "sudo dpkg-reconfigure xserver-xorg" thing? Does GRUB load?

Well, that's wrong way to do it anyway. With fglrx drivers xorg is configured with 'sudo aticonfig --initial'

Anyway, the problem is solved by booting to the single user mode (you can select it inb Grub menu) and running 'aticonfig --initial' (no sudo, you are root in singel user mode). Then 'reboot' will boot the machine and now you should be able to log in to Gnome :)

---

### Post by Mets on 2007-02-08
Well, I appreciate the try, but that didn't quite do it either.

> 
aticonfig --initial
Using fglrx
Nothing to do here, exiting

I also tried aticonfig --initial --input...blah for the singlehead configuration, and that didn't work.

When I reboot, I get "Xserver has failed to load because it is probably not configured properly.  Would you like to see server output?  Yes or No?

I click yes and I get the following
> Server Failure
Log file "/var/log/Xorg.O.log"
Using config file "/etc/X11/xorg.conf"
(EE) No Device Detected
Total Server Error


I have attached the two files, the log and the config file.  I had to gzip the log file because 20kb is "too big."  Any help relieving Mets' stress level would be greatly appreciated.

Is there anyway to just undo this whole thing and go with AIGLX instead?  I really don't know why I chose XGL, I honestly don't know the difference besides XGL is less open.  I just picked XGL because it came first on the beryl site.  All of my graphics were great before this :(

---

### Post by Mets on 2007-02-08
Nevermind I just restored my old xorg.conf and everything is working.  Back to normal again, and I'm back on Ubuntu.  I guess my system did not like the fglrx driver.  I'm going to give AIGLX a shot, like I should have from the beginning had I not rushed into this like the noobcake that I am :mad:  Thanks for your help guys.

---

### Post by adza on 2007-02-08
i have a similar problem... tried installing beryl (to no avail) then today when rebooting got the same x server error (i'm off the live cd right now though - never to boot into windows again!! hehe)... I reinstalled my old xorg.conf file by mv /etc/X11/xorg.conf.old /etc/X11/xorg.conf and it didn't fix the problem...  Server logs may shed some light for me...

I see the line 'dlopen: libglitz-gls.so.1: cannot open shared object file' ... this one has a one week 'veteran' of linux a little stumped... could someone please tell me how to fix this? would this be trying to load from xorg.conf or somewhere else?

 
***edit*** Problem fixed!! woo - hoo! i had modified the gdm.conf-custom file in my craziness to get everything going last night, removed the offending mod and back into ubuntu-ness :) Mets - hehe, i think i agree with you on the rushing into things... chalk up to experience me thinks.....

---

### Post by adza on 2007-02-08
Mets, in my travels i did find this [http://www.ubuntuforums.org/showthread.php?t=335034](http://www.ubuntuforums.org/showthread.php?t=335034) should help to ease the pain if you try again... myself, i found some other nice eye candy that will keep me happy for the time being...

---

