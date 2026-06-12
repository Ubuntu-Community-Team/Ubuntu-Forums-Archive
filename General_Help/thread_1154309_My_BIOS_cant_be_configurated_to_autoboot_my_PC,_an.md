---
title: "My BIOS cant be configurated to autoboot my PC, any solution through Ubuntu?"
date: 2009-05-09
forum: General Help
---

### Post by tirengarfio on 2009-05-09
Hi,

just that, any idea?

Bye

---

### Post by Alterax on 2009-05-09
I'm not absolutely certain by what you mean by "autoboot."

If by autoboot you mean to turn on from a powered-off state at a certain time, then Ubuntu (or any other OS) really can't help you; when the system is powered down, the operating system is not loaded in memory, so no triggers defined within it can occur.

This is something that should be set within the BIOS.  However, you have already tried that route.  Your next recourse is to find out who built your motherboard and see if there are any firmware updates for your specific board.  Re-flashing the BIOS to a newer version--like I said, be forewarned as they ARE board-specific and one not meant for your board can render it unusable--could provide the timer functions you are missing.

Or have I completely misunderstood what you were asking?  If so, describe what you are wanting in more detail, and I'll see what I can come up with.

---

### Post by Tipped OuT on 2009-05-09
^^^^ If that isn't what you mean, then maybe you mean boot from your CD/DVD drive in order to install Ubuntu? If so, I believe there's some work around with grub that lets you boot from a USB drive (flash stick). Don't quote me on this. :P

EDIT: Have you tried setting your bios to boot from your CD/DVD drive? I don't know, maybe you haven't . Also, you can install Ubuntu inside of Windows with out the need to burn a CD (just mount the ISO with Daemon Tools). Or if you are lazy and don't want to do that, just download Wubi and install Ubuntu inside of Windows like that, it's noob proof. :)

---

### Post by Alterax on 2009-05-09
OK, I'm really confused here...how do flash drives and wubi fit into setting a system to autoboot?

---

### Post by CatKiller on 2009-05-10
If your BIOS doesn't support waking at a particular time then you can't do it directly. As Alterax said, there's nothing else running that could turn it on for you. However, if your motherboard and network card support Wake-On-LAN and you have another computer that's on at that time you could send a command over the network to wake the computer up.

Otherwise, you can't do it, I'm afraid.

---

### Post by tirengarfio on 2009-05-10
> **Alterax said:**
> I'm not absolutely certain by what you mean by "autoboot."

If by autoboot you mean to turn on from a powered-off state at a certain time, 

Yes i meant that. Thanks!

---

