---
title: "Windows boot manager"
date: 2009-04-08
forum: General Help
---

### Post by Chamillionaire2 on 2009-04-08
Whats up?

OK, So after getting rid of windows months ago, i got stuck with the windows boot manager coming up, so its a pain to keep entering ubuntu. how would i go about making it automatically goto ubuntu?

Thanks Bye.

---

### Post by Tralce on 2009-04-08
Do you mean to say that you are seeing a Windows boot menu, or that you are seeing a GRUB menu windows as the default option?

If the former, perhaps:
```
sudo grub-install /dev/sda
```
where /dev/sda is the name of the hard drive you're booting from.

If the latter, perhaps:
```
sudo update-grub
```

---

### Post by jelle_ on 2009-04-08
i know two solutions for this.
1. configure the windows boot.ini
the windows boot manager keeps his information in an file at the windows c-drive called boot.ini. it is hidden, but you can open it in an text editor. change the default os to ubuntu and make timeout 0

using this solution, you don't have to change bootloader, but if you remove the windows partition, you cannot boot anymore

2. you can also install grub on your computer. there are several ways to install it from ubuntu. most use command line or reinstall ubuntu from the cd. kgrubeditor, found in add/remove programs, can also install grub.

---

### Post by WRDN on 2009-04-08
I would install GRUB personally. See [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") for a guide on installing it from the Ubuntu LiveCD.

---

