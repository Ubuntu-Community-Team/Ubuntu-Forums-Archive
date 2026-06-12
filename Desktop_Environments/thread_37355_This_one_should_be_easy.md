---
title: "This one should be easy"
date: 2005-05-26
forum: Desktop Environments
---

### Post by jlv on 2005-05-26
I bought a new printer/scanner (epson rx620) and am trying to get it running.  So far printing works fine (as much as I've tested).  However, I'm not able to use the scanner  from my user account.  I can become root and run scanimage, xsane or kooka and it works fine, so presumably this just a permissions problem... Anyone have any idea of what to check and where.

Thanks,

John

---

### Post by netrattler on 2005-05-26
If you click on System -> Administration -> Users and Groups -> select your username -> click on Properties -> Select user privileges -> make sure "use scanner devices" is checked. Hope this helps.

Joe

---

### Post by jlv on 2005-05-26
Sorry, I don't have those options.  Closest I seem to have in KDE is system->kuser, and I'm a member of goup 'scanner'.  Hmm, I added myself to group 'saned' with no obvious effect.

but thanks,

John

---

### Post by jlv on 2005-05-27
Some more digging shows that if chmod 666 /proc/bus/usb/00x/00y (where 00x & 00y are the values returned by sane-find-scanner.  There is a file /etc/hotplug/usb/libusbscanner that supposedly chowns the above to root:scanner, however mine is being set to root:root after turning the scanner off and on -- It doesn't actually appear that this file is run when the scanner is started or plugged in.

Ideas?

John

---

