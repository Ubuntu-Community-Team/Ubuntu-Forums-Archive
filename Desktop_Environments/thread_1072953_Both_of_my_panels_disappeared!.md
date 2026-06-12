---
title: "Both of my panels disappeared!"
date: 2009-02-17
forum: Desktop Environments
---

### Post by lethalfang on 2009-02-17
I'm using Ubuntu Desktop 8.10. Both of my top and bottom panel of my desktop disappeared after I log in. As a result, I have difficulty accessing any of my softwares in the application menu or launcher on the panel. 
Please help!

I am only able to get onto firefox by putting a CD in to have the file explorer automatically launched, so I can find the firefox launch script in /usr/bin and open firefox that way. 

I don't use shortcut keys very often, but I tried a few, e.g., alt-F1 and alt-F2, and nothing happens...... 

What happened there?

---

### Post by trepid666 on 2009-02-17
Is it a fresh install? have u turned off your computer yet since installing?

open terminal and run

sudo gnome-panel

---

### Post by lethalfang on 2009-02-17
> **trepid666 said:**
> Is it a fresh install? have u turned off your computer yet since installing?

open terminal and run

sudo gnome-panel

Yes, this is pretty much a fresh install.
I installed the thing earlier today, then installed some automatic updates including the latest kernal, etc., then I restarted and saw no problem. I then installed some other software, but when I restarted again, the panels are gone.
...
I ran that command "sudo gnome-panel" in the terminal, and got
sudo: gnome-panel: command not found

---

### Post by UbuntuNerd on 2009-02-17
try this in a terminal:```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by lethalfang on 2009-02-17
Well, I thank everyone for the help. 
Apparently, I must've accidentally deleted something, since tripid666 suggested that I ran "sudo gnome-panel" and the terminal returns "command not found."
So I took a guess and ran the command "sudo apt-get install gnome-panel," and everything is restored!
Woohoo! Saved me a whole day reinstalling everything!

---

### Post by richardi on 2009-04-16
Thanks Lethalfang - I just had the same problem after updating Nvidia drivers to 180.11. Reinstalling gnome-panel as you guessed did the trick.

---

