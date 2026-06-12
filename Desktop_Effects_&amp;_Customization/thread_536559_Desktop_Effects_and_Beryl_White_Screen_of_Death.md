---
title: "Desktop Effects and Beryl White Screen of Death"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by hexon89 on 2007-08-27
I am using a Dell Inspiron 1505/6400 with a Nvidia GeforceGo 7300. When I enable desktop effects or attempt to run Beryl-manager I get the dreaded white screen of death. I have looked for solutions, and found none. Are there any updates to these issues. I cannot enable restricted drivers either, I get the linux-restricted-modules-2.6.20-16-generic not found message.

---

### Post by FuturePilot on 2007-08-27
Do you have all the repos enabled?

---

### Post by st33med on 2007-08-27
Beryl is in Ubuntu's regular repository. You can install from there. Much easier, though, have no idea if it would work well.

PS: Have the same laptop as you and never had that problem. Something wrong with what you downloaded. And, have you considered Compiz Fusion? Little faster, especially with a script or compiling by hand.

---

### Post by st33med on 2007-08-27
> **hexon89 said:**
> I am using a Dell Inspiron 1505/6400 with a Nvidia GeforceGo 7300. When I enable desktop effects or attempt to run Beryl-manager I get the dreaded white screen of death. I have looked for solutions, and found none. Are there any updates to these issues. I cannot enable restricted drivers either, I get the linux-restricted-modules-2.6.20-16-generic not found message.

This could also help:
```
sudo apt-get install linux-restricted-modules-2.6.20-16-generic
```

---

### Post by hexon89 on 2007-08-27
I tried the sudo apt-get install linux-restricted-modules-2.6.20-16-generic command and I got the following error message:

hexon@HEXON:~$ sudo apt-get install linux-restricted-modules-2.6.20-16-generic
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.20-16-generic: Depends: nvidia-kernel-common but it is not going to be installed
  linux-restricted-modules-2.6.20-ck1: Depends: nvidia-kernel-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

