---
title: "Dual-Boot Problem. Help!!!"
date: 2009-03-01
forum: General Help
---

### Post by Graham1 on 2009-03-01
Hi

I've accidently installed GRUB to hd0,1 (which contain XP) rather than hd0,0 (Ubuntu). I use XOSL as my boot loader (from MBR) which points to each partition. 

How do I re-install GRUB back onto hd0,0 and also clear GRUB from my second partition so XP can boot?

Hope someone can help

:)

---

### Post by caljohnsmith on 2009-03-01
You can restore the XP partition boot sector by booting your Windows Install CD, go to the "recovery console" and do:
```
fixboot
```
And to install Grub to (hd0,0), you can do:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0,0)
grub> quit
```
Let me know how that goes or if you run into problems.

---

### Post by Rallg on 2009-03-01
Some XP systems did not come with an XP install CD, instead relying on a Windows recovery partition. I do not recall the details, but it is possible to restore the XP boot loader even without the CD. I did it once, years ago. Might be that there is something on the Microsoft web site. Surfing the Internet for advice won't help, since nearly everyone will tell you to use the XP install CD.

---

### Post by Graham1 on 2009-03-01
> **caljohnsmith said:**
> You can restore the XP partition boot sector by booting your Windows Install CD, go to the "recovery console" and do:
```
fixboot
```
And to install Grub to (hd0,0), you can do:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0,0)
grub> quit
```
Let me know how that goes or if you run into problems.

Thanks caljohnsmith, I owe you one :)

Just a quick question. If I were to install GRUB to the MBR, does it always detect new operating systems and add them to the list? I've always tended to install each distro's GRUB to it's own partition and then point XOSL to the required OS.

:)

---

### Post by Graham1 on 2009-03-01
> **Rallg said:**
> Some XP systems did not come with an XP install CD, instead relying on a Windows recovery partition. I do not recall the details, but it is possible to restore the XP boot loader even without the CD. I did it once, years ago. Might be that there is something on the Microsoft web site. Surfing the Internet for advice won't help, since nearly everyone will tell you to use the XP install CD.

Thanks for your reply Rallg :). Luckily, I own the XP CD.

:)

---

### Post by caljohnsmith on 2009-03-01
> **Graham1 said:**
> Thanks caljohnsmith, I owe you one :)

Just a quick question. If I were to install GRUB to the MBR, does it always detect new operating systems and add them to the list? I've always tended to install each distro's GRUB to it's own partition and then point XOSL to the required OS.

:)
Grub doesn't automatically detect other OSes and add them to its menu.lst, but that is not hard to do once you get the hang of it. :) If you would like help adding all your OSes to your Grub's menu.lst, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by Graham1 on 2009-03-01
> **caljohnsmith said:**
> Grub doesn't automatically detect other OSes and add them to its menu.lst, but that is not hard to do once you get the hang of it. :) If you would like help adding all your OSes to your Grub's menu.lst, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

I think I'll stick with using XOSL as that seems easier but thanks for your suggestion anyway :). 

Next time I just need to make sure a choose the correct settings. It funny, I've done this setup so many times (with Ubuntu) but I guess we all make mistakes. Thanks again. 

:)

---

