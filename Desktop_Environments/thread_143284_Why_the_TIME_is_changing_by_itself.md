---
title: "Why the TIME is changing by itself?"
date: 2006-03-12
forum: Desktop Environments
---

### Post by pmilin@ptt.yu on 2006-03-12
Hi!
When I log in Breezy, from time to time, the TIME (and sometimes even the DATE) is changed. I suppose that this could be related to some conflict with Windows, since I have dual boot, but don't know what and why. Also, I remember vaguely that I had same problem in Hoary, and that I managed to fix it, but now I cannot.
I have de-checked UTC and made CET: Europe/Belgrade, which is, again, constantly automatically changed to Europe/Sarajevo. Hence, beside the fact that the time-zone is changed from Belgrade to Sarajevo (which is benign being the fact that it is the very same time-zone), the TIME it self is changing, make smaller or rather huge jumps.
Can anyone help me with this issue?

---

### Post by Xian on 2006-03-12
Did you set 'UTC=no' in /etc/default/rcS ??

---

### Post by pmilin@ptt.yu on 2006-03-12
But of course! As I said: time is set to CET, and UTC=no.

Sincerely,
P.

---

### Post by Xian on 2006-03-12
You said that you "de-checked UTC" which could mean various things. 

I would at this point install rdate and sync that with a time server either at boot via a script, or as a session command when you enter your desktop environment. It is an easy way set your system to the correct time.

---

### Post by pmilin@ptt.yu on 2006-03-12
Sorry, I wasn't precise, you are right. Nevertheless, I cannot find rdate in Ubuntu repositories. Can I find it in Debian's?

P.

---

### Post by Xian on 2006-03-12
You just need to enable the Universe repos, or you can download the file directly from a mirror: [rdate_1.4-6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/r/rdate/rdate_1.4-6_i386.deb). It only depends upon libc6, which obviously you will already have installed on your system.

---

