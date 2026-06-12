---
title: "Need help removing ubuntu after error"
date: 2009-02-19
forum: General Help
---

### Post by jimmy666 on 2009-02-19
OK so i have the latest ubuntu installed, intrepid ibex i believe, and its NOT a dual machine, my laptop solely has linux. not xp or anything else, installed using a full partition for linux.

i have a boot disc with window xp sp2 and when it goes through its small initial install it gives me a terminal screen that says theres an error. do i need to format this thing all together to get the boot to work or what? im missing something...any ideas???:(

---

### Post by Mercury_Alpha on 2009-02-19
Can you be more specific about where the error occurs, and what the error is?

---

### Post by solwic on 2009-02-19
> **jimmy666 said:**
> OK so i have the latest ubuntu installed, intrepid ibex i believe, and its NOT a dual machine, my laptop solely has linux. not xp or anything else, installed using a full partition for linux.

i have a boot disc with window xp sp2 and when it goes through its small initial install it gives me a terminal screen that says theres an error. do i need to format this thing all together to get the boot to work or what? im missing something...any ideas???:(

If you have the whole XP disc, just pop it in and reboot.  Otherwise, try running a LiveCD and using gparted to format, then run your recovery disk.  

Without more specifics, that's all I can really say.

---

### Post by jimmy666 on 2009-02-19
basically it tries to install the windows xp and once it goes through to another stage in the windows loader screen it says there has been an error and needs to quit.

then gives error code:

0x0000007b
0xf78d2524
0xc0000034
0x00000000
0x00000000

---

### Post by Mercury_Alpha on 2009-02-19
Ah yeah, if it's a recovery disk, that relies on keeping a semi-hidden partition which contains the rest of the files you'd need to restore Windows. Recovery disks can't restore Windows without that data. If that partition was deleted, it's not looking good.

Providing recovery disks instead of proper install disks is a common cost-cutting measure for many computer makers. In fact, I think you have to explicitly ask for the actual Windows CDs when your order is put together.

---

### Post by BrillianceLin on 2009-02-19
If I do not interperted it wrong, you want to put the XP on your machine, right? I think you can tried virtual machine and put the XP on. Then you can(have to) run both os at the same time. I do not know how to put the XP on after you install Unbuntu. But what I did to switch back to dual OS was find a low level format sofeware(cd/floppy). Format the hard drive, and put on the XP 1st, then install linux second. Be aware when you are assigning partition to XP, make sure you will leave sapce(as the size you want) for you linux. Otherwise, some ugly thing may happen. The formating tool build in XP can not do the low level formating, so it will not format linux partition. I hope this reply can provide you some help.

---

### Post by BrillianceLin on 2009-02-19
Er, I am not sure he format that section of the harddrive. Cause by default setting, linux partitioner will(can?) not touch that area, at least in my case it did not. And I read from some other forum said you have to reconfig some thing in your bios setup to let those section being accesable for partitioner. But thanks for bring up the point.

---

### Post by jimmy666 on 2009-02-19
yeah basically*i burned an iso of a Windows XP SP2 ed onto a disk and i guess when it tries to load it craps out. 

so im gathering that its going to be hard to go from entirely Ubuntu back to entirely xp?

---

### Post by jimmy666 on 2009-02-21
so any ideas?

---

