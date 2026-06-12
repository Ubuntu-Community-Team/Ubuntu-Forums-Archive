---
title: "Both panels gone."
date: 2009-04-16
forum: Desktop Environments
---

### Post by Levviathor on 2009-04-16
I'm running Ubuntu 8.10.  Yesterday, when I booted into Ubuntu I was presented with a blank desktop.  Right-clicking did nothing, but Expo and Window Switcher both worked.  I was able to get a media player running.  I got an error when I tried to open a file, and the min/max/close buttons were spaced apart.

After some reading around, I found that I could open a terminal (couldn't get the run box to open) and type "gnome-panel".  This put it back, but it also removed the "alex@alex-laptop...$" prefix, causing it to ignore all further commands.  Closing the terminal would also cause the panels to close, and after I reboot I have to turn them on again.

I'm using a Dell I-1525, 4G, Pentium dual-CPU 1.73GHz machine.

---

### Post by PacSci on 2009-04-16
Suggestion: Type "gnome-panel &". You can then close the terminal. However, I don't know how to keep the panel starting up - try creating a '~/.xsession' file and adding 'gnome-panel' to it.

---

### Post by UbuntuNerd on 2009-04-16
try this command it should restore your panels to default:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by andrea000 on 2009-04-17
Try
ctrl backspace 
and see if that restarts it.

---

### Post by Levviathor on 2009-04-17
@PacSci, the panels still close after I closed the terminal.  I added the .xsession file (there wasn't one before), as you suggested, and it worked.  Sort of.

The panels started automatically, but there were a whole host of other problems.  The desktop didn't load (no background image, no icons, and right-clicking didn't do anything), everything had a win9x style look (flat, grey, sharp corners), my notification area didn't load any icons, and the list goes on.

@UbuntuNerd, nothing happened when I entered those >_>

@Andrea, ditto.


I found an interesting error in ~/.xsession-errors: "x-session-manager[5695]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout"

Not sure if this is relevant or not.

---

### Post by Crowchild on 2009-04-17
I am having the same problem. I rebooted my laptop after updating today and haven't been able to get the panels to stay.

I have to open a terminal and run them but as soon as I close the terminal (and leave the root session) it closes the gnome-panel.

If I try running gnome-panel without sudo, it tells me that 'A panel is already running'.

---

### Post by Crowchild on 2009-04-17
Rebooted and it seems to be work after trying UbuntuNerd's fix...!?!

Thanks.

---

### Post by Levviathor on 2009-09-03
This is a bit old, but I felt I should mention that I eventually just nuked my installation and reinstalled Ubuntu.

Unsurprisingly, that fixed it.

---

