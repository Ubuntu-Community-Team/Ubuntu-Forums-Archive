---
title: "hard disc keeps running"
date: 2008-12-22
forum: General Help
---

### Post by emanresu on 2008-12-22
hi all,

i installed [ossec-HIDS]("http://ubuntuforums.org/showthread.php?t=919472") last week. since then, it seems like just about anytime i do something in Ubuntu, my harddrive starts writing or reading or something, i can hear the activity and the green disc drive light is illuminated. is this common with the ossec-HIDS install? are there other less common applications i might install later for customization that are likely to do this?

---

### Post by sdennie on 2008-12-22
You should be able to figure out what is causing the disk activity with:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"
tail -f /var/log/syslog

```

To turn off the log spam afterwards, use:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

---

### Post by emanresu on 2008-12-22
after tailing the log:

> Dec 22 13:50:30 Shadowsuite kernel: [ 1590.522328] gconfd-2(6508): dirtied inode 749249 (?) on sda6

i have no idea what a (dirtied) inode is.

the rest is kjournald running. i suppose it's ossec writing a bunch of messages then. but i would like to know what an inode is and what it's relevance is. (all about those hanging prepositions.)

---

### Post by sdennie on 2008-12-22
[http://en.wikipedia.org/wiki/Inode](http://en.wikipedia.org/wiki/Inode)

Having kjournald or pdflush causing activity every 5 seconds or so is normal.  It's generally not harmful to performance but, if that really is the culprit of your performance issues (it probably isn't), this guide might be useful for you: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998")

---

### Post by emanresu on 2008-12-22
the HOWTO was good. thanks.

---

