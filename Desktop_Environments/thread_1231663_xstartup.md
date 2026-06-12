---
title: "xstartup"
date: 2009-08-04
forum: Desktop Environments
---

### Post by num on 2009-08-04
Hello,

I got Ubuntu 8.04 LTS with encrypted LUKS. Now I been trying to alter the xstartup file in the .vnc folder in my username folder but whenever I start up vncserver I look at the logs and ti says that it cannot find the xstartup file in the .vnc folder. But I checked it is there. What am I doing wrong?

---

### Post by num on 2009-08-04
This is my log:

[http://pastebin.com/m64e9d43c](http://pastebin.com/m64e9d43c)

---

### Post by Brandon Williams on 2009-08-04
What are the permissions on the file? Is it executable? Also, it would be helpful for you to post the content of the file here (make sure you mark it as code).

---

### Post by num on 2009-08-05
My account and others have the ability to read and write.

The contents are:

```
#!/bin/sh



xrdb $HOME/.Xresources

xsetroot -solid grey

x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

x-window-manager &

/etc/X11/Xsession
```

---

### Post by num on 2009-08-05
the thing when i run vnc i just get a terminal window but i want to see the whole desktop. please help me.

---

### Post by Brandon Williams on 2009-08-05
xstartup is a script which is executed. Your must have executable permission for this to work.

---

### Post by num on 2009-08-05
well the thing is i want to see the actual desktop here, in fact i really want to see the same session as a person would see on the computer. what is the best way to set this up?

---

