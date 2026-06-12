---
title: "error starting GNOME settings daemon"
date: 2008-02-01
forum: Desktop Effects &amp; Customization
---

### Post by Shay Andrews on 2008-02-01
I just booted up and got this message:
```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```
AWN has also stopped working; I'm not sure if that's a separate issue or not.
I found other threads with similar problems, but no solutions. Can anyone tell me how I might fix this? (Keeping in mind that I'm a relative newbie to Linux.)

---

### Post by pbh101 on 2008-02-01
I have the same error pop up approximately every other boot.  It doesn't seem to affect anything as far as I can tell.

pbh

---

### Post by Shay Andrews on 2008-02-01
I've lost my window theme and cursors. And as I mentioned, AWN is no longer working.

---

### Post by PartickThistle on 2008-02-05
Had the same issue.  Installing xscreensaver helped, but not completely.

---

### Post by Shay Andrews on 2008-02-05
I uninstalled emerald, and the problem went away.

---

### Post by MountainX on 2008-02-28
I'm getting this too. I would like to understand the problem so I can fix it. Can anyone offer any suggestions? Thanks.

---

### Post by Joeb454 on 2008-02-28
Try logging out then logging back in. Always fixes it for me.

As for how often it happens - about 4 times since I've had the system installed (Which is the end of October time :))

---

### Post by Nythain on 2008-02-28
Friend is having the exact same problem... on a default install of Ubuntu...  nothing fancy extra, and it happens seriously almost every time he logs in...

anyone out there have anything more substantial to go by??? possible causes, fixes, anything??? Its really hard to turn people on to an operating system that doesnt operate :( (i would like it to be known that for me, ubuntu has always operated flawlessly and with minimal effort on my part, but im already a convert :P)

---

### Post by DJCalarco on 2008-05-15
Drove me nuts too for a while, heres how I fixed it...

login to a failsafe terminal
$ vi /etc/network/interfaces

Make sure the following lines are in there, and that they arent commented out:

auto lo
iface lo inet loopback

Also, comment out anything involving IPv6 if you dont use it.

then:

$ sudo ifconfig lo up
$ exit

Reboot your box and your good to go.  Dont forget to change your session back to Gnome!

---

### Post by johnblack on 2008-07-04
Thanks DJCalarco,
Very clearly guide, I've fix my laptop with it :)

---

