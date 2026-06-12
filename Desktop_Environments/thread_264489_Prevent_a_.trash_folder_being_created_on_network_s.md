---
title: "Prevent a .trash folder being created on network share?"
date: 2006-09-24
forum: Desktop Environments
---

### Post by Jose Catre-Vandis on 2006-09-24
I have a network folder that I share on the net, using a php script as a web interface. I access and load and delete files remotely via NFS across my LAN.

A .trash folder gets created which then borks the php script

Is there a way to prevent .trash from being created, or to at least delete to trash in another location?

---

### Post by kidders on 2006-09-24
Hi there,

Files are really only trashed if you trash them on purpose (as opposed to deleting them). Perhaps you could just avoid trashing files on that volume. (I know that's a kinda dumb suggestion, but it's straightforward!)

How come your PHP script finds the directory so confusing?

---

### Post by Jose Catre-Vandis on 2006-09-28
> **kidders said:**
> Hi there,

Files are really only trashed if you trash them on purpose (as opposed to deleting them). Perhaps you could just avoid trashing files on that volume. (I know that's a kinda dumb suggestion, but it's straightforward!)

I do try to "really" delete, but somehow the .trash folders pop up anyway :D

> How come your PHP script finds the directory so confusing?

Dunno, doesn't like .trash, nor anything less than 755 on file/folder permissions (probably written for a Windows share :lol:)

---

### Post by kidders on 2006-09-29
What an odd problem! The main reason I asked about your PHP script is that there may be an easy way to alter it to behave itself. I can take a look if you'd like me to.

I'm not sure how to stop .trash from being created in the first place, but you *could* periodically delete it, perhaps. One possible hack might be to use cron to do a **if [ -e /path/to/.trash ]; then rm -Rf /path/to/.trash; fi** every 5 minutes, say, or maybe a **find /mnt/wherever -name .trash -exec -Rf rm {} \;**.

The most desirable solution would be to fix the broken PHP script, since it seems unreasonable that it should moan about something as straightforward as a directory. It seems downright silly to give up your trashcan for the sake of a badly-written PHP script!

---

### Post by robinlennox on 2007-09-15
Does anyone have a better solution for preventing a trash folder being created on a network share?

---

### Post by Jose Catre-Vandis on 2007-10-01
or on a mobile phone microSD card, which then "trashes" the microSD card and borks the USB ports when i try to disconnect the phone (properly by right click eject/unmount volume)

---

