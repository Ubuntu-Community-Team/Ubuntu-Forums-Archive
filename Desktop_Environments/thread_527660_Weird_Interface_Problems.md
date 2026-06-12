---
title: "Weird Interface Problems"
date: 2007-08-16
forum: Desktop Environments
---

### Post by Eclipse9069 on 2007-08-16
Well, basiclly I have been having new problems with my interface.

First of all, the clock is pused to the left, infront of all the items. 
I have no close, maximize, or minimise buttons, and on the bottom taskbar my garbage bin is pused to the left.

Here is a screenshot:
[[IMG]http://img441.imageshack.us/img441/7374/screenshotki7.th.jpg[/IMG]](http://img441.imageshack.us/my.php?image=screenshotki7.jpg)

You can see the problems in the screenshot.

Any help would be appreciated.
Thanks.

---

### Post by diatribe on 2007-08-16
have you installed any new programs or changed themes?

---

### Post by Eclipse9069 on 2007-08-16
Yep, downloaded a few themes from art.gnome.org.

Installed some, tried em, but ended up going back to Human theme.

It was working fine for a bit, then I restarted and it has been like this ever since.

---

### Post by Eclipse9069 on 2007-08-16
It seems like when I turn off Compiz effects, everything is normal, but when I enable Compiz again, it goes back to how it was.

Anyone know why? Or How I can fix it?

---

### Post by jim_p on 2007-08-17
You can set metacity to take over if compiz breaks down.
In compiz's settings, (can't remember the exact location) you can set a command
that your system will ball back to, if compiz fails. Use this > metacity --replace

For now, just run the command to get your borders back.
As for the panel, move the objects where you wish, and then lock them there
(right click on them >> Lock to panel)

---

### Post by BuffaloX on 2007-08-18
Getting your clock and bin back in place is easy. :)
You just right click, and select move.
If items are locked, you unlock the same way.

But you cant move items into places where locked items are, so you may have to unlock/lock other items on your bar too.

If you wish, you can even move items from one bar to another.

---

### Post by BuffaloX on 2007-08-18
About your windows.

Compiz / fusion / beryl all seem to all have this weird behaviour on some graphic cards.

If you have Nvidea graphic card, you need to add an option line to xorg.conf.

open a terminal, enter:
sudo gedit  /etc/X11/xorg.conf

find the section "Screen" and add the following line.
    Option         "AddARGBGLXVisuals" "True"

Reboot your system, and try compiz again...

---

