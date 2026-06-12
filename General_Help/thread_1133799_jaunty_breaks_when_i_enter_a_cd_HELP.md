---
title: "jaunty breaks when i enter a cd HELP"
date: 2009-04-23
forum: General Help
---

### Post by meeples on 2009-04-23
hey i'm running the Jaunty Jackalope beta at the moment and have just downloaded the iso for the final release so i can do a clean install and upgrade to ext4. just one thing.

every time i insert a blank cd into my cd drive everything on my desktop dissapears and i cant open brasero or access any files.

please help me. thanks. :(

---

### Post by prem1er on 2009-04-23
I'm not positive, but I think somebody had the same problem trying to backup some files yesterday or the day before.  I'll look for the post.  If I remember correctly, all of his directories would not be accessible.

---

### Post by meeples on 2009-04-23
thanks :D

---

### Post by Peter09 on 2009-04-23
looks like nautilus is crashing.

Try to recover by typing in a terminal

```
nautilus
```

Then put the CD in again. You should get a bunch of error messages on the terminal. Paste them here.

---

### Post by meeples on 2009-04-23
heres what i get in terminal :

```
meep@meep-desktop:~$ nautilus

(nautilus:4252): GVFS-RemoteVolumeMonitor-WARNING **: invoking IsSupported() failed for remote volume monitor with dbus name org.gtk.Private.HalVolumeMonitor: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (nautilus:4252): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: unknown format for key 'share/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only
Segmentation fault

```

---

### Post by Peter09 on 2009-04-23
Well there is a bug report open for this

[https://bugs.launchpad.net/ubuntu/+source/nautilus-open-terminal/+bug/315874](https://bugs.launchpad.net/ubuntu/+source/nautilus-open-terminal/+bug/315874)

---

### Post by meeples on 2009-04-23
does anyone know of a way to force burn a cd? if thats even possible lol

i really want to do this clean install...

thanks :)

---

### Post by meeples on 2009-04-23
i think ive found a way to write this cd :D

i downloaded K3b from the repository, it seems to be made for KDE but its burning the cd at the moment so fingers crossed!

i assume this is working because it isn't using nautilus in any way?

very happy. :):lolflag:

---

