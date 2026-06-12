---
title: "HELP!!! Login SCreen Doesn't  Appear (noob with big problem)"
date: 2008-08-10
forum: Desktop Environments
---

### Post by cooltuyul on 2008-08-10
My Ubuntu 8.04 amd64 during startup doesn't display the login screen. at first the startup looks good with the orange loading bar, howver when it is all the way and instead of the normal login screen, a black screen appers! it says loading please wait at the top and a terminal like entry asking for name and password.

HELP!!!

---

### Post by tuxxy on 2008-08-10
Did you recently edit any of your video settings?

ONce at the prompt log in with your user/pass and try running this command

```
startx
```

This should boot you back into GNOME however if it fails you could try and reconfigure the xorg 

```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by cooltuyul on 2008-08-10
i didnt change anything at least that i am aware of. any ways i tried the first code thank you it worked. however when i was going to turn the computer off, there was no option to shut down or restart! WHATS GOIN ON? also will i keep on typing:```
startx
``` every time i start up my computer?

---

### Post by tuxxy on 2008-08-11
You could try rebooting from the terminal by entering

```
sudo shutdown -h now
```

NOw see if it boots into GNOME, I also had an issue with the lgout menu going missing when I disabled power management in sessions.

---

### Post by Hunter M. on 2008-08-11
startx command, then it should boot into your default login manager, otherwise go back into a terminal and execute it manually
then do reconfigure on xserver

---

### Post by cooltuyul on 2008-08-11
> **Hunter M. said:**
> startx command, then it should boot into your default login manager, otherwise go back into a terminal and execute it manually
then do reconfigure on xserver whats xserver?

---

### Post by Hunter M. on 2008-08-11
xserver= displaymanager

---

### Post by zuner2012 on 2008-08-11
I can't tell you how many times this has happened to me. dang it sucks, I know. try unplugging all peripherals except for the power cord, monitor cable, keyboard, and mouse. Be sure to unplug audio and usb drives. If this doesn't work. When ubuntu loads correctly the orange passes back and forth a couple times, then starts filling up the bar. If after about 5 passes, it doesn't start, either ctrl alt delete, and reboot, or hold down the power button, and restart. Tell me if it works, it's worked for me before (might take many restarts though)

---

### Post by cooltuyul on 2008-08-11
can i use ```
 sudo dpkg-reconfigure xserver-xorg
``` in the terminal although ```
startx
``` works because its annoying to have to keep on typing it every time i start up.
:confused:

---

### Post by Java Geek on 2008-08-11
what do you have *'ed when you type sudo tasksel? Just so you know, don't change anything...

---

### Post by oVIXx on 2008-08-12
Check your inittab, in Slackware for example, you always start in Linux or what you might see as the command line, until you change the run level from 3 to 5. Init level 5 boots to a GUI login and log off options. Not sure how Ubuntu has the init levels set up but it should still be id:5:initdefault

---

### Post by woaibbhemm on 2008-08-12
hello~
      nice    to   meet  you .thank you   for   your  sharing    and  welcome   to  our   website ~










Welcome to usfine for [buy lotro gold](http://www.usfine.com/Lord-of-the-Rings-Online-US-c-93.html)Age Of Conan gold[/url] and 
[buy runescape gold](http://www.usfine.com/runescape-c-68.html)sevise.

---

