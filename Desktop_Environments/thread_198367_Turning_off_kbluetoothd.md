---
title: "Turning off kbluetoothd"
date: 2006-06-17
forum: Desktop Environments
---

### Post by afx on 2006-06-17
How can I turn off kbluetoothd from loading at startup? I really don't need it.
How can one manage programs/services loading at startup at all?!

---

### Post by caserio on 2006-06-17
Hi,

You can't turn off kbluetoothd. You have te remove the package bluez-utils. I did it, it's OK.

KDE (some) services-> kcontrol
System [services]("http://www.ubuntuforums.org/showthread.php?t=89491")

---

### Post by afx on 2006-06-17
Great! It works for me!
Thanks...

And regarding the second part of the question...
I installed BUM (BootUp-Manager), it's a nice util.
If anyone has an alternative, just say it.

---

### Post by caserio on 2006-06-17
I use sysv-rc-conf

---

