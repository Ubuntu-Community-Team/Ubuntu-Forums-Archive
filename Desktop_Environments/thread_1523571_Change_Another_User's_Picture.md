---
title: "Change Another User's Picture"
date: 2010-07-03
forum: Desktop Environments
---

### Post by rykel on 2010-07-03
Hi,

Is there a simple way for me (the main user) to change the photo of another user on my system, without logging into that user's account and using his/her "About Me"?

Thanks for advice!

---

### Post by clrg on 2010-07-04
Well, you could try to "sudo -s" to get root access, and then "su - <username>", and then "export DISPLAY=:0" to get graphics working, and then "gnome-about-me", which should bring up the users about me window. Of course, this is only a workaround; by su-minus-ing into his/her account, you actually do log in, but not graphical.

---

