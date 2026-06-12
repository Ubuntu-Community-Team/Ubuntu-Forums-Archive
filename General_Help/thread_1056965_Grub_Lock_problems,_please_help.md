---
title: "Grub Lock problems, please help"
date: 2009-02-01
forum: General Help
---

### Post by faux_fire on 2009-02-01
When I was securing the Ubuntu GRUB bootup while following this guide: [http://ubuntuforums.org/showthread.php?t=7353]("http://ubuntuforums.org/showthread.php?t=7353")
, I made a very stupid mistake and forgot, when inserting the encrypted password into menu.lst, to do password --md5 ************. My code now looks like this password –md5 *******. Other than that I followed the guide to the letter. Any thoughts on how to solve this problem? (If it helps, I am running Vista alongside it, and am using it to post this)

---

### Post by caljohnsmith on 2009-02-01
Can you boot your Live CD? If so, how about doing that, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
Find which is your Ubuntu partition as sdaX and do:
```
sudo mount /dev/[COLOR="Blue"]sdaX[/COLOR] /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And then you should be able to either change the password lines to what they should be, or you can remove them altogether. Let me know how that goes or if you run into problems.

---

