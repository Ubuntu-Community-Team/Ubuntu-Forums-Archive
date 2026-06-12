---
title: "Docker in Openbox Show nm-applet"
date: 2010-02-28
forum: Desktop Environments
---

### Post by mooreted on 2010-02-28
Added these startup programs to OpenBox's autostart.sh:

tint &
docker &
nm-applet &

nm-applet does not show in Docker. However, if I open a terminal and run nm-applet it shows up in Docker. The cli displays:

** (nm-applet:4467): WARNING **: <WARN>  request_name(): Could not acquire the session service as it is already taken.  Return: 3


** (nm-applet:4467): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

nm-applet is shown in ps-aux after starting OpenBox, so it is autostarting and it automatically connects to my wireless network, so it starts and runs, it just doesn't automatically show in Docker.

---

### Post by kerry_s on 2010-02-28
you need to remove "OnlyShowIn=GNOME" from the applet in /usr/share/applications

---

### Post by mooreted on 2010-02-28
There is no nm-applet desktop file in that location. The program I'm running is in /usr/bin/nm-applet.

---

### Post by kerry_s on 2010-02-28
my bag i was thinking something else, sorry.

usually with the *box's it's more of a timing issue, you need to make sure docker starts first. try putting a delay on nm-applet.

```
sleep 3; nm-applet --sm-disable &
```

adjust the time to your system speed.

---

### Post by mooreted on 2010-03-01
I think your command is for Fluxbox. I remember using that when I was running flux. But you had the right idea. After searching for the sleep command for OpenBox I found this command that worked:

(sleep 3 && nm-applet) &

Thanks for the help.

---

