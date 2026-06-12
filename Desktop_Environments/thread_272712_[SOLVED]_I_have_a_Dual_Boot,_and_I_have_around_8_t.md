---
title: "[SOLVED] I have a Dual Boot, and I have around 8 things to choose from."
date: 2006-10-06
forum: Desktop Environments
---

### Post by RonB123123 on 2006-10-06
I have a Dual Boot, and I have around 8 things to choose from. Is there a way to make it say Ubuntu or Windows? And I could just select one of those instead of 1 of 8.

My list looks something like this...

Ubuntu Linux
Ubuntu Linux Recovery
Ubuntu Linux
Ubuntu Linux Recovery
Ubuntu Linux
Ubuntu Linux Recovery
Windows XP

I just want it to say

Windows XP
Windows XP Safe Mode
Ubuntu Linux
Ubuntu Linux Recovery

Is there a way to do this? Thank you.

---

### Post by lemonsCC on 2006-10-06
You may want to look at this.  Its graphical and gets rid of the extras.

[http://www.hezardastan.org/breezy_xp_dualboot/en/gaginstall.html#gagbootmanager]("http://www.hezardastan.org/breezy_xp_dualboot/en/gaginstall.html#gagbootmanager")

---

### Post by Omnios on 2006-10-06
The other entries are either Linux installes or past versions of the kernel. You can try uninstalling the past kernels which what I have done before and the dissapeared. As for the other stuff you will have to read up on grub as there is ways of manually modding the grub file to make xp the default launch etc.

---

### Post by bruenig on 2006-10-06
```
gksudo gedit /boot/grub/menu.lst
```
once in there put a # in front of any entry that you don't want in the menu. And you can change the names of the ones you do want to keep too.

If you would paste your /boot/grub/menu.lst file in this thread, I could edit it for you and repaste the one you should use for your purpose, assuming you don't understand completely what I am saying.

---

### Post by RonB123123 on 2006-10-07
I followed bruening's instructions. Thank you very much. It worked really well, and I was able to move Windows XP up to be the first choice. 

I'm still making the transitition from Windows to Linux (Almost there). :)

---

