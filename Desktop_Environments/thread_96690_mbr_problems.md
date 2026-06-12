---
title: "mbr problems"
date: 2005-11-29
forum: Desktop Environments
---

### Post by nrayever on 2005-11-29
hi everyone:

i got some problems with my linux box. when i power up my box, i got a missing os error!! i got panic, then i took my live cd and try to look for all my documents. info was save and there.  i have 2 hard disks 80 gb each, one for os/home/swap and the other for documents.

i make a backup of my home and then i just reinstalled my ubuntu 5.10 but i got the same problem. so i decided that i should reset the mbr of the os disk. normally i use ultime boot cd to do that with mbrwork. after doing that i realized that i f#$%ed the mbr for my documents disk!!!](*,) ](*,) ](*,) ](*,) 

can i anyone help me recovering the mbr for my disk. it was a ext3 with a single partition in hdb1. i don't know how to recover it!!. and my documents are really important!!
 
please!! some help!!!:cry: :cry: :cry: :cry: 

sincerly nrayever

---

### Post by kalin on 2005-11-29
Try installing and running "testdisk". It's a command line tool that recovers lost partitions, and works pretty good.

One thing - since you don't mention the architecture of your PC in you post I think it's worth mentioning that it can't handle Mac partitions.

---

### Post by nrayever on 2005-11-29
sorry kalin, my box is an amd64 i will try i hope this works!! :smile: :smile:

---

### Post by nrayever on 2005-11-29
no luck yet, because my mbr was cleared, so, there are no partitions on the disk!!  please any other method!!

---

### Post by Original Brownster on 2005-11-30
[QUOTE=nrayever]

can i anyone help me recovering the mbr for my disk. it was a ext3 with a single partition in hdb1. i don't know how to recover it!!. and my documents are really important!!
[/QUOTE]

My friend this might just be your saviour: [Gpart]("http://www.stud.uni-hannover.de/user/76201/gpart/")

I haven't tried it but if you have no other option this could help you.

Let us know how you get on.

Regards

---

### Post by Danielle on 2005-11-30
hi, i deleted one of my partitions by mistake and i recovered it with a program that's on ubcd (ultimate boot cd). i didn't use ubcd becuase it wasn't my primary so i could bootup and just used the standalone program by its self. 

i can't remember what it's called but i'll find out what it's called if you like?

don't know if it works with a linux partition but it should if it's just the table you need, shouldn't it? i'll try and find out what it's called

---

### Post by Danielle on 2005-11-30
here you go [quote=from site]TestDisk is a powerful data recovery utility! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again[/quote]
[http://www.cgsecurity.org/phpwiki/index.php/testdisk](http://www.cgsecurity.org/phpwiki/index.php/testdisk)
[http://www.cgsecurity.org/index.html?testdisk.html](http://www.cgsecurity.org/index.html?testdisk.html)

here's the boot cd TestDisk is under Partition Tools
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

hope it works with Linux

---

### Post by Danielle on 2005-11-30
OK i just read the whole of your first post. sorry for being lazy and not reading it all.

---

### Post by Original Brownster on 2005-11-30
[QUOTE=Danielle]here you go 
[http://www.cgsecurity.org/phpwiki/index.php/testdisk](http://www.cgsecurity.org/phpwiki/index.php/testdisk)
[http://www.cgsecurity.org/index.html?testdisk.html](http://www.cgsecurity.org/index.html?testdisk.html)

here's the boot cd TestDisk is under Partition Tools
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

hope it works with Linux[/QUOTE]

Hi,
That looks really good, I think I'll have to d/l a copy!

---

### Post by Danielle on 2005-11-30
what testdisk or ubcd? because there's a live windows cd called ubcd4win that's 10 times better then ubcd, it's a proper live wincd with lots of great apps on.

---

### Post by Danielle on 2005-11-30
good luck, i have to go and catch a train.

---

### Post by kalin on 2005-11-30
[QUOTE=nrayever]no luck yet, because my mbr was cleared, so, there are no partitions on the disk!!  please any other method!![/QUOTE]

Hm, testdisk doesn't need a partition table, it will restore it, when you tell it to save ("write") the partitions found.

Just to make sure it's clear: it needs root privileges, so you need to run it this way: "sudo testdisk".

If you run it in a X terminal (e.g. gnome-terminal) you will need to resize the terminal (just make it a little bit higher), since testdisk requires 25 lines of text to be visible - it will tell you about it when you start it.

Then choose the device from the list, using the up/down arrow keys. Make sure Analyze is selected and hit Enter.

On this step it will show you the current partition structure, in your case - nothing. Hit Enter again.

Then the tool will analyze the contents of the harddisk, sector by sector, and will try to find lost partitions. After analysis is complete it will show you the list of partitions found. You can change some things here as you see fit (like making a partition bootable). If you like them the way it shows them just hit Enter again.

Now it should display how the final result would look if you choose to save. If you like it just highlight "Write", press Enter, and confirm by pressing Y when asked , and you will have your ext2 partition restored.

---

### Post by nrayever on 2005-12-02
thanks to everyone i really appreciate your help but i have to tell you, that i had already overwirte on my hard disk! and i had discoverd something more...... all my problems began because my system memory wasn't working well. most of times i tried to reinstall ubuntu, it failed at different stages. or when installation was completed, after rebooted again failures. i even tryed switching hard disks while installing, but no luck.

today i tried with the memory of my older brother pc. and it work smoothly!!

i was a victim of a bad quality process. :( :(  i bought this memory about 3 months ago!! today i reclaimed for its warranty i hope tomorrow i got a new one.

ok, so what i had learned of all this:

a) check twice before taking any kind of action
b) if you try to install ubuntu and you can't finish or after installation you got some strange errors, fails or even kernel panics, this means that might be your system memory is dying

i hope this thread could help someone else. and again thanks to everyone for your help. 

sincerly nrayever

---

