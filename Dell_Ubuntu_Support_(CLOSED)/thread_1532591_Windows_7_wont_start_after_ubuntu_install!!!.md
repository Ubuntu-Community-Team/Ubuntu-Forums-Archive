---
title: "Windows 7 wont start after ubuntu install!!!"
date: 2010-07-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zeddicus11 on 2010-07-16
Hi, I've just installed ubuntu 10.4, all was fine until I restarted and clicked the windows loader, my computer just crashes and does nothing, what do I do?

All I've done is followed ubuntus install instructions.

---

### Post by zyysql on 2010-07-17
You can use your liveCD to recovery you GRUB
open a terminal
input:
sudo grub
find /boot/grub/stage1
root (hd0,x)
setup(hd0)
quit
sudo reboot

good luck!

---

### Post by zeddicus11 on 2010-07-17
It didn't work, I got this error "sudo: grub: command not found"

Thanks for your help.

---

### Post by Mthbk1 on 2010-07-17
I've installed ubuntu 10.04 'inside windows' with wubi installer. Try it

---

### Post by ST3ALTHPSYCH0 on 2010-07-17
Try booting with your Win7 disc and choose "fix Windows boot".
Next, you'll have to reinstall Grub from a live CD.
I'm guessing that you resized your windows partition with Gparted, and, not knowing, left the "round to cylinders" box checked. A Win7 disc should chkdsk your windows partition.... BTW, this process may take several hours. You might also try resizing your Windows partition to just a little smaller, and uncheck the above mentioned box.

---

