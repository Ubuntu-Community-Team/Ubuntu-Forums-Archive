---
title: "Where is dual boot script for Ubuntu 10.04/Windows7?"
date: 2012-04-26
forum: Desktop Environments
---

### Post by henryf61 on 2012-04-26
I would like to save a copy of the dual boot script for Ubuntu 10.04/Windows 7 before I upgrade to 12.04 and have no idea where it is. I am running Linux 2.6.32-41-generic-pae and the script offers me the choice to start any version from 2.6.32-41 all the way back to 2.6.32-21. I want to preserve this to show others an example of what LTS support looks like. Well, at least one aspect of that support.

TIA for any help.

henryf61

---

### Post by scottbomb on 2012-04-26
You may be looking for the grub config?

/etc/conf.d/grub

---

### Post by henryf61 on 2012-04-27
Hi Scottbomb,

Thanks for the suggestion. Using your tip I browsed through comments in several files and found what I was looking for in /boot/grub/grub.cfg. Except that it wasn't exactly what I wanted. I was hoping to see a plain text listing of what showed up on my screen. This file generates the listing but each line of the listing is surrounded by code that the file needs. In short, the file in the exact form I was hoping for does not exist. But I do know what generated it.

Thanks for the tip. It definitely answered my question.

henryf61

---

### Post by oldfred on 2012-04-27
This lists just the menu entries from grub.cfg.

List entries in grub
cat /boot/grub/grub.cfg  | grep menuentry
grep menuentry /boot/grub/grub.cfg


If you want to document your entire system you can run the bootinfoscript. I run it before & after every major change just to document where everything is at, partition layouts, what is in MBRs & PBRs etc.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact 

I driectly download script and even run it as part of my rsync backup script.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

