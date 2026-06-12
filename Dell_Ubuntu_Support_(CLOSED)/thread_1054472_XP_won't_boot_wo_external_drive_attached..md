---
title: "XP won't boot w/o external drive attached."
date: 2009-01-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by elementsenjoi1 on 2009-01-29
Okay I have a Dell laptop running Win XP. I wanted to try out Linux, but I didn't want it on my hard drive. I installed Ubuntu on a usb external drive. Both systems boot fine and I like Ubuntu, but I can't boot XP without the external drive attached. This is kind of inconvenient for me being that I do use it as a laptop. The Ubuntu was just for fun, I don't really need it. Is there any way I can resolve this? I am pretty new to installing operating systems so try to dumb it down a bit if you could.

Thanks in advance,
Chris

---

### Post by marshall.robert on 2009-01-29
Basically, whats happened is you needed to install the bootloader onto the external hard drive, but its installed on your internal one.

This means that grub (the bootloader that ubuntu uses) cant find its configuration files without the external hard drive because it keeps them on the ubuntu partition.

You could fix this by booting from an xp disk, getting a recovery console up and then after entering an admin password type ```
fixmbr
```

this would make you able to boot xp without the external hard drive. this would also mean that you cannot boot ubuntu...

this would require you to restore grub on your external hard drive, which may be a bit tricky and a bit of trial and error (but hopefully not)

you can achieve this by booting of a live cd, mounting your ubuntu partition on your external hard drive and then cracking open a terminal.

you will probably need to browse to where you ubuntu partition is mounted. some people argue that this is not needed, but i always have to do it.

```
cd /media/disk
```

disk may change depending. you can go
```
cd /media
ls
```
to see what you have. there will most likely be ones like cdrom0 and floppy0, but you can ignore those.

after browsing to your mounted partition type
```
sudo grub
```
this opens the grub application where you work some magic.
```
find /boot/grub/stage1
```
you should get something like (sd1,0) as your output. i will use this as an example.
```
root (sd1,0)
setup (sd1)

```
and that should do it :)

best of luck.

EDIT: if the above doesnt work then take out the hard drive if you can and then try again.

---

### Post by elementsenjoi1 on 2009-01-29
Thanks, that is a little confusing, but I will try it. I am afraid I will mess something up though. Should I be worried?

---

### Post by caljohnsmith on 2009-01-29
I just wanted to mention that Grub does not use (sdX,Y) notation, it's always (hdX,Y) whether the drive is IDE or SATA; I think that might be a small typo on Robert's part. You can restore a Windows MBR (Master Boot Record) to your Windows drive using "fixmbr" like Robert recommended, or you can do the equivalent from Ubuntu by opening a terminal (Applications > Accessories > Terminal) and doing:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
And then to install Grub to the MBR of your Ubuntu drive, you can do basically what Robert suggested:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let us know how it goes or if you run into problems.

---

