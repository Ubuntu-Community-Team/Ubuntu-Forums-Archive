---
title: "Change Boot Sequence In Dual Boot Set Up"
date: 2009-06-15
forum: General Help
---

### Post by james.brantley on 2009-06-15
[SIZE=2]Hello all, I was wondering if someone could assist me with changing my boot sequence. I have a dual boot with Vista and it is listed first. I would like Ubuntu to be the default OS not Vista. I have searched the archives and for some reason was unable to find anything on it. I was able to increase the length of time to choose what OS to boot into but not the actual sequence.   Sorry if I just overlooked it![/SIZE]

---

### Post by synapsys on 2009-06-15
Depends on which boot loader you are using.... Vista (longhorn) or Ubuntu (grub)

---

### Post by skyjacker on 2009-06-15
> **james.brantley said:**
> [SIZE=2]Hello all, I was wondering if someone could assist me with changing my boot sequence. I have a dual boot with Vista and it is listed first. I would like Ubuntu to be the default OS not Vista. I have searched the archives and for some reason was unable to find anything on it. I was able to increase the length of time to choose what OS to boot into but not the actual sequence.   Sorry if I just overlooked it![/SIZE] See this link, I think it will help you.[HTML]http://ubuntuforums.org/showthread.php?t=1165995&highlight=boot+sequence[/HTML]

---

### Post by james.brantley on 2009-06-15
[SIZE=2]Could you provide me with the procedure for grub please?[/SIZE]

---

### Post by james.brantley on 2009-06-15
> **skyjacker said:**
> See this link, I think it will help you.[html]http://ubuntuforums.org/showthread.php?t=1165995&highlight=boot+sequence[/html]

[SIZE=2]Thank You![/SIZE]

---

### Post by skyjacker on 2009-06-15
No Problem, a lot can be learned from this forum, if you just ask!!!

---

### Post by jmszr on 2009-06-15
jamses.brantley,

I think this link will be of some help: [http://mathijs.jurresip.nl/2007/09/25/how-to-change-boot-order-of-ubuntu-and-windows/](http://mathijs.jurresip.nl/2007/09/25/how-to-change-boot-order-of-ubuntu-and-windows/) . They are having Windows be the default rather than Ubuntu but the mechanics are the same for what you want.

---

### Post by itix on 2009-06-15
If you have GRUB as bootloader (i.e. if you installed ubuntu after windows), you can type [COLOR="Navy"]gksudo gedit /boot/grub/menu.lst[/COLOR] and change the default entry to whatever OS you want to be the default selection.

If you have longhorn, I really have no f-in idea ;)
Haven't used windows for over 2 years and I haven't used vista at all.

---

