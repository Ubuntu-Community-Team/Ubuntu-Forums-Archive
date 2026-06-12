---
title: "Grub Help (Solved)"
date: 2005-11-30
forum: Desktop Environments
---

### Post by bananaman on 2005-11-30
Hey... i need some help!
I'm not sure how to change the GRUB so that Windows automatically starts when i turn on my computer instead of Ubuntu...

i tried going in to the menu.lst file in /boot/grub/ but i cant get it to work..
can someone help me out with this??

---

### Post by Iandefor on 2005-11-30
How is it that it won't work? Like, what does it say when you try to open up /boot/grub/menu.lst ?

---

### Post by Xian on 2005-11-30
Read this: [Customize Grub Loader](http://www.ubuntuforums.org/showthread.php?t=95586&highlight=menu.lst).
Edit the file with this command:

$ sudo gedit /boot/grub/menu.lst

---

### Post by bananaman on 2005-11-30
umm... i CAN go in the menu.lst file, i just dont understand the instructions on how to change the order of the operating system.
There are instruction IN the menu.lst file.. but im kind of a newbie.. so i don't understand very well

---

### Post by Xian on 2005-11-30
If Windows is your 2nd OS entry then change the default number to 1, if it is the third OS entry change the default number to 2, and so forth. Ubuntu is going to be the first entry, so a number of 0 will get you that booted automatically.

Do NOT change the order of the operating systems. It is _way_ to easy to make a mistake and then you will have more serious issues. Also, when you upgrade your kernel the order will get switched again so you are back to square one.

---

### Post by aznboi on 2005-11-30
Post up what u have in them menu.lst file and we'll help you out with it

---

### Post by bananaman on 2005-11-30
this is  what i have:

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdc5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdc5 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdc5 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1



which number do i need to change???
i tried changing this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc2
title		Microsoft Windows XP Home Edition
root		(hd0,0) <---- I changed this number to "0"
savedefault
makeactive
chainloader	+1

but it didnt work.

---

### Post by aysiu on 2005-11-30
Change *default 0* to be *default 6*.

It's at the very beginning of the menu.lst file: ```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
**default         0**
```

---

### Post by mrmcctt on 2005-11-30
> Change default 0 to be default 6.

It's at the very beginning of the menu.lst file:

Shouldn't that be 5, aysiu?  I started counting from '0' and windows was the fifth listing. 

> which number do i need to change???
i tried changing this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc2
title Microsoft Windows XP Home Edition
root (hd0,0) <---- I changed this number to "0"
savedefault
makeactive
chainloader +1

but it didnt work.

I think you need to change that back to a 1 or you may not be able to boot to windows.

---

### Post by bananaman on 2005-11-30
Alright!
Thanks... got it working...
thanks again...

---

### Post by mrmcctt on 2005-11-30
Sorry, aysiu.  Guess I've got a little more to learn.

---

### Post by aysiu on 2005-11-30
[QUOTE=mrmcctt]Sorry, aysiu.  Guess I've got a little more to learn.[/QUOTE] Every time you see the word *title*--that's another entry. So Windows is actually the seventh entry... hence, *default 6*.

---

### Post by mrmcctt on 2005-11-30
I see....I thought the last one was just the OP showing that they changed their partition numbers and not a part of menu.lst.

Thanks

---

### Post by aysiu on 2005-11-30
[QUOTE=mrmcctt]I see....I thought the last one was just the OP showing that they changed their partition numbers and not a part of menu.lst.

Thanks[/QUOTE] No, you're right. The last one is just the tried change. My point before was that even this line ```
title Other operating systems:
root
``` is considered an entry, making Windows the seventh, not the sixth entry.

---

### Post by mrmcctt on 2005-11-30
OK 

I got it now.

Thanks again.

---

