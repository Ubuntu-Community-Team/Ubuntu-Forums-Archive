---
title: "Text login"
date: 2006-03-04
forum: Desktop Environments
---

### Post by Azguz Bloodfist on 2006-03-04
Hi, I'm running kubuntu breezy and would like a text based login, and then start X after I've logged in if I want to.

I realize I have to edit /etc/inittab. The current runlevel is 2, so I would like to know the value to change it to.

I managed to do this on Fedora Core, but I wanted to make sure it was the same procedure. 

Thanks

---

### Post by chronusdark on 2006-03-04
you dont have to edit inittab i think you just have to add the runlevel you would like to the end of your grub boot string the one where you select your kernel

---

### Post by Xian on 2006-03-04
[QUOTE=Azguz Bloodfist]Hi, I'm running kubuntu breezy and would like a text based login, and then start X after I've logged in if I want to.[/QUOTE]

For kdm (Kubuntu)
$ sudo update-rc.d -f kdm remove

For gdm (Ubuntu)
$ sudo update-rc.d -f gdm remove

Edit: per incubus clarification.

---

### Post by incubus on 2006-03-04
Actually, "kdm", since you're running Kubuntu.

incubus

---

### Post by Azguz Bloodfist on 2006-03-05
[QUOTE=Xian]For kdm (Kubuntu)
$ sudo update-rc.d -f kdm remove
[/QUOTE]

Thanks. Do you also know the command to change it back, just incase?

---

### Post by incubus on 2006-03-05
Yep, it's in here:
$ man update-rc.d

For most purposes (including this one) it will be "defaults" instead of "remove".

incubus

---

