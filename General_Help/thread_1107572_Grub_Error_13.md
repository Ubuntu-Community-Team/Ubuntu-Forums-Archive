---
title: "Grub Error 13"
date: 2009-03-26
forum: General Help
---

### Post by Tiger658 on 2009-03-26
I just rebooted and got a grub error 13, I don't know what to do I have looked all over the place and can't find anything. I need to finish my essay tonight, can anyone help?

Ryan

---

### Post by Mud.Knee.Havoc on 2009-03-26
Basically, Windows wants to be on the first physical drive, but the link above will give you some ways around it.

Don't forget to back up your menu.lst before playing around with it.

---

### Post by Tiger658 on 2009-03-26
I tried that, and I couldn't find anything that was helpful. I have Vista on a SATA drive and Ubuntu on a ide. could that be causing a problem?

Ryan

---

### Post by meierfra. on 2009-03-27
Do you get grub error 13 when you pick Vista at the Grub menu?

Boot into Ubuntu (or, if you can't, the Ubuntu Live CD), open a terminal (Applications->Accessories->Terminal) and post the output of

```
sudo fdisk -lu
```

---

