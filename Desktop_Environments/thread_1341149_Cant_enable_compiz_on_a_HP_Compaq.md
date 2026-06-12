---
title: "Cant enable compiz on a HP Compaq"
date: 2009-11-29
forum: Desktop Environments
---

### Post by Masquerade on 2009-11-29
Hi everyone,

I just installed Ubuntu Karmic on a HP Compaq.
(it looks like this: i have a labtop (hp compac) and a lg screen attached to it)
However, i can not enable compiz desktop effects there. I already checked the "Hardware Drivers" section in the main menu.
**See below for more detailed information**
Here is the output of compiz --replace
```
compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (2304x1024) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 


```

and the content of xorg.0.log is linked [here]("http://paste.ubuntu.com/331212/").

Thanks a lot in advance,
benny

---

### Post by mikeac72 on 2009-11-29
Install your latest graphic drivers, if you didn't already do that.

Install Ubuntu Tweak.
[http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)
Use compiz fusion from Ubuntu Tweak.

---

### Post by Masquerade on 2009-11-29
thanks  a lot for the fast reply. ubuntu tweak seems to have installed compiz, but there is still the same problem when executing ubuntu-tweak.

---

### Post by andrea000 on 2009-11-29
Have you installed ccsm?You can also run compiz in
the terminal.
applications->accessories->terminal
> compiz

There is also compiz check it may also show some
problems that is stopping compiz from working.

---

### Post by Masquerade on 2009-11-29
thanks a lot for the tip.
compiz check told that the screen resolution is too high to enable compiz. this is because i had two monitors attached. 
is it possible to run compiz on a dual-monitor-view, and if, how?

greetings,
benny

---

### Post by andrea000 on 2009-11-29
I do not know but there shouldn't be anything stopping
compiz from running on a dual monitor maybe some one else
who knows more about compiz could help on this.Also what
graphic card do you have if you don't know go to there
website and look for it in there help section?

---

### Post by Masquerade on 2009-11-30
this is said to be reason because compiz-check says:
> Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) y

 Your resolution is 2304x1024 but the maximum 3D texture size that your
 graphics card is capable of is 2048x2048. Thus Compiz will not be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again). 


for the graphics card: lspci says
```
[...]
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
[...]
```

when changing the second (attached) screens resolution from 1280x1024 to 1024x768 the behaviour changes:
compiz-check says that compiz should be able to run, however compiz --replace makes the video output freeze. (though the computer still seems to react to keys pressed, for example the I/O key.)

---

### Post by Masquerade on 2009-11-30
i created an extra thread for this issue [here]("http://ubuntuforums.org/showthread.php?p=8413760#post8413760")

---

