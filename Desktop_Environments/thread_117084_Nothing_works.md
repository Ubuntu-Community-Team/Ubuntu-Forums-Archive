---
title: "Nothing works"
date: 2006-01-14
forum: Desktop Environments
---

### Post by Rasymas on 2006-01-14
I'm completely at a loss. command "su" doesn't work, it says autentication failure, even if i enter the corect pass, nothing work in system/administration tab. Any solutions

---

### Post by GeneralZod on 2006-01-14
Ubuntu uses "sudo", not "su" :

[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---

### Post by Rasymas on 2006-01-14
Please don't post any links for wiki, cuz noobs can't find anything there! Anyway, not even sudo work! But thanks anyway. Here's what happens, I pres System/Administration/Synaptic... and nothing pops up, like pass promting window, the same situation is with everything in adminsitration tab :S

also, it doesn't open Updates list, I can't install them, halp would be valuable :)

---

### Post by aysiu on 2006-01-14
[QUOTE=Rasymas]Please don't post any links for wiki, cuz noobs can't find anything there![/QUOTE] I agree that the Wiki is a mess to navigate, but that's why people post *links* to the Wiki. How would you find that page otherwise?

---

### Post by Mustard on 2006-01-14
I would suspect that your user doesn't have super-user privileges and that you need to edit the /etc/sudoers file from a root prompt using the visudo command.

Did you use expert install when you installed last?

---

