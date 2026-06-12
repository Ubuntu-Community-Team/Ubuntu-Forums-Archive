---
title: "[SOLVED] Metacity"
date: 2008-05-14
forum: Desktop Environments
---

### Post by dozersmasher on 2008-05-14
Ok, huge prob: I tried to switch metacity for XFWM4, now I want to switch back, but can't. It is very annoying when I have to start it manually. Does anyone know how to change the WM to Metacity in Ubuntu Gutsy Gibbon?

---

### Post by sdennie on 2008-05-14
Is it possible that you saved your sessions with XFWM4?  One thing to try would be to login, switch to metacity (Alt-F2 then metacity --replace) then go to System->Preferences->Sessions->Session Options and click the Remember Currently Running Applications button.  Logout and back in to see if the change has worked.

---

### Post by dozersmasher on 2008-05-15
no, that made it freak out. I did some wierd commands in terminal. I'll see if I can dig up the commands.:confused:

---

### Post by dozersmasher on 2008-05-15
Got it. The commands I used were here: [http://ubuntuforums.org/showthread.php?t=88393](http://ubuntuforums.org/showthread.php?t=88393) to reverse it:
```
sudo sed -i "s/xfwm4)/xfwm4|openbox)/" /usr/bin/gnome-wm
echo export WINDOW_MANAGER=/usr/bin/metacity >> ~/.gnomerc
```

---

