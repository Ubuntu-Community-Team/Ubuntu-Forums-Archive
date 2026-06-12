---
title: "KDE Desktop Now Fails"
date: 2007-05-23
forum: Desktop Environments
---

### Post by gspaulding on 2007-05-23
I installed Ubuntu 7.04 generic i386 and everything ran well.  Wanted to try kde, so I did the aptitude install kubuntu-desktop and configured it.  For a week or so I have been using kde mostly, but could still log into a gdm session when desired, and had kde as the default.

Today, upon booting, I get the Kubuntu logo, the bar fills, then I get a ubuntu 7.04 ubuntu tty1 prompt.  Then a message window opens:  Failed to start the X server.  It is likely that it is not setup correctly.  Would you like to view the x server output to diagnose the problem?

Choosing <ok> shows these errors:
(EE) open /dev/fb0: no such files or directory
(EE) no devices detected
Fatal Server Error No Screens found

Then I get the $ prompt.  Upon ctrl-alt-del, I see a message during shutdown saying var/run/kdm.pid not found.

My main concern is just getting back to a desktop, either gdm or kde.  Thank you for any suggestions.

---

### Post by Kobalt on 2007-05-23
The X server usually doesn't crash this way without touching it : did you try to install such things as graphic card drivers, Beryl/Compiz, ... ?

---

### Post by gspaulding on 2007-05-23
No installs, but did look at increasing my graphics card resolution.  When I changed it to higher resolution I could only get 43Hz refresh, so I changed it back to 1024X768 75Hz, which is what it was when I started.  My card is an ATI X1600 pro.

Could I try uninstalling the kubuntu desktop?  What is the code?

---

### Post by Kobalt on 2007-05-24
How did you change your resolution ? Did you manually edit the xorg.conf ? 
You should reconfigure xserver in my opinion (you don't need to reinstall the whole kubuntu desktop). At boot press Ctrl+Alt+F1 to access a command line, log in, and enter : ```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions, leave the default choice if you don't know. After this reboot your computer, and hopefully you should get a graphical interface back.

---

### Post by g8m on 2007-05-24
If you login in tty and type "startx" you probably would get to see where you made a mistake in /etc/X11/xorg.conf.

---

### Post by gspaulding on 2007-05-24
Thanks for the suggestions.  I will try them and post back the results.

I never touched the xorg.conf file or any other configuration files.  I simply went to the utilities that pertain to the display properties and choose a higher resolution.  It would only work at a low refresh rate, so I changed it back to the resolution I had been using.  I continued working in the session with no problems and shutdown.  Next restart, no gui.  I have had some shutdown problems when in a kde session, but the gdm sessions always shut down nicely.  I appreciate the helpful members of this community.

---

### Post by gspaulding on 2007-05-24
Whoo-hoo,

Back in business.  I ran the dpkg-reconfigure, answered a lot of questions I had no idea how to answer, and wound up back at the $prompt.  So I tried 'startx' and booted into my gnome desktop.  I restarted and choose gnome as my default desktop and all is well.  I think I'll stick with gnome for now, since I've lost confidence with kde (even though I kind of like it better.)  My video card is now listed as 'generic' but it is an Ati X160.  The resolution & refresh are fine, so I won't worry about that.

Thanks for your help.

---

