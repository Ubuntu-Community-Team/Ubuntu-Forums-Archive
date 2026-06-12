---
title: "Why doesn't gnome see the proper resolution?"
date: 2006-08-15
forum: Desktop Environments
---

### Post by endfx on 2006-08-15
I have a laptop with intel 945GM graphics in it. I've setup xorg.conf to use the i810 driver and have the resolution specified as 1680x1050 (The only resolution I have specified in the "Screen" section of the xorg.conf file)

But gnome still displays 1280x1024. And in System->preferences->screen resolution it only lists 1280x1024 as the closest thing to 1680x1050.

Does anybody know why this gnome won't let me select the proper resolution?

---

### Post by endfx on 2006-08-16
Can someone tell me where the config file is for gnome where it would keep track of what resolution is currently being  used?

---

### Post by orb9220 on 2006-08-16
Try

sudo dpkg-reconfigure xserver-xorg

in a term

---

### Post by hecato on 2006-08-16
Also in /etc/gdm/gdm.conf search the default launch of X....

At the end of the line you can add 

```

-- --logverbose 6

```

irc.


Dont know if the -- are for something special.

Anyway, after that, restart the X (you can log out and before enter user name and password hit CTRL+ALT+BACKSPACE [restart x]), then you can check the /var/log/Xorg.0.log and see the valid "pool" of modes... and the diferent validations of test done...


If you see the resolution that you whant in that log file like aprovated, then you can add it (the name) to your Xorg configuration file. For example "1024x768_60" instead of the name "1024x768"...

---

