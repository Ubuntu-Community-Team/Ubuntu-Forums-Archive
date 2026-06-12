---
title: "I killed windows bootloader"
date: 2009-03-12
forum: General Help
---

### Post by Ze MoreiRa on 2009-03-12
Don't ask me how, **** happens. there is no more "boot" folder on Vista partition. so it won't load.
Good news is that kubuntu is still running
Now I need to restore bootloader, but have no idea how to do it
Any help would be appreciated ...

---

### Post by phinullfermata on 2009-03-12
If you have a Vista CD, putting it in the computer and running it in recovery, selecting the restore MBR (Master Boot Record) or something like that should do it.  I don't have experience with Vista but I remember reading something similar to that.

---

### Post by cespinal on 2009-03-12
yup...I remember a similiar time where my solution was to back up all my daya in ubuntu...run the live cd... and wipe vista off my hardrive once and for all...

---

### Post by Aaric on 2009-03-26
Go to terminal from kubuntu and type :

&#8220;sudo gedit /boot/grub/menu.lst&#8221;

A large text file will open and at the bottom leave a line and add this:

title	 Vista (Loader)
root	 (hd0,1)
savedefault
makeactive
chainloader	+1

(Do not type this line but if that does not work on re-boot try &#8220;hdo,0 or hd0,2&#8221; and so on until it works.)


I'm not 100% sure this will work, but try it and see. If it doesn't you are just back where you started, so there's no loss. Let me know if it works.:)

---

### Post by SuperSonic4 on 2009-03-26
> **Aaric said:**
> Go to terminal from kubuntu and type :

“sudo gedit /boot/grub/menu.lst”

A large text file will open and at the bottom leave a line and add this:

title	 Vista (Loader)
**root	 (hd0,1)**
savedefault
makeactive
chainloader	+1

(Do not type this line but if that does not work on re-boot try “hdo,0 or hd0,2” and so on until it works.)


I'm not 100% sure this will work, but try it and see. If it doesn't you are just back where you started, so there's no loss. Let me know if it works.:)

You can edit the entry direct from grub too so you don't have to boot into kubuntu each time. Press e to edit and then make your change and press b to boot (grub tells you what to do)

In the bit I've bolded in the quote is the hdd/parition that vista is in. Grub starts with 0 and is in the form (hdX,X) so the first partition on the second hdd is (hd1,0)

---

