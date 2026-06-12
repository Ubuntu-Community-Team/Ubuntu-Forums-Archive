---
title: "Ubuntu overwrote the MBR entry of my own Grub located on another partition."
date: 2009-04-26
forum: General Help
---

### Post by sirbender on 2009-04-26
Hi,

I have ONE harddisk, which is always booted first in the bios and which has after installing Ubuntu the following partitions: [http://img204.imagevenue.com/img.php?image=56849_gparted_122_496lo.jpg&loc=loc496](http://img204.imagevenue.com/img.php?image=56849_gparted_122_496lo.jpg&loc=loc496)

sda1 and 2 are Vista. sda3 is Ubuntu. sda7 is my Grub partition. The rest are data partitions.

The Grub on my Grub-partition (installed in the MBR) was used to boot all OSs on my harddisk. Now that I installed Ubuntu from the Live-CD it put its own Grub into the MBR (replacing mine). Here is Ubuntu's Grub menu.lst file:

```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a8eb48c8-a85f-4879-a2fa-8b85768f804a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a8eb48c8-a85f-4879-a2fa-8b85768f804a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1

```
What I did: I took these menu.lst entries from Ubuntu and put them in my own Grub menu.lst on the Grub-partition. Next, I wrote my own Grub to the MBR (setup (hd0)).

I am pretty good at Grub, so I normally know what I am doing. So I rebooted and my own Grub started - showing me the entries I just added to menu.lst.


Windows Vista did boot as usual, but Ubuntu did not :(((

I tried to modify the Ubuntu-menu.lst entry (removing uuid and replacing it with root (hd0,2) etc.) but nothing worked. I used all possible and impossible combinations but it did not work out.

I noticed that in the Grub console I only find /boot/grub/stage1 from my own Grub partition and not Ubuntu's one. Perhaps this means that the Ubuntu partition is not mounted, which I guess it should be at this point, right?


Anyway I restored Ubuntu's Grub in the MBR again and booting Ubuntu works again now.

Still - in the long run I need to use my own Grub partition. Please tell me what I need to do to make this happen?

Cheers,
sb

---

### Post by meierfra. on 2009-04-28
What error message do you get?  It sounds like that  the grub on your grub partition cannot handle the newer  256bs/inode ext3 file system used  by Ubuntu 9.04 and higher.

Two solutions:

1)  Copy all the stage files from the Ubuntu partition to the Grub partition and reinstall grub to the MBR.

2)  Install the Ubuntu grub to the boot sector of the Ubuntu partition and  chainload Ubuntu with

title Ubuntu
uuid   a8eb48c8-a85f-4879-a2fa-8b85768f804a
chainloader +1


Let me know if you need more detailed instructions.

---

### Post by sirbender on 2009-04-30
> **meierfra. said:**
> What error message do you get?  It sounds like that  the grub on your grub partition cannot handle the newer  256bs/inode ext3 file system used  by Ubuntu 9.04 and higher.

Two solutions:

1)  Copy all the stage files from the Ubuntu partition to the Grub partition and reinstall grub to the MBR.

2)  Install the Ubuntu grub to the boot sector of the Ubuntu partition and  chainload Ubuntu with

title Ubuntu
uuid   a8eb48c8-a85f-4879-a2fa-8b85768f804a
chainloader +1


Let me know if you need more detailed instructions.

Boot sector of the Ubuntu partition? How do I do that? Something like:

root(hd0,2)
setup(hd0,2)

But then Grub in the MBR will call Grub in the Ubuntu PBR. So I see two Grub menus. Why can't I directly use the root and kernel commands to start Ubuntu? That's how it is normally done.
I doubt it doesn't understand the new ext3. But I will recheck it.

thanks!!!

---

### Post by meierfra. on 2009-04-30
> Boot sector of the Ubuntu partition? How do I do that? Something like:

root(hd0,2)
setup(hd0,2)

yes.


> But then Grub in the MBR will call Grub in the Ubuntu PBR. So I see two Grub menus. 

if you use "hiddenmenu" and "timemout 2" you will  hardly notice the second grub menu. This method has the advantage that you will not have to edit the "menu.lst" on your grub partition after kernel updates. 

> I doubt it doesn't understand the new ext3. 
If neither 1) nor 2) fixes your problem we will have to have a closer look at your system.

---

### Post by sirbender on 2009-04-30
> **meierfra. said:**
> yes.




if you use "hiddenmenu" and "timemout 2" you will  hardly notice the second grub menu. This method has the advantage that you will not have to edit the "menu.lst" on your grub partition after kernel updates. 


If neither 1) nor 2) fixes your problem we will have to have a closer look at your system.



Hehe :)
Actually it was a problem with old stage files :)
It just wasn't able to mount/read the Ubuntu partition in ext3. Copying Ubuntu's stage files over solved it :)

Now all I need is getting rid of this stupid Vista boot menu. It still has 2 entries - also a Windows7 entry that doesn't work anymore since Ubuntu is now on that partition.

Thanks!!!

---

### Post by meierfra. on 2009-04-30
> Now all I need is getting rid of this stupid Vista boot menu. It still has 2 entries - also a Windows7 entry that doesn't work anymore since Ubuntu is now on that partition.

Do you have two different Vista you would like to boot or just one?

Just let me know, and I can show you how to get rid of the Vista boot menu.

---

### Post by sirbender on 2009-05-01
> **meierfra. said:**
> Do you have two different Vista you would like to boot or just one?

Just let me know, and I can show you how to get rid of the Vista boot menu.


I just have one. Got rid of the bootmenu by using bootrec and bcdedit. Do you have a solution for this problem that involves only Linux?

---

### Post by meierfra. on 2009-05-01
> Do you have a solution for this problem that involves only Linux? 

No. You need to edit the bcd and as far as I know there is no way to do that from Linux. This would have been my solution:

Boot into Vista. Go to "Start". Type "cmd" and press "Ctrl+Shift+Enter". This will open the Vista  commandline as an administrator. Type

```
  
bcdedit /set {bootmgr} default {current}
bcdedit /set {bootmgr} timeout 0

```

---

