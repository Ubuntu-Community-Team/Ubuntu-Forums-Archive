---
title: "[SOLVED] Xubuntu 7.04 - no taskbar, other"
date: 2007-06-08
forum: Desktop Environments
---

### Post by kansas_plainsman on 2007-06-08
Running xubuntu on a mini-itx system and overall it's quite usable.

Problem is that the xfce desktop doesn't have the taskbar, nor the other 'bar' and I can't find any way to get them to appear.  Any suggestions?

---

### Post by Cushie on 2007-06-08
Try right mouse click on panel or bottom of screen

---

### Post by ugm6hr on 2007-06-08
Or:
```
xfce4-panel
```
in Terminal.

Then: Applications->Settings->Settings Manager->Panel 
to customise the number and location of panels.

---

### Post by kansas_plainsman on 2007-06-08
Thank you on the xfce4-panel command in terminal suggestion - of course, I had to append an "&" to keep them there after dismissing the terminal, but it worked.

Is there a way to have it start that way by default? - UPDATE - Answered my own question: I entered the command as an autostart - thanks again.

---

### Post by daInvincibleGama on 2007-12-29
Could you post what you did to make it stick? typing xfce4-panel& in console did not help for me. It just closed after I closed terminal.

Also how do I put it in the startup routine?

---

### Post by kansas_plainsman on 2007-12-29
It's been a while since I did that - search 'autostart' for xfce and you should see how to add such a command.

A quick google turned up this link:

[http://gentoo-wiki.com/HOWTO_Autostart_Programs](http://gentoo-wiki.com/HOWTO_Autostart_Programs)

---

