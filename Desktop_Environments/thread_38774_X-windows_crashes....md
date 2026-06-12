---
title: "X-windows crashes..."
date: 2005-06-02
forum: Desktop Environments
---

### Post by bigbill52a on 2005-06-02
Xwindows crashes taking the screen, keyboard and mouse.  Luckily, you can still exit Linux by pressing the off/on switch on the computer.  The computer shuts down.  Pressing ctrl-alt-backspace or any other keys are ineffective.  The screen consists of squares in various shades of grey.  Some of the squares blink.  This happens mostly with kde, but sometimes with the other windows managers.  It has happened with or without fglrx installed.


SEE MY LAST RESPONSE....

---

### Post by dataw0lf on 2005-06-02
Could you give us any relevant portions of your X logs ? (ala /var/log/Xorg.0.log)
Can you switch to a VT ( ala Ctrl-Alt-F(1-7) ) ?

Does it happen on any particular applications?  Are you able to reproduce the error?

---

### Post by bigbill52a on 2005-06-02
The keyboard also goes completely dead...so I can only press the on/off switch on the computer to halt ubuntu.  After about 15 - 20 seconds, the computer shuts off.  It does not even switch to text mode, while it is shutting down.  I had the same problem whether or not fglrx was installed.  Xwindows failed 3 or 4 times last night and I just gave up on Ubuntu, until I learn how to correct this problem.  I did notice that I had the problem more often in KDE...My logs are gone since I got pissed and nuked the drive...lol

---

### Post by Joeb on 2005-06-03
It would help to know what video driver you have installed, when asking for help on an X problem.  If you installed the commercial nvidia driver, did you happen to turn on transparancy?  Evidently, it's not very stable and causes lots of problems with the current version of X.

Tell us what video card you have and what driver you told Ubuntu to use and we can help.  It would be good to post the relavent section of the logs that dataw0lf suggested, too.

Joeb

---

### Post by bigbill52a on 2005-06-04
ati driver for k7 kernel.  I had the same problem with or without installing the ATI driver.  In other words it crashed before I installed the driver and after I installed the driver.  I could not use kde for fear of imminent crash and when it started affecting all the windows managers, i gave up and nuked ubuntu...

---

### Post by Joeb on 2005-06-04
I don't have an ATI card, so I'm won't be able to help troubleshoot that, but there are a lot of users who do, maybe one will chime in.  I noticed, though, that you said it locked up with the K7 kernel.  How did it perform with the stock kernel?  I've had minor problems with the other kernels that don't seem to exist with the stock one.  In addition, on my computer, I didn't notice any real performance difference between the stock and K7 kernels.

It definately sounds like an X-windows problem with the driver and/or kernel.  If you have already removed Ubuntu, you might try booting from the Live CD and see if the problem manifests itself there.  It uses the stock kernel.

Joeb

---

### Post by simianMiscreant on 2005-06-04
See my topic for more on this...should be just a few below this one.

---

### Post by simianMiscreant on 2005-06-06
My fix is here:
[http://ubuntuforums.org/showthread.php?p=201964](http://ubuntuforums.org/showthread.php?p=201964)

---

### Post by bigbill52a on 2005-06-07
After suffering several days with just Windows Xp installed, in a fit of anguish, I reinstalled Ubuntu, but I avoided any KDE files or programs.   The desktop seems stable.  I am beginning to believe that my X-Windows crashes are KDE related since they occurred while I was either using KDE or a KDE program in gnome or xfce. or had just recently used such a program.  I will run several days like this and report any failures, if any, with NO KDE.  My sources.list contains the complete list from from the unofficial guide and is basically the same, as when I had installed Ubuntu the last time.

amd-64 3000 with 1 gig 3200 ram
ati 9600 chipset
msi k8t neo
with k7 kernal and fglrx installed using suggestions from
[http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10)

---

### Post by bigbill52a on 2005-06-07
Apparently, it is Konqueror that is causing my xserver to crash.  I removed it along with the supporting files
Removing kde-core ...
Removing kdeaddons ...
Removing kubuntu-desktop ...
Removing kdebase ...
Removing konq-plugins ...
Removing konqueror ...
Patience, a Kde game, works fine in Gnome.  If I find any kde programs that cause this crash..I will report them here.  Otherwise, Gnome is stable and working fine.

---

