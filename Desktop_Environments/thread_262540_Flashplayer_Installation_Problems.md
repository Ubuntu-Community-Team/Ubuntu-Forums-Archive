---
title: "Flashplayer Installation Problems"
date: 2006-09-21
forum: Desktop Environments
---

### Post by TBone13 on 2006-09-21
when i try to install flashplayer on ubuntu dapper, this is what i get:


```
----------- Install Action Summary -----------

Macromedia Flash Player 7 will be installed in the following directory:

Mozilla installation directory  = /home/USER/.mozilla

Proceed with the installation? (y/n/q): y

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.


Installation complete.


Perform another installation? (y/n): 

```

thanks in advance for any help.

---

### Post by aysiu on 2006-09-21
Looks as if it worked. What's the problem?

---

### Post by TBone13 on 2006-09-21
i seem to not be able to watch some videos that use flashplayer...

and i have no idea why.


also, i get prompted to have it installed often.

---

### Post by srunni on 2006-09-21
"NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser."

Well, if you're the administrator, go ahead and remove it ;)
Do this by renaming the file from xpti.dat to xpti.dat_backup or something like that, so you don't permanently lose it.

---

### Post by TBone13 on 2006-09-21
well see that's the thing.

i've searched for an "xpti.dat" in every mozilla folder i can find.




i cannot find an "xpti.dat" anywhere..............

---

### Post by aysiu on 2006-09-21
Try this: ```
sudo updatedb
locate xpti
``` The first command may take a few minutes.

---

