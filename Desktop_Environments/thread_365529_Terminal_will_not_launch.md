---
title: "Terminal will not launch"
date: 2007-02-19
forum: Desktop Environments
---

### Post by mbc2000 on 2007-02-19
Hello,

I can't launch a terminal using Applications | Accessories | Terminal.  I get a 'Starting Terminal' in the taskbar, but it disappears after a couple of seconds.  I'm using Ubuntu-Edgy.


[edit] I figured it out.  I have xinerama running with nvidia-glx.  The answer is here:  [http://ubuntuforums.org/showpost.php?p=1644324&postcount=7](http://ubuntuforums.org/showpost.php?p=1644324&postcount=7)

---

### Post by ubix on 2007-02-19
**R-click** on desktop background, select **Create Launcher**. Enter something (whatever) in the **Name** field, and enter **[COLOR="Red"]xterm[/COLOR]** in the **Command** field. _Click OK_. This will create a new icon on your desktop. Clicking it will open a vanilla X11 terminal. In it enter **[COLOR="Blue"]gnome-terminal[/COLOR]**. This is the command that you have troubles with, _hence, you should see the error that it generates_!

---

