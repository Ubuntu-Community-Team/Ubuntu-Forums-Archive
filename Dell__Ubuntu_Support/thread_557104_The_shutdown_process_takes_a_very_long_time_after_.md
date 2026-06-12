---
title: "The shutdown process takes a very long time after I ran &quot;dpkg-reconfigure --all&quot;"
date: 2007-09-22
forum: Dell  Ubuntu Support
---

### Post by JangMunho on 2007-09-22
To make the tg3-dkms driver work, I ran "dpkg-reconfigure --all".
It took a long time to reconfigure all of the packages, and the tg3 driver works after this action, but new problem came. The shutdown process seems to have some problems now, because it takes a very long time.

Previously, I modified the "sleep" value in /etc/init.d/halt from 0 to 5. The system shut down 5 seconds after the hard disk power off, but now, I modified the value back to 0, the laptop still takes a very long time after the hard disk power off.

There is no error logs either in the syslog or in the user log. I don't know where the problem is.

Please help me!!! What can do?

---

### Post by neptho on 2007-09-23
When shutting down, press Alt-F7 after X logs out, or Ctrl-Alt-F7 while still in X.  You should be able to see what it's 'held up on' as it slowly turns things off.

---

