---
title: "autostart compiz at xfce session"
date: 2008-02-03
forum: Desktop Effects &amp; Customization
---

### Post by jipke on 2008-02-03
Today I installed XFCE on (a working GNOME with compiz) Ubuntu to give it a try. I didn't installed the xubuntu metapackage, don't need all the extras. I installed XFCE4 instead. Everthing works fine, except compiz doesn't autostart in XFCE. After I login I have to enter ```
compiz --replace
``` in a terminal to make it work.
I searched the forum and came across some solutions. One mentioned that saving the session while compiz is running should do the thrick. Unfortunately is doesn't for me. And replacing ```

Client0_Command=xfwm4
``` with ```
Client0_Command=compiz
``` in file /etc/xdg/xfce4-session/xfce4-session.rc only leaves me with borderless windows after a login.

How do I get compiz autostart at login? Thanks in advance.

---

### Post by sisco311 on 2008-02-03
open compizconfig setting manager, go to the 'window decoraton' plugin and type your command to run your window decorator in the 'Command' box.

the default window decorator in xubuntu is gtk-window-decorator. if you are using emerald, then the command is emerald.

to install compizconfig setting manager type:
```
sudo aptitude install compizconfig-settings-manager
```in a terminal.

to run it type ccsm or go to the Applications -> Settings -> Advenced Desktop Effects Settings

---

### Post by srlapo on 2008-02-14
I had a similar problem. Besides the step on the previous post you need to do something else to fix it .
[http://ubuntuforums.org/showthread.php?t=623752&highlight=compiz+xfce](http://ubuntuforums.org/showthread.php?t=623752&highlight=compiz+xfce)
The step 5 on that thread should ensure that compiz starts automatically at login

---

