---
title: "adding a hard drive when ive got two already"
date: 2009-05-06
forum: General Help
---

### Post by frenchcr on 2009-05-06
Ive got ubuntu on one hard drive and xp on another and i choose which operating system to go into when grub appears when i boot up.

I bought a 1Tb drive today and want to put all movies and music on it so that both ubuntu and xp can access the files.

1) Is it just a plug and play thing?
or 
2) Will i have to format the drive so both can see it?..is so what format?
3) Do i have to do anything else like going into bios?
...if so..
4) What do i need to do?

---

### Post by bhishan on 2009-05-06
Make the filesystem NTFS so that u can view the drive from windows as well as ubuntu. Turn off your computer, plug in your hard drive (it is an internal hard drive isn't it). I think you should make your new harddrive slave by moving the pin. It is generally written on the hard drive itself. Then turn on the computer, both your operating systems must detect it.

---

### Post by frenchcr on 2009-05-06
> **bhishan said:**
> Make the filesystem NTFS so that u can view the drive from windows as well as ubuntu. Turn off your computer, plug in your hard drive (it is an internal hard drive isn't it). I think you should make your new harddrive slave by moving the pin. It is generally written on the hard drive itself. Then turn on the computer, both your operating systems must detect it.

Yeh, its an internal, the Samsung SpinPoint F1 1TB SATA-II with 32MB Cache.

---

### Post by Legace on 2009-05-06
If it's a SATA drive, just plug it into a SATA port on your motherboard and you're ready to go :)

(No need to configure slave/master pins).

---

### Post by Dngrsone on 2009-05-06
Like bhishan said, format it NTFS and you will be able to see it from both sides.  You might have to add it to your /etc/fstab for easier mounting in Ubuntu, though.

---

### Post by frenchcr on 2009-05-06
> **Dngrsone said:**
> Like bhishan said, format it NTFS and you will be able to see it from both sides.  You might have to add it to your /etc/fstab for easier mounting in Ubuntu, though.

how do you add it to /etc/fstab (for easier mounting)

---

### Post by dabl on 2009-05-06
> **frenchcr said:**
> how do you add it to /etc/fstab (for easier mounting)

You follow this:

[http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab](http://ubuntuforums.org/showthread.php?t=283131&highlight=fstab)

:-)

---

### Post by Dngrsone on 2009-05-06
[Everything you need to know about fstab](http://ubuntuforums.org/showthread.php?t=283131&highlight=add+ntfs+drive+fstab)

---

### Post by frenchcr on 2009-05-06
Thanks folks !!

---

