---
title: "Screen goes blank after login"
date: 2007-07-02
forum: Dell  Ubuntu Support
---

### Post by thegeez on 2007-07-02
I have a Dell Inspiron E1505 with factory installed Ubuntu 7.04.  I've had this system for about 10 days and I'm new to Linux.

I've been gradually making changes to get things more to my liking.  One of the things I tried was the special "desktop effects" which forced me to enable the restricted driver for the nvidia video card.  I decided I didn't like the special effects and thought the restricted driver was causing some text overlay problems on some web pages, so decided to back that out also.  From the restricted driver support module, I disabled the nvidia driver and was told the changes would take effect after rebooting.  I rebooted, logged in and the screen went blank.  Actually it goes black for about 10 seconds then changes to white.  At this point I am not able to do anything except hit the power off button.

Since everything seems normal until it recognizes me after I login, I suspect a configuration file got changed.

Can anyone help?  I'm at a loss.  I've tried logging in as root but that fails.  Thought maybe I could find the configuration file that was changed and change it back.

Would appreciate any info.

---

### Post by Rocket2DMn on 2007-07-02
In case you haven't yet, the typical command to reconfigure your video drivers (among others) is
```
sudo dpkg-reconfigure xserver-xorg
```You can access a terminal by hitting CTRL+ALT+F1.  Please read your way through this - don't rush it too much, you do need to answer the questions correctly or you will have more problems.  TAB moves you through options on screens with more than one choice, SPACEBAR can select (like when you have the choices for resolutions - select your monitor's max res and everything less than that).
If this fails, some people with this problem have noted that it just takes awhile for the screen to properly show up, and switching workspaces may help (CTRL+ALT+RIGHTARROW/LEFTARROW).
Good luck!

---

### Post by thegeez on 2007-07-03
Rocket, thanks for the response.

Before reading your response, I was able to start a xterm session from a session type select box at the bottom of the normal login screen (CTRL+ALT+F1 gets you a dell login screen).  Before trying to reconfigure the video drivers, I tried CTRL+ALT+RIGHTARROW/LEFTARROW to change workspaces, that did nothing, so then I created a backup of xorg.conf in my home directory.

:frown:AN ASIDE:  It appears that when enabling the nVidia restricted driver through Gnome's restricted driver module that no xorg.conf backup file is created, that's bad, bad, bad.  The only xorg.conf backup file in the /etc/X11 directory had a date that preceeded dell's shipment to me.:frown:

I carefully stepped through the "dpkg-reconfigure xserver-xorg" dialog and ended up with an xorg.conf that differed slightly from the one I copied to the my home directory.  Resolutions, refresh rate, etc. were all the same, the biggest difference was that the old file contained probably 10 lines in the beginning describing paths to fonts (as I remember).

Satisfied that I'd done as good as I could, I hit CTRL+ALT+BACKSPACE to reboot.  As you warned, I've ended up with a bigger mess than I started with.  Bottom line is that the X server fails to start because "It is likely that it is not set up correctly."  The tailend of the "Markers" in the X server output are (WW) warning, (EE) error, (NI) not implemented, (??) unknown.  I finally get to a screen that says "The X server is now disabled.  Restart GDM when it is configured correctly.  <OK>".  After selecting OK, I get a startup screen that prompts me with "dell login:".  I tried many different names and passwords to no avail.

My next step will be to try to get login information from dell and restore the previous xorg.conf.

---

### Post by Rocket2DMn on 2007-07-03
In order to restore the previous xorg conf, you can just get to the terminal and type
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
You can try F1 all the way to F7, you should have a terminal somewhere.  I am not familiar with nvidia drivers as I am cursed to use an ATI card, but they both have their problems, so I feel ya.

---

### Post by thegeez on 2007-07-03
Nothing I have tried, including F1 through F7, get me to a terminal session.  Right now the only way I can get out of the dell login screen is to power down.  So until someone can tell me what the dell login and password are, I'm dead in the water.  I've posted over on the Dell support forum, but no response yet.

---

