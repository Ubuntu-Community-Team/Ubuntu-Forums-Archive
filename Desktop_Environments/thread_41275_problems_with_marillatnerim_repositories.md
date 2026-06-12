---
title: "problems with marillat/nerim repositories?"
date: 2005-06-12
forum: Desktop Environments
---

### Post by Bil-E-daKid on 2005-06-12
Hey there fellow Ubuntu users. I've had problems with this the last couple of days and wandered over here:

[http://ftp.nerim.net/debian-marillat/](http://ftp.nerim.net/debian-marillat/)

....to find the reason for my problems.

Turns out the stable/unstable/testing directory names have changed to sarge/sid/etch (respectively).

Update your /etc/apt/sources.list as detailed and everything starts working fine again.

Yaaay!

Thanks for your attention.

---

### Post by RastaMahata on 2005-06-12
marillat repos are famous for breaking stuff in ubuntu... That's why people should use backports extras repos, which have the same packages, if not more. :P

---

### Post by Bil-E-daKid on 2005-06-13
Really? I had no idea! Thanks for that information.

Does that mean I can install things like w32codecs and libdvdcss etc from the backports repos? (ie, can I turn off the marillat/nerim repos completely?).

Thanks
Bil

---

### Post by bored2k on 2005-06-13
[QUOTE=Bil-E-daKid]Really? I had no idea! Thanks for that information.

Does that mean I can install things like w32codecs and libdvdcss etc from the backports repos? (ie, can I turn off the marillat/nerim repos completely?).

Thanks
Bil[/QUOTE]
 yes. if you installed something using marillat, you will need to manually downgrade them to ubp. And, this is not a place to ask questions.

---

