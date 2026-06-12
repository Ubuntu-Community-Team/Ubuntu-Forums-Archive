---
title: "help lost the top part of the window!!"
date: 2008-04-18
forum: Desktop Environments
---

### Post by versidus on 2008-04-18
**[SIZE="3"]i have tri monitors with three different desktops, the middle one is fine, but the left and right desktop are a little messed up, when i open a window the top part is missing (the part  with the X to close and minimize and maximize and the title) how do i get it back?[/SIZE]**:confused:

[IMG]http://i88.photobucket.com/albums/k177/versidus/Screenshot.png[/IMG]

and here is me trying to fix it!

[IMG]http://i88.photobucket.com/albums/k177/versidus/l_d623cf091779bc43f238d8016d4494d4.jpg[/IMG]

---

### Post by OffAxis on 2008-04-18
as in, the window opens up too high relative to the desktop?

Use the CTRL key (might be the ALT key, I forget at the moment) + the left mouse button to 'Grab' any part of the program that opened up and drag it down the screen.

---

### Post by perlluver on 2008-04-18
It could be compiz if you just installed it, then hit alt+f2 and type either emerald --replace or metacity --replace, whichever you prefer.

---

### Post by versidus on 2008-04-18
[SIZE="3"]**the emerald --replace command worked but AWN stopped working, so i rebooted and it all went back to the way it was before, with awn working fine, but missing the top part or the windows on the left and right desktop....  **[/SIZE]:mad:

---

### Post by versidus on 2008-04-18
**[SIZE="3"]why wont emerald stay on???[/SIZE]**

---

### Post by perlluver on 2008-04-18
Do you have Emerald installed?  If so, which version of Ubuntu are you running?

---

### Post by versidus on 2008-04-19
[B][SIZE="3"]i am running 7.10 and yes Emerald is installed.
here are a few other things i noticed about the three desktops, all the effects work on the middle desk top, like reflection, i have my work space set to 4 witch is fine on the middle desktop, but on the other two desktops i only get two??? weird right, if i go to the presences to adjust it it shows that it is set to 4??? what do you think is going on here???[/SIZE][/B]:confused:

---

### Post by prshah on 2008-04-19
> **versidus said:**
> [SIZE="3"]**the emerald --replace command worked but AWN stopped working, so i rebooted and it all went back to the way it was before, with awn working fine, but missing the top part or the windows on the left and right desktop....  **[/SIZE]:mad:

You may not have direct rendering enabled on the other two desktops. Try this```

glxinfo -display :0 | grep direct
glxinfo -display :1 | grep direct
glxinfo -display :2 | grep direct

```

---

### Post by versidus on 2008-04-19
**[SIZE="3"]this is the error i get.[/SIZE]**




```
versidus@versidus-desktop:~$ sudo su
[sudo] password for versidus:
root@versidus-desktop:/home/versidus# glxinfo -display :0 | grep direct
direct rendering: Yes
direct rendering: Yes
direct rendering: Yes
root@versidus-desktop:/home/versidus# glxinfo -display :1 | grep direct
Error: unable to open display :1
root@versidus-desktop:/home/versidus# glxinfo -display :2 | grep direct
Error: unable to open display :2
root@versidus-desktop:/home/versidus# 

```

---

