---
title: "Creating Ghost Images of HDD in Ubuntu"
date: 2009-05-13
forum: General Help
---

### Post by Vigh on 2009-05-13
hi, I was just wondering if there are any programs out there for ubuntu that are capable of making ghost images of your ubuntu install with programs and data, also I have done a little bit of robotics programming but all in all am not that great a programmer but would love to be involved in the ubuntu community, are there any resources available that I could study, what is the primary programming language used for debian linux, ubuntu? I am a believer in open-source software and love the idea of non-proprietry software and operating systems, I would love to contribute what-ever I can to the community, yours sincerely Anthony Vigh

---

### Post by kaibob on 2009-05-13
Have a look at:

Clonezillla
[http://www.clonezilla.org/](http://www.clonezilla.org/)

Partimage
[http://www.partimage.org/](http://www.partimage.org/)

Ghost for Linux
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

I have personally used Clonezilla, and it works well, although grub issued error messages after a restore. I have used Acronis True Image for many years, and it also works well, but you have to pay for it. Also, True Image does not work with EXT4 except on a sector-by-sector basis.

---

### Post by aeiah on 2009-05-13
most stuff is C but a lot of the smaller apps are python, which is a fun and versatile language to learn if you're starting out. as for ghosting.. there are things like part image and clonezilla but you dont really need that sorta thing unless you've got loads of computers. just use the trusty dd command, but read up on it first of course.

a basic dd command would be something like:
```

dd if=/dev/sda1 of=/media/externaldrive/root.img

```

where sda1 is the drive or partition you want a bit-for-bit copy of, and root.img is where you want to save it. you could also copy from one drive to another, making an exact partition instead of image but images are more flexible in terms of storage etc.

if you wanted to restore root.img you'd do:
```

dd if=/media/externaldrive/root.img of=/dev/sda1

```

there are other settings that you might want to include, or you might want to pipe the dd output straight into a tar.gz to save space (dd will copy empty space too so your image can probably compress quite well). i strongly suggest googling for examples and making sure you know what goes in 'if=' and what goes in 'of=' :p

bear in mind that you cant copy from a mounted partition, so you'll be best doing it from a livecd. i often do it from the gparted livecd.

---

