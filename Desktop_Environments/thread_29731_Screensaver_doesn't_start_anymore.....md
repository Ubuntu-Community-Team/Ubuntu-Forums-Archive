---
title: "Screensaver doesn't start anymore...."
date: 2005-04-25
forum: Desktop Environments
---

### Post by mirtux on 2005-04-25
Hi,
   i've some problems with the screensaver. It works testing it under the Kcontrol panel, and set it up to start after 5 minutes of inactivity. But when the time has passed nothing happen and the screensaver does not start. Also the lock screen button does not work.

Any ideas?

Thanks in advance,
MC

---

### Post by chalker on 2005-04-25
I'm actually having the same problem.  I'm "thinking" it might be related to mplayer because I use the --stop-xscreensaver option, but even when I turn off and on the screensaver again it will never start up unless I reboot.  Is anyone else having this problem??

---

### Post by mirtux on 2005-04-26
If it is of any help i don't have mplayer so in my case it should not  be related to that.... :???:

Regards,
MC

---

### Post by mirtux on 2005-04-27
Hi,
  i've read from a debian list that it is caused by **kdebluetooth** module. I've purged it and then reinstalled and all things went smoothly...

Regards,
MC

---

### Post by troywill1 on 2005-04-27
I don't use the KDE screensaver because in my experience it has been unreliable at best.  I disable the KDE screensaver and use only Xscreensaver.  

For background look here: [http://www.jwz.org/xscreensaver/faq.html#kde](http://www.jwz.org/xscreensaver/faq.html#kde)
For instructions look here: [http://www.jwz.org/xscreensaver/man1.html#10](http://www.jwz.org/xscreensaver/man1.html#10)

This works like a charm and I have used it for a long time on numerous KDE installations.

Troy

---

### Post by dhuff on 2005-04-27
I second Troy's suggestion. xscreensaver is much superior to the KDE screensaver.

---

