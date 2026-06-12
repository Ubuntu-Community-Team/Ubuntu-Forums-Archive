---
title: "How to on additional Tweaks"
date: 2005-03-24
forum: Desktop Environments
---

### Post by vvu on 2005-03-24
I have used the suggested tweak methods and they work wonders on my machine.  Additional questions on this same line...


(1)  How do you clear the contents of Find Files/Folders?

(2)  How do you clear the contents of the Run Command?

(3)  How do you get every new users desktop to have what you have - look and feel - a default user profile (I tried copying the contents of my /home/myprof/* profile to /etc/skel/  - that did not work.


Thanks again - happy Kubuntu!

---

### Post by Ironi on 2005-03-25
> **vvu]
(1)  How do you clear the contents of Find Files/Folders?

(2)  How do you clear the contents of the Run Command?
[/QUOTE]
There doesn't seem to be an easy way to do so said:**
> 
(3) How do you get every new users desktop to have what you have - look and feel - a default user profile (I tried copying the contents of my /home/myprof/* profile to /etc/skel/ - that did not work.

I'm not 100% certain that these cover everything, but try copying the following from the default user's home dir:
**Folders:** .qt .kde .local .config Desktop .fonts
**Files:** .kderc .fonts.conf

HTH.

---

### Post by vvu on 2005-03-25
Excellent!  Thank you sir for 1 and 2...KDE config files of course!  The default user profile is /etc/skel right?

---

