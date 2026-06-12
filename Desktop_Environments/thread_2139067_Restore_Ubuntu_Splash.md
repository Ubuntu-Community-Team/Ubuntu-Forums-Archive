---
title: "Restore Ubuntu Splash"
date: 2013-04-25
forum: Desktop Environments
---

### Post by NoobKing on 2013-04-25
I installed ubuntu 13.04 and i wanted to give kde a try to so i installed kubuntu-desktop. Now my system reads kubuntu in grub and boots with a kubuntu splash screen. Is there a way to get the boot and grub restored back to how it was while keeping KDE on there? Also would KDE-standard cause the same issue?

I tried 

sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

and
sudo apt-get install --reinstall ubuntu-desktop

but no change.

---

