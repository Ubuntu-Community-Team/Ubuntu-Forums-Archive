---
title: "Help is needed with GRUB"
date: 2009-02-20
forum: General Help
---

### Post by nemoneder on 2009-02-20
I am an absolute newbie to Ubuntu Linux.
My PC has dual boot Ubuntu and WinXP.
It was working nicely with two systems. But now there is a problem. 

Previous GRUB page had an option (at the end of the list) "Microsoft Windows XP Professional". Now it is gone. Instead, there is one line "Other operating system". When choosing it (Other operating systems), the screen shows: Error 11: Unrecognized device string.

I checked the menu.lst file, at the end of the file it says the following :

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I have no ideas have to get the WinXP back. Please give me some adveises. Thank you very much in advance.

---

### Post by mcduck on 2009-02-20
Could it simply be that you have so many old kenrels installed that the windows entry doesn't fit on the screen any more (since it clearly is still in your menu.lst file)?

In that case uninstall the old kernels with Synaptic and they will be removed from the Grub menu as well.

---

### Post by nemoneder on 2009-02-20
Thanks for your suggestions. I guess this is not the problem. It was working for a long time. By the way, what exactly I have to do to delete the old kernels. Thanks.

---

### Post by Mercury_Alpha on 2009-02-20
Have you made any changes to your hard drive configuration lately? Added a drive, removed one, changed the cabling, etc?

If you're using a RAID array or SATA drives, that can also complicate things.

Have you successfully booted into Windows after installing Ubuntu?

Also, can you see the Windows partition(s) from within Ubuntu's file browser?

---

### Post by mcduck on 2009-02-20
> **nemoneder said:**
> Thanks for your suggestions. I guess this is not the problem. It was working for a long time. By the way, what exactly I have to do to delete the old kernels. Thanks.

It's not really a matter of guessing.. ;) If the kernels list fills your screen in Grub, then that's the problem. If not, the problem is something else (although I can't really imagine anything else based on the information you gave, since Window is definitely included in your menu.lst. Even if you'd done some changes to your partitions, for example, the Windows entry would still show, it just wouldn't boot correctly). 

Anyway, to uninstall old kernels I recommend searching in Synaptic for "linux" in the package name. Then pick all old versions for linux-image, linux-headers and linux-restricted-modules, right-click and select "Mark for complete removal". When done, click "apply".

---

