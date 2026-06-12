---
title: "Monitor turns off after 10 minutes using xscreensaver"
date: 2007-10-29
forum: Desktop Environments
---

### Post by louvros10 on 2007-10-29
Sorry to start a new thread, but I 've lost in the forum threads about that matter and I can't figure out what to do...:(:(:(
I 'm using xscreensaver and I have installed Compiz Fusion. Gnome-screensaver isn't working after I installed Compiz Fusion. Xscreensaver is working and the power settings from the advanced tab of xscreensaver menu is unchecked.
The problem I have is that after 10 minutes idle my monitor turns off. I can't watch a movie without moving the mouse every 10 minutes. It's pretty annoying!!!
Please help me...!!!
Thanks in advance!!!

---

### Post by perlluver on 2007-10-29
Did you check the system settings to?  Every time I reboot my box, it sets my power savings to default.

---

### Post by louvros10 on 2007-10-30
Yes I 've checked the power saving settings and I 've switched the monitor never to turn off. But it keeps turning off after 10 minutes.
I 've tried to open the xscreensaver file with gedit but it gives me encoding error!!
Please help me...:???::???::???:

---

### Post by bingoUV on 2007-10-30
If you do the following, the monitor should never turn off by itself : 
```

xset -dpms

```

Do this in your X startup script. If you want it to turn off after half an hour of inactivity, you can do this (1800 is the number of seconds)
```

xset dpms 1800

```

---

### Post by Jose Catre-Vandis on 2007-11-01
> **bingoUV said:**
> If you do the following, the monitor should never turn off by itself : 
```

xset -dpms

```

Do this in your X startup script. If you want it to turn off after half an hour of inactivity, you can do this (1800 is the number of seconds)
```

xset dpms 1800

```

Do you mean in /etx/X11/xorg.conf or another file?

---

### Post by XPinG on 2007-11-02
no he means to type the command in a shell or you may do it from  Alt+F2
I have the same problem but with a little differance, I'm using gnome-screensaver (I even tried with xscreensaver) and the settings are frozen I can't change the time out of my screen saver
EX: if I put 2 min in gnome-screensaver after 2 min it gos to the one I chosed, but in the 10th min my screen goes blank (that was the screensaver I had before my dist-upgrade to 7.10 from 7.04) and in the 30th min my screen goes to sleep mode with amber led
I've been searching for the solution for many days, and when I found your post i said to my self that it would be a good idea to contribute :)

---

### Post by bingoUV on 2007-11-03
> **Jose Catre-Vandis said:**
> Do you mean in /etx/X11/xorg.conf or another file?

no, create  a file ~/.xsession , and write the command in it. Now restart the X server by a ctrl-alt-backspace.

---

### Post by Jose Catre-Vandis on 2007-11-03
> **bingoUV said:**
> no, create  a file ~/.xsession , and write the command in it. Now restart the X server by a ctrl-alt-backspace.

OK thanks :)

Won't even let me have an empty file called .xsession, borks the login?

---

### Post by Shinoda on 2007-11-03
Try [this]("http://ubuntuforums.org/showthread.php?t=597832#post3673565").

---

### Post by Jose Catre-Vandis on 2007-11-04
> **Shinoda said:**
> Try [this]("http://ubuntuforums.org/showthread.php?t=597832#post3673565").

Great, that fixed it for me :)

---

### Post by krambo on 2007-11-19
> **Shinoda said:**
> Try [this]("http://ubuntuforums.org/showthread.php?t=597832#post3673565").

This worked for me too - many thanks :)

---

