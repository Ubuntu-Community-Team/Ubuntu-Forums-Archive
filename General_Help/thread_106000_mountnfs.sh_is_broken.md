---
title: "mountnfs.sh is broken"
date: 2005-12-19
forum: General Help
---

### Post by kbreit on 2005-12-19
When I run /etc/init.d/mountnfs.sh my system dies.  It still runs but is unable to run any programs.  A reboot is required to fix this.  I've seen this behavior on two comupters.  Can anyone give me any suggestions?

---

### Post by copperhead on 2006-03-24
I'm surprised that there are no responses to this message.  The same thing happens to me.  When I boot up and log in, all my applications work fine.  When I bring up a command prompt and run /etc/init.d/mountnfs.sh, my samba mounts connect fine, but it seems to kill something in my xserver.

When I try to run any applications from there on out, I get messages like the following:
```

talbrech@elrond:/mnt/gandalf$ amarok
: cannot connect to X server :0.0
talbrech@elrond:/mnt/gandalf$ gaim

(gaim:9356): Gdk-CRITICAL **: gdk_display_get_name: assertion `GDK_IS_DISPLAY (display)' failed

** (gaim:9356): WARNING **: cannot open display: unset

```

Any ideas as to what the problem is?

---

### Post by copperhead on 2006-03-24
I commented out the "bootclean mountnfs" line at the end of the mountnfs.sh script, and the mount comes up fine without killing my computer.

EDIT: I wonder if [this link]("http://www.sitening.com/blog/2005/10/17/bootclean-whacked-my-sockets/") offers any information... seems the bootclean was messing up his sockets.

---

