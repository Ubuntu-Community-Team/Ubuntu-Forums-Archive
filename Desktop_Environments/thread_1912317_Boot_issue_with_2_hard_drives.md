---
title: "Boot issue with 2 hard drives"
date: 2012-01-20
forum: Desktop Environments
---

### Post by freee on 2012-01-20
Hi,

I have two 300GB drives. First I installed linux on one drive, then I installed Windows 7 on the other drive thinking it would load the boot manager after windows installation to choose OS. However, boot manager is not loading anymore for some reason. Does anyone know why? Am I missing something here.


Thanks.

---

### Post by oldfred on 2012-01-20
Windows often overwrites the grub2 boot loader in the MBR. Even with two drives it may do that as each system defaults to boot from sda as that is the most common boot. Have you tried booting from the other drive? And if installing Windows after Ubuntu you need to have the os-prober search for other installs by running update-grub.

```
sudo update-grub
```You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. May be better to run the git/beta version of boot script as it has some fixes.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by freee on 2012-01-21
SOLVED! Now grub boot loader is back with nice purple screen.

Thank you I fixed it with Boot Repair image with one click!

---

