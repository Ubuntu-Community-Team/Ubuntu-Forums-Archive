---
title: "Can't Install Ubuntu 8."
date: 2009-02-18
forum: General Help
---

### Post by psychtor on 2009-02-18
I can&#8217;t install the recent Ubuntu 8.

&#8220;Sorry the program ubiquity closed unexpectedly.&#8221;

So I looked at the logs.

The last message listed under Messages is:

&#8220;Unbuntu ubiquity: Fatal Python Error. Inconsistent interned string state.&#8221;

The last message listed under Auth.log is:

&#8220;Ubuntu TTY ; unknown PWD=/home/ubuntu ; user=root ; command=/usr/bin/ubiquity&#8221;

The last two messages listed under Daemon.log is:

1.	&#8220;ubuntu x-session=-manager [6737] : warning: unable to find provider &#8216;gnome-wm&#8217; or required component &#8216;window manager&#8217;&#8221;

2.	&#8220;warning: application &#8216;libcanberra-login-sound.desktop&#8217; failed to register before timeout&#8221;

The last line from debug is:

&#8220;ubuntu ubiquity [7000] ;debconffilter_done : install (current : none)&#8221;

The last line from kern.log is:

&#8220;ubuntu kernel: [640.462624] squashsf error: unable to read inode [2a1fc985 : 15of]&#8221;

Actually there are 52 squashfs errors in a row above this one.

The last two lines from user.log are:

1. &#8220;ubuntu ubiquity [7000]&#8221; runtime error: install failed with exit code 134; see/var/log/syslog

2.	&#8220;ubuntu ubiquity [7000]&#8221; (blank area no message listed)

So I close out the logs window and click on places and get this error:

&#8220;Sorry the program nautilus closed unexpectedly.&#8221;

So I go back to syslog and get this:

&#8220;ubuntu kernel [2133.713922] nautilus [6902] : segfault at 40000004 ip b75f7e86 sp bff6eaeo err 4 in libglib &#8211; 2.0.50.0.1800.2 [b75d4000+b5000]&#8221;

Then a long string of &#8220;recursive core dump detected, aborting&#8221; errors.

So, far be it from me to know what any of all this means.

---

### Post by oldos2er on 2009-02-18
Run 'Check CD for defects' or md5sum the disc: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Therion on 2009-02-18
GAWD how I hate recursive core dumps!!!  ARRRRGH!!

Seriously, reburn your install media.  Burn it sloooow... No faster than 16x for a CD with 8x being my preferred speed unless you're using an *80-wire/40-pin connector cable.




/Seriously people, it's time to get one.

---

### Post by psychtor on 2009-02-20
> **oldos2er said:**
> Run 'Check CD for defects' or md5sum the disc: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The CD checks out as OK when I select that option.

---

### Post by psychtor on 2009-02-20
> **Therion said:**
> GAWD how I hate recursive core dumps!!!  ARRRRGH!!

Seriously, reburn your install media.  Burn it sloooow... No faster than 16x for a CD with 8x being my preferred speed unless you're using an *80-wire/40-pin connector cable.




/Seriously people, it's time to get one.

I can't save files to CD at home since that drive is just a reader and the library here disallows using the CD drives to save files.

The CD for both 7 and the recent 8 was mailed to me from the Netherlands when I requested one on this webpage:

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by psychtor on 2009-02-22
I don't know what speed the disk was made at but the CD drive can read at 32X.

Does anyone know what any of these errors mean?

---

