---
title: "Cannot boot into Win 7  Grub legacy &quot;Error 13&quot;"
date: 2013-02-08
forum: Desktop Environments
---

### Post by sankscan on 2013-02-08
Fred,

I installed grub2 by using Synaptic and I can see a new menu.lst and it picked all the kernels installed on my Ubuntu 12.10 m/c. Great! It however did not have an entry for Windows 7 which is on (hd0,0). So, I manually added the Win 7 entry into the menu.lst as shown below. I still see "Error 13".

Do you think I need to install grub on /sda (Windows disk) and boot from that disk for grub to load Windows and Ubuntu without any errors? Please advise.

********************
#title Windows
#root

title		Windows 7 Pro x64
root		(hd0,0)
savedefault
makeactive
chainloader +1

# This is a divider to separate Ubuntu 
# from Windows
*********************

---

### Post by oldfred on 2013-02-08
Moved to a new thread as your boot issues seems different even if same grub error 13.
For reference.
[http://ubuntuforums.org/showthread.php?t=2064591](http://ubuntuforums.org/showthread.php?t=2064591)

We need to see details of your install. If still booting with grub legacy Boot-Repair will not fix it, but it can help you upgrade to grub2 or repair grub2. If just a Windows issue you may need Windows repairCd

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by sankscan on 2013-02-08
Fred,

I manned up and used boot-repair and guess what, it worked like a charm. I have a much cleaner grub and I can dual boot without any issues. boot-repair is pretty neat!

Thanks for the suggestion!

---

### Post by oldfred on 2013-02-08
Glad it worked. :)

Pretty sure you were converted to grub2.

---

