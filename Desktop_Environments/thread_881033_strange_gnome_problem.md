---
title: "strange gnome problem"
date: 2008-08-05
forum: Desktop Environments
---

### Post by aqshin on 2008-08-05
Gnome does not start if the mouse is not plugged. Even if I reboot, it does not help. Also, Alt+F1 does not work when this problem happens. But when I plug mouse (logitech MX1000) and reboot it works. Any idea how to fix this problem?

---

### Post by KatBuntu on 2008-08-05
Yeah, very strange!! 
Press Ctrl+Alt+F2 and try to reconfigure your xorg.conf file:
```
# dpkg-reconfigure xserver-xorg
```
If you haven't started your X start them with:
```
$startx
```
If the X started, move to the Ctrl+Alt+F7 and restart the X with Ctrl+Alt+Backspace

...Of course with your mouse plugged

---

### Post by aqshin on 2008-08-05
Thanks for the reply. Actually no any "Alt" combinations works. I mean Alt+F1, F2, F3. The only thing I can do then is rebooting, like holding down power button. Though, I usually use Alt+SysReq+k (then, r s e i u b). Read it at some thread for safe reboot.

I think this may be because I installed ubuntu (7.10) with the mouse plugged. And therefore gnome is configured for this setting. Have no idea though how to see/check it.

---

### Post by aqshin on 2008-08-05
Actually, there is no problem when mouse is plugged before powering on the laptop. The thing is then I will have to carry mouse wherever I take the laptop. Not a big problem. But it would be better if i solve it ;)

---

### Post by KatBuntu on 2008-08-05
> **aqshin said:**
> Actually, there is no problem when mouse is plugged before powering on the laptop. The thing is then I will have to carry mouse wherever I take the laptop. Not a big problem. But it would be better if i solve it ;)

Then you can start a graphic session! open a terminal, and before you hit the <ENTER> for the > #dpkg-reconfigure xserver-xorgcommand, unplug the mouse, then hit the <ENTER>

---

### Post by aqshin on 2008-08-13
Thank you! this solved the problem..

---

