---
title: "X server video error"
date: 2007-07-31
forum: Dell  Ubuntu Support
---

### Post by demonwithin on 2007-07-31
ok, im posting this because its a Dell XPS 410, when i go to install after selecting to install at the FIRST screen, with the timer, it goes, and does the load bar, right before it finishes it tell me about a video X server error, i hit ok a few times, then giver me a black screen with _ blinking, i can type, but i have to eject the CD or hold the power button to get out of it.  My video card is nVidia 8600GTS, and im using a DVI, but i could go VGA if need be, but dont really want to, help?

---

### Post by Rocket2DMn on 2007-07-31
Have you tried reconfiguring Xorg?  You should select the nvidia driver if you can, and some people start with VESA driver.
You can get to a terminal by hitting CTRL+ALT+F2.  F1-F7 gives you different sessions, though F7 is typically your GUI screen.
```
sudo dpkg-reconfigure xserver-xorg
```
When you run this, please read, don't just ENTER your way through.  Select your video driver and when you get to the resolution page, select your monitor's max resolution and everything less.  Use TAB to move and SPACEBAR to select.
Once the reconfiguration is complete, run
```
/etc/init.d/gdm start
      or
startx
```

---

### Post by demonwithin on 2007-07-31
i think you mis understood, this is right after i put in the CD and select install from the first menu, before i ACTUALLY install

---

### Post by Rocket2DMn on 2007-07-31
My bad, I didn't read carefully enough - read AFTER INSTALL not INSTALL AFTER.
You can try plugging the monitor into the VGA port (just for the install), but if that doesn't work, you should try downloading and using the Alternate CD rather than the Live CD.  This will give you a text based install (doesn't require the Xserver), and if the problem pops up after you install, you will be able to troubleshoot it by getting the correct drivers, though you shouldn't need to right away.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and select the Alternate CD checkbox at the bottom
Don't forget to check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the alternate cd against the correct [hash]("https://help.ubuntu.com/community/UbuntuHashes"), if you need it, and burn the disc at a slow speed like 4x to prevent write errors.
Post back after you've tried these options and still have problems.

---

### Post by demonwithin on 2007-07-31
tried the VGA it didnt work, note though, i have no VGA, so it was VGA to DVI, but it was still analog

---

### Post by Rocket2DMn on 2007-08-01
You can't easily do VGA to DVI, you can do DVI to VGA with a simple adapter.  I think that's what you mean.  Try the alternate CD, some people just have problems with the Live CD, it's quite common.

---

### Post by michael37 on 2007-08-02
> **Rocket2DMn said:**
> Try the alternate CD, some people just have problems with the Live CD, it's quite common.

Agree, go for alternate CD to get the OS installed, and then troubleshoot the graphics drivers.

---

### Post by demonwithin on 2007-09-02
hey, sorry about not updating, i used Wubi to install it and used the alternative setup, it worked the first and second time, but today i tried it and got the X server error again, i updated my drivers and all when installing beryl, but i dont know what else to do now.  I set up FF the way i wanted and dont wanna lose it.  any help? i get the same error as before.  both windows and ubuntu drivers are up to date, i just dont know what to do

---

