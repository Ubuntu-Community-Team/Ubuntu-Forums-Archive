---
title: "Ubuntu wants to get rid of mbr on update"
date: 2009-05-10
forum: General Help
---

### Post by mikeeeman on 2009-05-10
I'm have a little problem - when I try to install updates, or if I use the "sudo apt-get -f install" command in terminal, I am told that mbr will be removed. I am running Ubuntu 8.10 Intrepid with Wubi alongside Vista. Now, I am afraid that if I allow it to remove this, it will be removing my master boot record and make my entire system unbootable. At this point, I am unsure of what to do. Any help is appreciated!

---

### Post by mikeeeman on 2009-05-10
Please can anyone help?

---

### Post by pastalavista on 2009-05-10
I don't know anything about Wubi installs but I do know the MBR gets changed in order to dual-boot. Have you restarted lately?

---

### Post by Brandon Williams on 2009-05-10
The mbr package provides a program called install-mbr, which installs the mbr bootloader to the master boot record of your drive. Removing this package does not do anything to the actual MBR on your disk ... it just removes install-mbr and associated documentation. You don't need to worry about removing it. If you ever need it again, you can just reinstall.

---

