---
title: "ATI Radeon 320M - No direct rendering - please help"
date: 2006-02-18
forum: Desktop Environments
---

### Post by gthing on 2006-02-18
I have tried everything I could find to get my HP ZE4430 laptop with a ATI Radeon 320M video card working with direct rendering.  All things I have tried so far have left me with "Direct Rendering: No".  My video and music is choppy, and I think this will fix it.

The instructions here: thttp://www.ubuntuforums.org/showthread.php?t=62517&highlight=320M
looked promising, but I couldn't get them to work because I am using the K7 kernel, and I think the drivers he pointed to only work on the i386 kernel.  

Also, there are 3 drivers, right? ATI, radeon, and fglrx?  I'm not even sure I have the radeon driver, how can I tell/get it?

The fglrx driver crashes x no matter what I seem to do with it.  

If anyone has gotten this card working, or knows how to get it working please let me know.  Some documentation says it won't work, yet many people around have reported getting it working.

---

### Post by art on 2006-02-18
I have a different card, so I couldn't tell, but check the /etc/X11/xorg.conf, under section Device what is listed as driver. Mine sais radeon. And I have direct rendering. So if yours sais ati, change it to radeon

---

### Post by gthing on 2006-02-19
I changed it to radeon but still dont have direct rendering.  Thats why Im wondering if the radeon driver is even installed.  Will it default to ati if it can't find the radeon driver?  I mean, is the fact that I have radeon set as my driver and that the GUI runs an indication that the radeon driver exists?

---

### Post by dcstar on 2006-02-19
[QUOTE=gthing]I changed it to radeon but still dont have direct rendering.  Thats why Im wondering if the radeon driver is even installed.  Will it default to ati if it can't find the radeon driver?  I mean, is the fact that I have radeon set as my driver and that the GUI runs an indication that the radeon driver exists?[/QUOTE]
lshw will tell you what hardware Ubuntu detects (in the display section).

That's a start to your task, the other is to look at your Xorg log files in /var/log for any messages saying what is going on.

---

### Post by gthing on 2006-02-20
Looking at that log file it seems that the radeon driver is loading - but I'm still showing directing rendering - no.  I just don't get it.  Why does ATI release drivers and not include support for one of HP and Compaq notebook's most common video cards?  Why do the 3rd party drivers not support it?  

Why can't I just force the radeon driver to do direct rendering?  Unless the 320M is vastly different than any similar mobility radeon it should jsut work.

---

### Post by Kray on 2006-02-20
I think that ati driver is the same as radeon driver. This is just opensource driver for ATI cards. And fglrx isn't going to work for 320M.

I have same gfx card in my Presario 2100 and IIRC I've got DRI enabled out-of-box in Breezy. Unfortenately my laptop is in repair ATM, but I've got a snapshot of my whole HDD. If ya interested I can post my xorg.conf. It is all I can do at the moment...

One note - u can got DRI enabled for 320M but ati/radeon driver is mostly for 2D part, so 3D performance will be not-so-good anyway. OTOH TuxRacer on Hoary (DRI off) was unplayable, playing on Breezy (DRI on) was ok.

---

### Post by gthing on 2006-02-20
Im getting pretty frustrated.  I would love to try whatever you're doing in your xorg.conf that has it working...

---

### Post by gthing on 2006-02-20
Just for giggles I booted up into the live CD that I got with Breezy.  Sho 'nuff, the direct rendering works by default - no problems.  I tested it with glxgears and everything. 

So what gives?  Does it work with a default install?  Did a kernel update kill it?  If so, how can I "roll back" the kernel?  

Or do you guys think it is something elsE?

---

### Post by gthing on 2006-02-20
Well I tried booting up with the originally installed kernel, and guess what- still no Direct Renering.

Someone must know why it works out of the box on the live cd, but not on the install CD.

---

### Post by Kray on 2006-02-21
Sorry, it appears that I don't have my old xorg.conf file (I have only my home directory backup) :(

Maybe boot into live cd and make copy of /etc/X11/xorg.conf. Then compare it with this from HDD installation.

---

### Post by art on 2006-02-21
Well I do have direct rendering on my old Mobility radeon 7000 IGP, I attach my xorg.conf. If you post yours it might help as well finding what you miss.

---

### Post by beanlover on 2006-04-10
I have very recently installed Ubuntu 5.10 on my laptop (for the first time).  I have an HP ze4610us.  It has the ATI Radeon 320M graphics adapter.

Here is what I did to get direct rendering enabled:

I downloaded the following two files from [http://dri.freedesktop.org/snapshots/]("http://dri.freedesktop.org/snapshots/"):

1)[http://dri.freedesktop.org/snapshots/common-20060403-linux.i386.tar.bz2]("http://dri.freedesktop.org/snapshots/common-20060403-linux.i386.tar.bz2")
2)[http://dri.freedesktop.org/snapshots/radeon-20060403-linux.i386.tar.bz2]("http://dri.freedesktop.org/snapshots/radeon-20060403-linux.i386.tar.bz2")

Next I extracted the contents of both files to my home directory.  I then created the folder "dri" in /usr/src folder (not sure if this in necessary or not...it's just what I did) and copied both extracted file contents into that directory.

Next I went in the "common-20060403-linux.i386" and entered:

```

sudo sh install.sh

```

Then I did the same thing in the "radeon-20060403-linux.i386".

That's it!  I couldn't believe how easy it was to do.  I rebooted and 3d was good to go.  I didn't have to directly edit my xorg.conf or anything funky like that.

I need to mention that I already installed gcc_3.4 and the kernel source headers for the Ubuntu kernel (the radeon install does some compiling so I'm sure these are required).

---

### Post by ]Nbx*cmD[ on 2006-12-01
I wrote this howto about it:

[http://ubuntuforums.org/showthread.php?t=310018&highlight=ati+320m](http://ubuntuforums.org/showthread.php?t=310018&highlight=ati+320m)

---

