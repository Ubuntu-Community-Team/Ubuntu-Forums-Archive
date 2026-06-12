---
title: "Xubuntu 12.04 Application Autostart command is ignored"
date: 2012-06-05
forum: Desktop Environments
---

### Post by cacv12000 on 2012-06-05
In Xubuntu 12.04 I'm trying to run the following command at startup to align my dual monitors:

/usr/bin/xrandr --output LVDS1 --auto --output VGA1 --auto --right-of LVDS1

On my system this command is completely ignored by the XFCE session and startup application at startup.

If I input the command in a terminal it works as intended.

Any ideas as to what could be wrong?

Thanks

---

### Post by ajgreeny on 2012-06-05
> **cacv12000 said:**
> In Xubuntu 12.04 I'm trying to run the following command at startup to align my dual monitors:

/usr/bin/xrandr --output LVDS1 --auto --output VGA1 --auto --right-of LVDS1

On my system this command is completely ignored by the XFCE session and startup application at startup.

If I input the command in a terminal it works as intended.

Any ideas as to what could be wrong?

Thanks
Trying to run it how?

You can't just put that command into the startup applications command box and run it that way, you may have to make a shell script of it, and point to that in the startup applications list.

You can also try with the complex command ```
bash -c "/usr/bin/xrandr --output LVDS1 --auto --output VGA1 --auto --right-of LVDS1"
```in the command box, but I am not totally sure about that.  A script certainly should work with no problems as far as I can see.

---

### Post by LewisTM on 2012-06-05
The system might need a short delay before running that command.
Try 
```
sh -c "sleep 10 && /usr/bin/xrandr --output LVDS1 --auto --output VGA1 --auto --right-of LVDS1"
```
If it works you can try decreasing the delay a bit.

Cheers!

---

### Post by cacv12000 on 2012-06-05
The following command solved the problem:

sh -c "sleep 10 && /usr/bin/xrandr --output LVDS1 --auto --output VGA1 --auto --right-of LVDS1"

Thanks!

---

### Post by LewisTM on 2012-06-05
Cool!
Please mark as SOLVED.

---

