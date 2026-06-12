---
title: "[SOLVED] Boot Grub, 3 Operating systems on 2 hds..."
date: 2009-01-06
forum: General Help
---

### Post by zx6r1033 on 2009-01-06
I have Ubuntu 64bit and vista 64bit currently running as a dual boot system from my Sata drive. Recently, I got a job which requires me to load XP as well, but I didn't want to touch the partitions on my primary drive, so i loaded it onto my second HD. When I go into the grub menu, though, XP does not show up on the list, so I am assuming I have to add it myself. I am also assuming I can copy one of the other boot options and change the physical drive location so it finds it?  Last but not least, how do I figure out what Ubuntu has assigned my second drive?  (Windows views my second drive as 1,1 for Vista, 1,2 for Ubuntu, and 1,1 for XP, but ubuntu sees them differently.)

---

### Post by Pessulus on 2009-01-06
In the "/boot/grub/menu.lst" file it describes how to do it.

There will be a map over the hard drives in "/boot/grub/device.map"

---

### Post by caljohnsmith on 2009-01-06
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it might take to boot Windows from Grub.

---

### Post by zx6r1033 on 2009-01-07
> **Pessulus said:**
> In the "/boot/grub/menu.lst" file it describes how to do it.

There will be a map over the hard drives in "/boot/grub/device.map"

device.map didn't display either of the other two drives, so I took a guess and wrote it in as hd1,0 and it worked flawlessly. 

Thanks for your help!

---

