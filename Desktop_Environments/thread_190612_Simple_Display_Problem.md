---
title: "Simple Display Problem"
date: 2006-06-06
forum: Desktop Environments
---

### Post by lear45builder on 2006-06-06
Hi,

I have a small problem.  I've got Ubuntu running well on a 700mHz Intel box, connected to a 17" LCD.  However, each time I reboot, while the resolution stays at 1280X1024, the refresh rate always defaults to 75Hz, which makes the display a bit fuzzy.  LCD panels run at 60Hz, and when I click on resolution and change it back to 60, all is well.  How do I make the change stick once I reboot?

Thanks!

LB

---

### Post by bswilson on 2006-06-06
You need to update your X Windows configuration.  On Dapper, the file you need to modify is /etc/X11/xorg.conf.  

**Step 1. Back up xorg.conf**
In a terminal window, run this command.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BAK
```

**Step 2. Update xorg.conf**
Run this command to open xorg.conf for editing:
```
gksudo gedit /etx/X11/xorg.conf
```
Find the section that starts with **Selection "Monitor"**.  Add the item below before the **EndSection** stanza.
```
StartSection
        ...
        ...
        VertRefresh   60
EndSection
```

**Step 3. Save and exit!**
Save your file and exit from gedit.  Now, you'll want to restart your X Windows display by typing Ctrl-Alt-Backspace.

---

### Post by lear45builder on 2006-06-06
Hi,

I'm running Breezy, but it would prob be the same.  Just edit the X11 config file to utilize VertRefresh of 60 as the only option.  Thanks, I'll give that a shot....

LB

---

