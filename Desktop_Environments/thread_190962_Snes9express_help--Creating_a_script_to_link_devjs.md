---
title: "Snes9express help--Creating a script to link /dev/jso to /dev/input/jso"
date: 2006-06-06
forum: Desktop Environments
---

### Post by ubundrew on 2006-06-06
Hi all;

First, just let me say that I am amazed by the number of people willing to assist those with less experience in ubuntu. Thanks!

On to my question:

I've gotten snes9express installed, and it runs fine. My only problem is that I have to manually create a link from /dev/jso to /dev/input/js0 (found this solution on another thread here) every time I boot so that my joystick (Logitech precision) works. I can't find a way to configure this to point to /dev/input/jso in the configuration options.

Can someone assist me in writing a script to automatically create the link? The command I use in the terminal is "ln /dev/input/js0 /dev". If I can get a script to do this then hopefully I can just run it at startup. 

Thanks again!

-Andrew

---

### Post by cmarker on 2006-06-07
you could creat a cron job to do run that command on startup.  You can search the forum for more information about cron jobs but you can edit them by doing.

```
sudo crontab -e

```

then input the desired command to be run on reboot

```
@reboot /bin/ln /dev/input/js0 /dev
```

let me know if that works

---

### Post by droazen on 2006-06-07
Add your ln command to /etc/rc.local - the commands in that file will be executed right after the runlevel 2 scripts during bootup.

Or try zsnes :)

---

### Post by ubundrew on 2006-06-07
[QUOTE=droazen]Add your ln command to /etc/rc.local - the commands in that file will be executed right after the runlevel 2 scripts during bootup.

Or try zsnes :)[/QUOTE]

That's perfect! Worked like a charm. Thank you both so much!

---

