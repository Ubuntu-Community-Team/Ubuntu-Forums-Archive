---
title: "Taskbar and menu lost"
date: 2009-01-14
forum: General Help
---

### Post by malel on 2009-01-14
Some urgent help please . I just removed Evolution through Synaptic and have lost my Taskbar and the Applications menu. I am not able to get run Terminal. How can I get these back ??

Thank you

---

### Post by pieisgood4589 on 2009-01-14
Hmm... So you tried "GNOME-Panel" and it didn't work?

You could try resetting GNOME settings to default by running this-
rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Trust me, it's safe to run, other users can confirm that too. What it does is removes GNOME settings to restore them to defaults.

---

### Post by malel on 2009-01-14
Thank you for the info but how do I get into the "Terminal" as I have lost the Taskbar and the Applications Menu

---

### Post by DarkDancer on 2009-01-14
Try this (it's the only way I could think of) hold down alt and hit f2. This should bring up the run application box. In that box there should be an option to "Show list of known applications" click the little arrow beside that and go down to terminal, double click it. The terminal should open, there is probably a better way, but I am at a loss.

---

### Post by malel on 2009-01-14
Thank you but Alt/F2 does not work for me .Nothing happens.  Something else perhaps?

---

### Post by adamlau on 2009-01-14
Ctrl+Alt+F1 into another terminal, log in and go from there.

---

### Post by malel on 2009-01-14
Thanks but that didn't help either . Nothing happened again . I tried a restart and then into recover mode which bought up the command line but even though I reinstalled Evolution and tried to install menu I still do not have a taskbar . It must be hiding there somehwere surely. I really do not want to reinstall the whole system ...

---

### Post by theWrkncacnter on 2009-01-14
Did you try running
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
from a virtual terminal? (ctrl-alt-F1)

Also I think there is a command to restart the panel in Xubuntu if it gets stuck in the off position, but I don't know if the same applies for Ubuntu.

From your desktop, try
alt-f2
killall gnome-panel

If gnome-panel is running, but stuck, this will kill it and bring it back.

---

### Post by theWrkncacnter on 2009-01-14
If alt-f2 isn't working, try the killall command from the virtual terminal.

---

### Post by mc4man on 2009-01-15
As far as your Applications menu, if still not functional go to places -> home folder -> view - 'show hidden files' -> .config -> menus and delete the applications.menu file.
That will restore the Applications drop down

---

### Post by malel on 2009-01-15
Thank you all for your replies . I was not able to carry out any of you instructions because all I had access to was the desktop Firefox and Thunderbird . I just couldn't access anything . Anyway I have reinstalled Ubuntu and bought it up to date and everything is working fine now. I guess the answer is not to delete Evolution because it is hooked into so many other applications

Cheers . This thread can be closed now .

---

### Post by jeh311 on 2009-01-16
> **mc4man said:**
> As far as your Applications menu, if still not functional go to places -> home folder -> view - 'show hidden files' -> .config -> menus and delete the applications.menu file.
That will restore the Applications drop down

this solved my problem

---

### Post by bidzapfc on 2009-01-18
> **theWrkncacnter said:**
> Did you try running
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
from a virtual terminal? (ctrl-alt-F1)

Also I think there is a command to restart the panel in Xubuntu if it gets stuck in the off position, but I don't know if the same applies for Ubuntu.

From your desktop, try
alt-f2
killall gnome-panel

If gnome-panel is running, but stuck, this will kill it and bring it back.

what is the command??

---

