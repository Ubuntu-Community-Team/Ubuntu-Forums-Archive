---
title: "Accidentally changed permissions in /media, does it matter?"
date: 2006-03-11
forum: Desktop Environments
---

### Post by cowlip on 2006-03-11
Hi, I was trying to change the permissions of one device and by accident changed everything in media with "chown owner:owner *" (I am owner).

Do I have to reinstall or anything?

Thanks for the help

---

### Post by amohanty on 2006-03-11
Did you do that via sudo, ie sudo chown ...?

AM

---

### Post by cowlip on 2006-03-11
Yes unfortunately ;(

---

### Post by taurus on 2006-03-11
Why don't you change it back if you remember how you did it the first place.  No need to re-install anything...

---

### Post by amohanty on 2006-03-12
IF you didnt do somethign like (recursive change):
> sudo chown **-R** owner:owner *

that means only your top level folder ownership has changed, so use taurus' suggestion and chang eit back to root:root


HTH
AM

---

