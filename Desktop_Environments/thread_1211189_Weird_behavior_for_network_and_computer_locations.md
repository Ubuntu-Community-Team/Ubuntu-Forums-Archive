---
title: "Weird behavior for network and computer locations"
date: 2009-07-12
forum: Desktop Environments
---

### Post by shadysamir on 2009-07-12
When I try to open any network share (samba or other) or try to open computer from places, the file browser window closes and I lose my desktop icons until the next restart. This behavior is new. The network locations actually ask for my username and password but then once it tries to show the files the window closes.

I am able to browse all folders on my hard drive and other local ntfs volumes. But once I try to open from the same file browser a network location the windows closes and desktop icons disappear.

---

### Post by cariboo on 2009-07-12
It would help to know what version you are using, as I had the same problem with Karmic alpha2. A reinstall using the daily build soved the problem. I had several other problems, so a clean install was needed.

---

### Post by shadysamir on 2009-07-12
My version is Jaunty with all the latest updates.

---

### Post by cybil on 2009-07-22
I have the same issue with Jaunty.  It was working fine until an update about two days ago.

---

### Post by shadysamir on 2009-07-22
The issue was resolved on its own on my ubuntu. I am not sure if it's related to any updates.

---

### Post by cybil on 2009-07-22
Plain reboot did not correct the issue, but an update and reboot did the trick.

---

### Post by volkswagner on 2010-01-31
9.04 same exact issue here.  I have tried several reboot's and log out login attempts.

What logs can I check to see if any errors are recorded?

Issue was created perhaps by bad mount/unmount of usb disk.

UPDATE:  Since the problem I can no longer mount my samba share on Linkstation.  I have been using the same command, now it does not work.

```
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

I still get the error using sudo and su to root user.

---

### Post by volkswagner on 2010-02-01
Can't anyone give a hint?

---

### Post by volkswagner on 2010-02-03
Please, can't anyone suggest how to debug this.  Since I am not the only case, this may be a bug?

Even if you don't know how to fix it, perhaps you can point me to what logs shall have relevant info, or hint to what process is broken.  Is it a network, GDM, Nautilus, or what?

EDIT: Well perhaps I have more info to offer.

From /var/log/messages:

When trying to browse <computer>

```
Feb  3 08:46:45 T43 kernel: [  743.371576] nautilus[4118]: segfault at 45797254 ip b77a976b sp bf87fa30 error 4 in libglib-2.0.so.0.2200.3[b774f000+b8000]

```

Whe trying to browse <network>

```
Feb  3 08:50:41 T43 kernel: [  979.609127] nautilus[4325]: segfault at 6e6f6349 ip b781b76b sp bfcfe500 error 4 in libglib-2.0.so.0.2200.3[b77c1000+b8000]

```

Does this indicate a hardware issue?  I am running on an IBM ThinkPad T43.

---

### Post by volkswagner on 2010-02-03
Confirmed bug.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/515336](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/515336)

---

