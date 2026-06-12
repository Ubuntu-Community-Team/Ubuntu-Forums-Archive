---
title: "A dual boot computer and a broken laptop screen"
date: 2009-02-12
forum: General Help
---

### Post by dlawler on 2009-02-12
well, i've been dual booting vista and ubuntu no problem for about a year not, and i know my fair share of things. buuuuuuuut, i dropped my laptop, and do not have the money for the repair. so for now it's been sitting at my home, with an external monitor, and it's been in vista, because that's what was running when the screen broke, i just plugged it in (vista is kept around for the rest of the family). wellllll, the power went out and my computer had to manually restart, and somehow ended back up in ubuntu, but it's necessary that i access my windows partition (i need to use some programs i cannot run in windows) but my monitor won't let me see the GRUB loader, and i've tried pushing lots and lots of buttons to get to select the windows partition (i've sucessfully done it once in the past) and cannot get to it... 

so, now the question.

is there anyway i can rearrange the order in which the boot options show up on the grub loader? or can i just tell ubuntu to automatically boot up into vista on my next restart?

this is realllllllly important...
(engineering homework that needs completed....)

---

### Post by mkvnmtr on 2009-02-12
There is a program in the package manager and maybe in add and remove that lets you set the next default start in grub. I forgot the name but you can probably use just gtub in the search box and find it.

---

### Post by girishsasikumar on 2009-02-12
Once u boot sucessfully into Ubuntu u need to edit
/boot/grub/menu.lst
so type the following code into a terminal (accessories->terminal)
```
sudo gedit /boot/grub/menu.lst
```
you will see a line like
```
default 0
```
This means your default OS is set to 0, now go down further to end of file and u will see a list of OS, something blocks like this

```

ubuntu kernel 2.24.4 ... blah blah

ubuntu kernel .... restore

:
:
:

other operating system

windows  vista
rootnoverify
chainloader +1

```

now u can understand that default is set to 0 ur ubuntu OS, so count number of blocks to ur vista listing and put that as default like this (suppose vista is in ur 5th block)

```
default 5
```

save the file and restart, u should get to ur vista

get back to me if u have any problemz ... else mark the query as solved .....

---

### Post by girishsasikumar on 2009-02-12
Or you can install a package called

Kgrubeditor (check in add remove programs)

There was another one in gnome too but i cant remember the name

---

### Post by dlawler on 2009-02-13
> **girishsasikumar said:**
> Once u boot sucessfully into Ubuntu u need to edit
/boot/grub/menu.lst
so type the following code into a terminal (accessories->terminal)
```
sudo gedit /boot/grub/menu.lst
```
you will see a line like
```
default 0
```
This means your default OS is set to 0, now go down further to end of file and u will see a list of OS, something blocks like this

```

ubuntu kernel 2.24.4 ... blah blah

ubuntu kernel .... restore

:
:
:

other operating system

windows  vista
rootnoverify
chainloader +1

```

now u can understand that default is set to 0 ur ubuntu OS, so count number of blocks to ur vista listing and put that as default like this (suppose vista is in ur 5th block)

```
default 5
```

save the file and restart, u should get to ur vista

get back to me if u have any problemz ... else mark the query as solved .....

did both ideas.
should have worked, but miraculously, i'm still ubooting....

could i really just be real dirty and delete all my linux kernals from the grubloader (make a back up of course) and restore it once in windows?

imean it's a crazy idea, but the problem with the whole thing is, is that i've got about 2 or 3 hours before class, and i'm desperate...

---

### Post by Yellow Pasque on 2009-02-13
> now u can understand that default is set to 0 your ubuntu OS, so count number of blocks to your vista listing and put that as default like this (suppose vista is in your 5th block)
If Vista was in the "5th" slot, then default would be 4.
Remember to start counting at 0 and not 1 ;)
e.g.
```
title Ubuntu blah
...
title Ubuntu blah (recovery mode)
...
title Windows Vista
```
Then default would be 2.

---

### Post by dlawler on 2009-02-13
--Edit--

did get it to get into the login screen..
but of course, i either need to choose to boot into admin or my account. if i can get into admin, i can change users (i've had to do it before, ironically)....


but alas.
i cannot see what i am clickin.


i don't suppose any one here would be of help there, either?

---

### Post by cd-r80 on 2009-02-13
If you want to get Vista booted, keep tapping arrow down key when booting. Windows is usually the down one in the menu.

---

### Post by dlawler on 2009-02-13
> **cd-r80 said:**
> If you want to get Vista booted, keep tapping arrow down key when booting. Windows is usually the down one in the menu.

that doesn't work for some reason....
now i can't even get into it. :(

---

### Post by Yellow Pasque on 2009-02-13
Post your /boot/grub/menu.lst

---

### Post by dlawler on 2009-02-13
> **Temüjin said:**
> Post your /boot/grub/menu.lst

default 14
timeout 12

title Ubuntu 8.04.1, kernel 2.6.24-22-rt
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-22-rt root=UUID=c2912272-a4dc-445d-b00f-5a43351c7f2e ro quiet splash vga=792
initrd /boot/initrd.img-2.6.24-22-rt

title Ubuntu 8.04.1, kernel 2.6.24-22-rt (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-22-rt root=UUID=c2912272-a4dc-445d-b00f-5a43351c7f2e ro single
initrd /boot/initrd.img-2.6.24-22-rt

title Ubuntu 8.04.1, kernel 2.6.24-22-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=c2912272-a4dc-445d-b00f-5a43351c7f2e ro quiet splash vga=792
initrd /boot/initrd.img-2.6.24-22-generic

title Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-22-generic root=UUID=c2912272-a4dc-445d-b00f-5a43351c7f2e ro single
initrd /boot/initrd.img-2.6.24-22-generic

title Ubuntu 8.04.1, kernel 2.6.24-21-rt
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-rt root=UUID=c2912272-a4dc-445d-b00f-5a43351c7f2e ro quiet splash vga=792
initrd /boot/initrd.img-2.6.24-21-rt

title Ubuntu 8.04.1, kernel 2.6.24-21-rt (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-rt root=UUID=c2912272-a4dc-445d-b00f-5a43351c7f2e ro single
initrd /boot/initrd.img-2.6.24-21-rt

title Ubuntu 8.04.1, kernel 2.6.24-21-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=c2912272-a4dc-445d-b00f-5a43351c7f2e ro quiet splash vga=792
initrd /boot/initrd.img-2.6.24-21-generic

title Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-21-generic root=UUID=c2912272-a4dc-445d-b00f-5a43351c7f2e ro single
initrd /boot/initrd.img-2.6.24-21-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=c2912272-a4dc-445d-b00f-5a43351c7f2e ro quiet splash vga=792
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=c2912272-a4dc-445d-b00f-5a43351c7f2e ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=c2912272-a4dc-445d-b00f-5a43351c7f2e ro quiet splash vga=792
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=c2912272-a4dc-445d-b00f-5a43351c7f2e ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin

title Other operating systems:

title Windows Vista/Longhorn (loader)
root (hd0,1)
chainloader +0
savedefault
makeactive


i have a lot of kernals...
i know.

think of it as a young linux entrepreneur's mistake

---

### Post by cd-r80 on 2009-02-14
menu.lst looks Ok.  Are sure that Vista partition is not corrupted?
Perhaps you can move your:

title Windows Vista/Longhorn (loader)
root (hd0,1)
chainloader +0
savedefault
makeactive

first in menu.lst & set default to 0. But perhaps it is not the problem.

---

### Post by dlawler on 2009-02-14
you know, i haven't even thought of the idea of it being corrupt, because i have been logged into it for so long now, for sometime.

so, what should i do next?
haha.

delete ye olde vista partition?

---

### Post by cd-r80 on 2009-02-15
There is:

[http://ubuntuforums.org/showthread.php?t=729535](http://ubuntuforums.org/showthread.php?t=729535)

sudo apt-get install ntfsprogs

sudo ntfsfix /dev/hda1
or /dev/sda1 or what was your Vista partition.

I have not tried it.

---

