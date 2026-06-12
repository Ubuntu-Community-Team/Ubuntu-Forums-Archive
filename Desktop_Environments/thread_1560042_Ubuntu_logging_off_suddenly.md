---
title: "Ubuntu logging off suddenly"
date: 2010-08-24
forum: Desktop Environments
---

### Post by rlopes528 on 2010-08-24
This happens once in a while:

I'm happily surfing the Internet, working or doing anything else and suddenly Gnome logs off.
That's a pain in the *** really.

Any ideas?

---

### Post by clrg on 2010-08-24
Does anyone besides you have an account on that machine? They might be accessing it with vnc or ssh and log you off to annoy you (I used to do that =D )

---

### Post by rlopes528 on 2010-08-24
> **clrg said:**
> Does anyone besides you have an account on that machine? They might be accessing it with vnc or ssh and log you off to annoy you (I used to do that =D )

Unless someone hacked into my box no :)

---

### Post by mendhak on 2010-08-25
Have you installed anything recently or made any system changes?

If you can't remember any installs or updates, you could have a look at Synaptics Package Manger logs (File > History).  

You could also have a look at the files in /var/log - 'messages' or 'syslog' to see if there are any events that correspond to your relog.

---

### Post by mendhak on 2010-08-25
Ah, not sure if this is related, but there's an incomplete bug about this [here](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/511095) and there was another unresolved thread about it [here](http://ubuntuforums.org/showthread.php?t=1387438).

Reading that thread doesn't give you much hope, everyone has different circumstances in which this logout happens - BUT, one general area for a few of the people, (which is the only pattern emerging in this chaotic problem) is that it could be related to X-Server.

---

