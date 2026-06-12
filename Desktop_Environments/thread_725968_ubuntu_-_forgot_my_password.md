---
title: "ubuntu - forgot my password"
date: 2008-03-16
forum: Desktop Environments
---

### Post by ubuntoexpert on 2008-03-16
forgot user name and password to the ubuntu linux

any way to retrive it?

---

### Post by sisco311 on 2008-03-16
Reboot your computer and select Recovery Mode from the Grub menu.
When the computer first starts up, you have a few seconds to push esc to go into GRUB.

When the command prompt appears, issue the command:
```
ls /home
```This command will print the home folders.(home folder name = user name)

Type:
```
passwd *username*
```to change your password.

```
reboot
```to reboot your computer.

---

### Post by ghost_ryder35 on 2008-03-16
> **sisco311 said:**
> Reboot your computer and select Recovery Mode from the Grub menu.
When the computer first starts up, you have a few seconds to push esc to go into GRUB.

When the command prompt appears, issue the command:
```
ls /home
```This command will print the home folders.(home folder name = user name)

Type:
```
passwd *username*
```to change your password.

```
reboot
```to reboot your computer.
I'm deleting the recovery mode option from my GRUB menu.  Damn that is too easy to take over my PC :(

---

### Post by kellemes on 2008-03-16
> **ghost_ryder35 said:**
> I'm deleting the recovery mode option from my GRUB menu.  Damn that is too easy to take over my PC :(

Like that's going to stop someone to take over your pc ;-)

---

### Post by p_quarles on 2008-03-16
> **ghost_ryder35 said:**
> I'm deleting the recovery mode option from my GRUB menu.  Damn that is too easy to take over my PC :(
I have to agree with kellemes, here. Disabling Recovery mode does nothing but make things more difficult for you should there be any problems. Any Linux live disk will be able to accomplish the same thing.

If you're worried about people with physical access to your system, you need to encrypt your data.

---

