---
title: "Toolbar disappeared [Gnome, Ubuntu 8]"
date: 2008-10-16
forum: Desktop Environments
---

### Post by frobenius123 on 2008-10-16
I'm not sure what the reason is, but my top toolbar no longer shows up when gnome starts. This means that the only way for me (not being a very sophisticated user) to open a terminal is to SSH into the box remotely, set DISPLAY=:0 and run xterm or similar...

Any idea what might be causing this or which logs/config files I should look in?

TIA

---

### Post by jhernandez1270 on 2008-10-16
boot up and log in to the box that has the Gnome panel (top toolbar) missing.
Right-click anywhere on the screen
Select Create-launcher
Under the name field type : Terminal
Under the the command: field type: gnome-terminal

Click OK

Launch the terminal and type:

gnome-panel

or 

sudo gnome-panel

it should come up for you

to insure it comes up again after reboot, click on System>Preferences>Sessions

in the Sessions Options tab click the "Remember Currently Running Applications" button

hope this helps

---

### Post by jonlightyear2000 on 2010-06-24
Hey Jhernandez1270, 

Wow! That really helped! I didn't think I could do anything on Ubuntu but now I'm dead proud of myself!

I can't find session manager in preferences though! Any idea what's wrong? 

The toolbar disappears when a start a new session meaning I can't access new network connections!

---

