---
title: "GRUB broken - cannot startup Ubuntu"
date: 2009-02-28
forum: General Help
---

### Post by FalFire on 2009-02-28
I cannot boot into Ubuntu anymore since I installed SUSE linux on another partition. Before I installed SUSE linux I had Ubuntu and windows on separate partitions, and everything worked fine. Now when I boot up I have another bootloader, at least one with a novell SUSE theme. The option to boot Ubuntu is still there however it gives me "Error 15: file not found" when I try to boot up Ubuntu. 

I think the problem is that I mounted SUSE linux under / when installing it. According to the partition manager in SUSE the Ubuntu and Windows partitions are not mounted at all. I think it is looking for the boot files in the SUSE partition. How can I get my old GRUB back and load off the Ubuntu partition?

---

### Post by hallbrian on 2009-02-28
If you have a live cd you can use that to reload Grub

In live session use terminal

```
sudo grub 

find /boot/grub/stage1  (use this to find your ubuntu partition number)

root (hd0,*)       use above for *

setup (hd0)

Quit
```

reboot then grub should start up and should find all other partition ie windows and suse and show on table.

---

### Post by caljohnsmith on 2009-02-28
It would help to first get a clearer picture of your setup, so how about downloading the **Boot Info Script** to your OpenSUSE desktop (or you can use a Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do the following as **root user**, but replace <username> with your user name:
```
bash /home/[COLOR="Blue"]<username>[/COLOR]/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by BLTicklemonster on 2009-02-28
> **caljohnsmith said:**
> It would help to first get a clearer picture of your setup, so how about downloading the **Boot Info Script** to your OpenSUSE desktop (or you can use a Live CD):

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do the following as **root user**, but replace <username> with your user name:
```
bash /home/[COLOR="Blue"]<username>[/COLOR]/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.


Whoa, cool, RESULTS.txt gives me the exact specific information I need to add to fstab to mount all my partitions on boot so that I don't have to open nautilus and click them to mount them, doesn't it? 

*edit:
Upon further reflection, it doesn't. I was hoping it displayed information on each partition like mtab does, but with uuid stuff and all. The only thing stopping me from using mtab to edit fstab is my laziness.

---

### Post by FalFire on 2009-02-28
> **hallbrian said:**
> If you have a live cd you can use that to reload Grub

In live session use terminal

```
sudo grub 

find /boot/grub/stage1  (use this to find your ubuntu partition number)

root (hd0,*)       use above for *

setup (hd0)

Quit
```

reboot then grub should start up and should find all other partition ie windows and suse and show on table.

Thanks, this worked! the first command returned two different partitions, I tried both and the last one worked! Grub doesn't show the new SUSE install however, but I'm planning on removing it anyway so it's not a problem.

---

