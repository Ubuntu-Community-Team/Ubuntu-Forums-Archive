---
title: "Dell Inspiron 1501 problem installing Ubuntu 11.04"
date: 2011-09-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Chough39 on 2011-09-26
I have installed from CD's the downloaded versions on two computers following the MD5 Sum check of Ubuntu 9.10, 10.10 and 11.04. There were no problems. However with a Dell Inspiron 1501 only the 9.10 installed with no problem. The 10.10 and 11.04 CD's failed to work and a dreaded vertical striped grey screen was all that arrived. As I wish a clean install of 11.04 can someone provide a solution please.

---

### Post by ninjaaron on 2011-09-27
It's not exactly clear what the problem is from your post, but you could try reburning the disk.  You could also try following the instructions on the install page for a live USB instead of a CD.  I do all my installs with a live USB, as it generally tends to go smoother than with optical media.

Let us know.

---

### Post by Toz on 2011-09-27
You need to use the **nomodeset** kernel parameter. See: [http://ubuntuforums.org/showthread.php?t=1839957&highlight=Inspiron+1501]("http://ubuntuforums.org/showthread.php?t=1839957&highlight=Inspiron+1501").

---

### Post by Chough39 on 2011-09-28
I have downloaded 11.04 again and installed on a USB following a MD5SUM check. On booting and pressing F6 I changed to &#8220;nomodeset&#8221; . The USB version of Natty Narwhal now works perfectly. The USB version I agree works smoothly, though why it was only with this computer that the problem arose I do not know.
 Many thanks to those who have provided such useful information.

---

