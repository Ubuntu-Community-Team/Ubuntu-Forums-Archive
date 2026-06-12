---
title: "dual boot time out"
date: 2006-01-04
forum: General Help
---

### Post by bobhc on 2006-01-04
Hi
I have installed ubuntu and have no complaints(early days).
I am dual booting as my wife is only just get to find her way around WINXP so I want 
to get to find out and use ubuntu more before I throw her in at the deep end and remove WINXP. I have tried to edit menu.1st in the grub folder to take out the 10
second and replace with 0 as I belive that then holds the boot menu untill the user
make a choice. my wife complains it boots in to ubuntu before she can pick WINXP.
But I am unable to edit the file,in the properties it say I can read/write on the permissions tab.
There is only one account, my self, do I need to set up any permissions else where
and if so how do I do it.


Bob

---

### Post by Chris Tucker on 2006-01-04
open a terminal and enter:
sudo gedit /boot/grub/menu.lst

it will ask for a password, re enter yours, thats a security precaution.
you can replace the word gedit with whatever your favorite editor is.
also, the file extention is LOWERCASE LST, as in short for list..  .lst  .. i just like makeing that clear because i have had several people say they do "ls" and think its .1st and complain that it cant find that file...

---

### Post by oakz on 2006-01-04
menu.lst is usually only editable by root, to edit the file use sudo from the terminal:

$ sudo vi /boot/grub/menu.lst

---

### Post by bobhc on 2006-01-04
Hi
The speed of the replys is first class,
I did as instructed and was able to edit.
0 (zero) is not the right number as the computer boote straight in to ubuntu, no
bootloader menu, do you now of the right thing to enter or do I just put in some hufe figure

Bob

---

### Post by kingsidy on 2006-01-04
about 4 to 5 seconds i think is pretty good

---

### Post by beerorkid on 2006-01-04
I just cut and paste the whole xp info part to the top of the list.  it rearranges the boot order.

Sorry I can not display mine cuz I am on a work ubuntu box, not dual boot :-(  but here is the general jist of what I am saying

right after:> ## ## End Default Options ##

and before: > title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

I put in the windows entry which would be listed at the very bottom

---

### Post by oakz on 2006-01-04
Setting the timeout to -1 disables it, forcing the user to make a menu selection

---

### Post by bobhc on 2006-01-04
Hi all
it was -1, working a treat, my thanks to all for there help


Bob

---

