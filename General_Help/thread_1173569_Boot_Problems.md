---
title: "Boot Problems"
date: 2009-05-29
forum: General Help
---

### Post by GatewayOpener on 2009-05-29
When I boot my laptop, it does the regular things, etc. Then after the Ubuntu loading screen ends, the screen flashes before freezing. What is wrong and what can I do about it?

---

### Post by quixote on 2009-05-30
The point where it freezes is when the X windowing system starts to load.  That provides your graphical desktop.  For that it has to control output to the screen, so when it's not working: no screen :-( .

You're going to need to boot from a liveCD or into recovery mode, and edit a file called xorg.conf.  (Located in /etc/X11/xorg.conf)  I'm not that good with editing xorg.conf, but those who are are going to need to know 1) which computer you have, and 2) --very important-- exactly which graphics card you have.

If you search for whatever your make of computer is, the graphics card, and xorg.conf, you may find someone who's already solved the problem and has an example of the edits you need to make.

---

### Post by pastalavista on 2009-05-30
Before you go editing xorg.conf, you should try booting in recovery mode and select the last option "Repair X" or... select "Root Terminal" and run ```
sudo dpkg-reconfigure xserver-xorg
``` and then exit and reboot.

---

### Post by GatewayOpener on 2009-05-30
I have a 2003-2004 Gateway 7405GX with an ATI Mobile Athlon 9600 64-bit graphics card and a half gig of ram. I mean, it is still a good laptop as when I first got ubuntu on it, it was just about as fast as my new '08 Gateway FX. I don't want to have to throw it out. If you guys can help, it would be greatly appreciated.

I am also putting Ubuntu alongside Vista on the FX since it has 2 built in hard drives so I can move files around.

---

### Post by quixote on 2009-05-31
Nice old ATI graphics cards generally need all kinds of special treatment. ;-)  I had an ATI Mobility Radeon 7500 in my old Sharp MP30 laptop, which is even more of an oddball than most ATI cards (from an ubuntu perspective).

If the dpkg-reconfigure xserver-xorg works for you (I've never tried that) that sounds like an easy solution.  

If not, what I did was search the Ubuntu forums for my exact model number and "xorg.conf", and when someone posted a sample xorg.conf, I'd try it until I found one that worked.  It's a lot of booting with liveCD, editing the xorg.conf on the hard drive, rebooting, and going curse-mutter-mutter when it didn't work, but eventually I found a configuration that functioned.  There are probably more elegant ways to do it, when you know what you're doing :D .

---

### Post by lavinog on 2009-05-31
Did you upgrade to jaunty?
Did you install the proprietary drivers?
if yes to either, your problem could be you are using a driver that is not meant for your video card.
ATI dropped propretary support for your card right before jaunty's release.

---

### Post by GatewayOpener on 2009-05-31
Well, I ended up just getting the disc I used from my friend and I reinstalled it. It's fine now, it had nothing on it anyway since it was a recent conversion.

---

### Post by lavinog on 2009-06-01
Did you do the wubi install again?

---

### Post by GatewayOpener on 2009-06-01
Yeh, I just re-ran the boot disk.

---

