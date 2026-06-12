---
title: "modifying an iso?"
date: 2009-03-22
forum: General Help
---

### Post by linuxisevolution on 2009-03-22
I downloaded the Ubuntu iso, and I am currently modifying some things. I extracted the iso to a directory to add some files to it and used mkisofs to create the iso again, but it will not boot.

What is the best way to modify an iso and still keep it bootable?



Please help!!!

---

### Post by emarkay on 2009-03-22
AFAIK, and ISO is a FIXED IMAGE of a CD.
You need to "recompile" it.
I think you are trying to get prune juice from an apple and an orange.

---

### Post by linuxisevolution on 2009-03-22
> **emarkay said:**
> AFAIK, and ISO is a FIXED IMAGE of a CD.
You need to "recompile" it.
I think you are trying to get prune juice from an apple and an orange.

How do I 'recompile' it? I am trying acetoneiso2 at the moment to start over and see if extracting it with this program will help.


Don't I just need to make it bootable?

---

### Post by linuxisevolution on 2009-03-22
how do i make this bootable?

---

### Post by emarkay on 2009-03-22
[http://en.wikipedia.org/wiki/ISO_image](http://en.wikipedia.org/wiki/ISO_image)

I don't do programming - this is beyond me now...

---

### Post by snowpine on 2009-03-22
Check out an application called Remastersys. It allows you to make a custom Ubuntu "remix" ISO from your currently installed system.

---

### Post by linuxisevolution on 2009-03-22
> **snowpine said:**
> Check out an application called Remastersys. It allows you to make a custom Ubuntu "remix" ISO from your currently installed system.

I know, but that is very far from what I want.

I need to edit config files..

---

### Post by igor. on 2009-03-22
See here: [http://ubuntuforums.org/showthread.php?t=1102213](http://ubuntuforums.org/showthread.php?t=1102213)

---

### Post by linuxisevolution on 2009-03-22
> **igor. said:**
> See here: [http://ubuntuforums.org/showthread.php?t=1102213](http://ubuntuforums.org/showthread.php?t=1102213)

I already know how to modify the squashfs files, but thats not what I need.

I need to modify the ACTUAL files located on the cd's root directory, and reburn it.

 I have the iso made now how do I make it bootable? :)


Thanks! :)

---

### Post by linuxisevolution on 2009-03-22
thanks everyone, I was able to do it with the command:

sudo mkisofs -D -r -V  -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o zephyrus2.iso work


Result:

[http://98.219.177.90/apache2-default/linforum/forum/forum/hdd/cache/zephyrus2.iso](http://98.219.177.90/apache2-default/linforum/forum/forum/hdd/cache/zephyrus2.iso)

I am remastering several times this day so forgive me if the iso is not complete when you download...

---

