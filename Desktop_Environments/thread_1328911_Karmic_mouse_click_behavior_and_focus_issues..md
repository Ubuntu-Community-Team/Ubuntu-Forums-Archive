---
title: "Karmic mouse click behavior and focus issues."
date: 2009-11-16
forum: Desktop Environments
---

### Post by thanatoast on 2009-11-16
Hello,
I am having some strange problems with Karmic, using Gnome.
I open gedit and start typing. I the move the mouse up and click on the File menu and get the file menu (as expected). I then click back on the text area. I am no longer able to click on the File menu. Clicking on the File mene moves the text pointer to the top line in the text area. If I right click on File (or anyplace else on the desktop), I get the editor menu (Undo/Redo/Cut/Copy/Paste/etc) as if the mouse pointer is still over the text area.
Another similar behavior: I left click on gedit on taskbar to minimize it, click it again to restore it. Then right click in the text area of gedit. It behaves exactly as if I had right clicked on gedit on the task bar and shows that menu (Minimize/Maximize/etc). Clicking in the text area makes that menu go away and right clicking again behaves as it should. This behavior is similar in other programs I have tried. Hoovering over taskbar items (and buttons in firefox) gives some odd results at times as well.  Gnome seems to know that I am hoovering, but shows text content from a firefox page I no longer have open (I think that's what it was showing). Sometimes the mouse clicking seems to have completely stopped.  If I press Alt-F for the file menu, or some other menu, the appropriate menu opens and mouse clicking begins working again in that program. Also, the scroll wheel acts in a similar manner at times. If I place the mouse over a gedit program and use the scroll wheel it will scroll another window behind it.  Left clicking in gedit (when this happens) changes the focus to the window that was behind gedit. Similar to the above, if I click on an item in the taskbar, then move the mouse up to an item on the desktop and use the scroll wheel it acts as if the mouse is hoovering over the taskbar still and scrolls through open programs. (I also just discovered that when it is doing this, Alt-Tab does not work either.)

Additionally, I pre-wrote this message using gedit (while I experimented with the mouse).  I noticed that when things were "not right" the text cursor would sometimes vanish mostly while moving the pointer back and forth using the arrow keys) and typing would not always work when the cursor was gone. Once just after I right clicked in gedit to make the cursor come back the screen turned black (the screen-saver, I assume) and returned to normal immediately when I moved the mouse.

If it matters, this is a new install on a Dell Optiplex GX150. The mouse is a TrackMan Marble+ (ps/2). I do not have visual efects turned on. I do not have an xorg.conf file. 

I am hoping to take this machine offline by the end of the week. I have a hard enough time convincing the people I will share it with that Linux is the way to go, without having to explain that they need to right click a few times to be able to left click on something. Should I just find a different distro, or is someone actually trying to fix this?

Thank you for taking the time to read this.

---

### Post by misja on 2009-11-19
I'm experiencing problems with mouseclick/focus behaviour as well.
The problems started since I upgraded to 9.10.

I have the problems only on one machine though, on two other pc's there are no problems.
Could it have something to do with my dual monitor setup perhaps?

---

### Post by Jbike on 2009-11-19
I am having similar problems Sometimes the mouse just stops working, leaving the pointer at a fixed spot on my monitor... Three seconds to a minute later it comes back just fine.  Any suggestions?  


Jbike

---

### Post by jorisjoris on 2009-11-24
I'm having the same problem.  Unplugging the mouse and plugging it back in solves the problem temporarily.  I'm also experiencing Nautilus crashes.  I noticed that a new version of Nautilus came out, but upgrading to that has not resolved the issue.

---

### Post by tnvkrishna on 2009-11-24
even i too have a similar problem..

---

### Post by vogia on 2009-11-28
yes i've the same problem

i's a problem of focus on multi-windows.

---

### Post by lulaz on 2010-01-24
Has anybody found a fix for this problem ?

---

### Post by nickez2001 on 2010-01-25
I'm having similar problems. I can't left click on the menus in nautilus. But moving the window around fixes it temporarily. However, I have the same problem in firefox. And not even reboot fixes that.

---

### Post by eccomaggio on 2010-02-01
I've been having problems on my Asus UL30 with the cursor since I upgraded to Karmic. The cursor jumps to points in the text, sometimes while i'm typing. It seems to be not entirely random, often returning to the same spot over and over, though the exact spot seems to change randomly. If I have recently cut and pasted something, it randomly dumps the contents of the cursor at the spot I'm typing, sometimes several times in a row. It's very strange, and it's the first time I've experienced this behaviour with Ubuntu. I've tried playing with mouse sensitivity settings, but it happens even when I use the trackpad, with the mouse disconnected. It doesn't matter if I'm using the notebook on my knee or on a firm surface. It's making Ubuntu almost unusuable... :(

Anyone experiencing anything similar?

---

### Post by permute on 2010-02-06
It was the multiple monitor setup, (using Synergy in my case), that was causing my problem. As soon as I disabled Synergy (actually QuickSynergy) the left clicks and mouse focus issues went away.

---

### Post by gkid on 2010-02-07
[http://ubuntuforums.org/showpost.php?p=8786820&postcount=23 ]("http://ubuntuforums.org/showpost.php?p=8786820&postcount=23")
go to the link above hope it works for you as it works for me.
[]("http://ubuntuforums.org/showpost.php?p=8786820&postcount=23")

---

