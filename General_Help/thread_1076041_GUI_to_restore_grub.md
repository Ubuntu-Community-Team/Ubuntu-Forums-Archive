---
title: "GUI to restore grub"
date: 2009-02-20
forum: General Help
---

### Post by garyflynn on 2009-02-20
I have windows on sda1 and ubuntu on sdb3, with various other data, swap and rescue partitions on other parts of the disks.

Is there a gui that will find the operating systems and set up grub without me going to the command line?

I've seen advice to use my installation cd to pretend I'm installing but not formatting the partitions so that it will automatically configure grub and then error out.  I'm afraid to try that because if it does try to overwrite, I've lost hours of work.

I have not been able to find a gui that will analyze my disks, figure out what is what and prepare grub for me automatically, the way the installer will.

Does this exist somewhere? I'd really rather not manually configure /boot/grub/menu.lst because I'm not sure what I'm doing.

---

### Post by caljohnsmith on 2009-02-21
To my knowledge there is no GUI program available that will automatically configure Grub to boot all your OSes; only the Ubuntu installer tries to do that when you install Ubuntu. Definitely I would not recommend trying to go through the steps of installing Ubuntu again just to try to get it to configure Grub to boot all your OSes, because as you've all ready surmised, probably it will just completely overwrite your current Ubuntu install. If you would like a hand booting all your OSes from Grub, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and what it might take to boot all your OSes from Grub.

---

### Post by saidinesh5 on 2009-02-21
do you mean sth like Grubconf or KGRUBEditor ??

---

### Post by garyflynn on 2009-02-21
Thanks everyone.  I've gotten it working.  I wasn't comfortable overwriting the mbr by myself because that may have been a contributing factor in nuking my windows partition, forcing me to reinstall yesterday.  But since there is no gui that will do it for me, I guess I had to bite the bullet and install it manually.

Thanks for looking.

You would think that since the code for analyzing the hard disk/os configuration has already been written on open source terms, that the code could be pulled out and issued as a separate package.

But the standard grub, find stage 1, root, install on the hd does work to anyone else who finds this if there still is no gui.

The GUIs that are available do not look at the hard drives to try to find operating systems, they just provide input fields to essentially edit menu.lst manually.

But thanks again.

---

