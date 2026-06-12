---
title: "help on mounting an iso file"
date: 2009-04-12
forum: General Help
---

### Post by CD661 on 2009-04-12
hi i am a complete ubuntu beginner , i am running 8.04 hardy heron thingie and i am using a acer aspire one 150 with 100 gb hard disc, i upgraded to ubuntu without much trouble and i am very pleased. i recently stumbled upon the playonlinux app and installed it but since i dont have a cd-rom drive in my netbook i cant install anything without iso's . lets skip ahead abit here so i dont have to explain my (evil) doing further. but i got an iso i wanted to mount and started to research. first i tried the following 

sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso (i used the real filename and moved it to user directory so that i worked) /media/iso/ -t iso9660 -o loop

but got error message:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

the error log lookes like this

[ 8994.574278] FAT: Directory bread(block 503) failed
[ 8994.574291] FAT: Directory bread(block 504) failed
[ 8994.574303] FAT: Directory bread(block 505) failed
[ 8994.574315] FAT: Directory bread(block 506) failed
[ 8994.574328] FAT: Directory bread(block 507) failed
[ 8994.574340] FAT: Directory bread(block 508) failed
[ 8994.574352] FAT: Directory bread(block 509) failed
[ 8994.574364] FAT: Directory bread(block 510) failed
[ 8994.574376] FAT: Directory bread(block 511) failed
[ 9026.295903] ISOFS: Unable to identify CD-ROM format.

 
so i tried some other options with gmountiso and fuseiso but got the same results. 

i really REALLY want it to work but please explain everything to me very very simple. the only thing i can do in terminal is follow what people tells me to do step by step from the internet! ^_^

---

### Post by aktiwers on 2009-04-12
Have you seen this?
[http://www.getdeb.net/app/AcetoneISO](http://www.getdeb.net/app/AcetoneISO)

Edit:
What game are we talking about? Maybe ther is an easier way to install it

---

### Post by coffeecat on 2009-04-12
You don't need the modprobe line. Move the iso to your Desktop, then:

```
sudo mkdir /media/iso
```You can omit this if you've already created /media/iso.Then:

```
sudo mount -o loop ~/Desktop/filename.iso /media/iso
```And a CD icon will appear on your desktop labelled 'iso'. Double-click on that and you can browse the contents. Everything will be owned by root, so if you want to copy things out, you'll have to 'sudo cp' and use the /media/iso path

You can put the iso somewhere else if you want, but you'll have to change the path in the mount command. I've suggested using the desktop because then you can see everything happening.

When you've finished, unmount with:

```
sudo umount /media/iso
```

---

### Post by CD661 on 2009-04-12
@ aktiwers 

the game is warcraft 3 :D ok so i downloaded acetoneiso2 and it finally worked! cant get it to work with playonlinux tho, but i can just run it through wine :) thanks a bunch! 

@coffeecat
then it tells me: 

mount: you must specify the filesystem type 

i got i working the other way but would be nice to have a working solution for the terminal :))

---

### Post by coffeecat on 2009-04-12
> **CD661 said:**
> 
@coffeecat
then it tells me: 

mount: you must specify the filesystem type 

i got i working the other way but would be nice to have a working solution for the terminal :))

Curious. I actually tried the code I posted before posting using the Ubuntu Jaunty daily build iso and this mounted fine. Perhaps your iso is damaged or corrupted somehow - the error you posted in your first post certainly suggests this - but you managed to access it with actoneiso. Very odd. The only thing else I can suggest is simply a rearrangement of your original mount command, as follows:

```
sudo mount -o loop -t iso9660 ~/Desktop/filename.iso /media/iso
```Which also works with my Ubuntu iso.

---

