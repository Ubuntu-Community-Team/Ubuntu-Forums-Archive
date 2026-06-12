---
title: "Nothing but the desktop picture"
date: 2008-07-15
forum: Desktop Environments
---

### Post by champs on 2008-07-15
This afternoon when I looked at my desktop, I had my VM running, a torrent downloading and Firefox with a number of open tabs, not to mention the menu bar and panel and an assortment of icons on the desktop.

Tonight there is nothing but the desktop picture. No menu bar or Panel, no icons.

I have tried ctrl-M, ctrl-alt-F etc.

I'm using Gnome on 8.04

---

### Post by llamakc on 2008-07-15
Press the key combo ALT+F2 and type in

```

nautilus

```

---

### Post by Yuki_Nagato on 2008-07-15
Try llamakc's suggestion first.

-----

Press "Ctr + Alt + F1" to get to a terminal.  Then enter

```
sudo shutdown -h now
```

This will shutdown your computer the same way it would if you had clicked to shut it down.  Buffers are emptied and processes warned.

Turn it back on.  Start the torrent application again - it should pick up.  Firefox will have cached all of the open tabs for when you start up again.  The VM session we cannot save.

---

### Post by champs on 2008-07-15
Sorry guys...... *Alt + F2* doesn't bring up the box to type a command, and

*sudo shutdown -h now* worked but when the system reloaded, all that comes up is the desktop picture. I can even change the desktop picture and the updates popup notification came up, but there is still no menus, panel or icons.

As for running programs, I created a folder on the desktop which now gives me access to File Browser, so I start everything I need, except the Menu panel at the top and bottom of the page.

---

### Post by Yuki_Nagato on 2008-07-15
Try running

```
nautilus
```

from the Alt + Ctr + F1 terminal instead.  If this does not work, we may have to re-install your desktop environment.

_[http://ubuntuforums.org/showthread.php?t=859478&highlight=gnome+menu]("http://ubuntuforums.org/showthread.php?t=859478&highlight=gnome+menu")_

Just found it.  This person seems to have had the same problem.  They fixed it by reconfiguring GNOME.

---

### Post by champs on 2008-07-15
Cheers for that......

Followed the steps in the link but still did not fix the problem, so this is what I did to fix it.

Firstly, I did CTRL+Alt+F1 for virtual terminal and 

Code:
```
sudo dpkg-reconfigure ubuntu-desktop 
```

But I received the reply ubuntu-desktop not installed

I then tried...

Code:
```
sudo apt-get install nautilus-open-terminal 
```

I went back to the GUI (Ctrl+Alt+F7)but did not get the 'open terminal' option on the desktop in order to use

Code:
```
 gnome-panel & 
```

Bit the bullet and went back to the terminal and did

Code:
```
apt-get install ubuntu-desktop 
```

Once it was finished installing, I went back and did right click, "open terminal" and

Code:
```
gnome-panel & 
```

All fixed..... Interesting that my desktop icons were all missing. I found them all in the Garbage Bin. Will be having words with two little girls that I have been told were playing in the study yesterday afternoon.

---

### Post by Yuki_Nagato on 2008-07-15
> Will be having words with two little girls that I have been told were playing in the study yesterday afternoon.

Ctr + Alt + L

And thank you for the follow-up.

---

### Post by Izek on 2008-07-16
I believe this also happens sometimes when Ubuntu doesn't have enough RAM. logging out and back in solves the RAM issue though.

---

