---
title: "changing boot system"
date: 2009-04-11
forum: General Help
---

### Post by djallalnamri on 2009-04-11
*hello again
*i used to partition my hd with mandriva then install:
 1 mandriva
 2 winxp
 3 ubuntu
 thus ubuntu would detect other installed os and be the booting one
*but recently i made a mistake and used same mounting point for both mandriva and ubuntu so i have problem with mandriva which would not start because its mounting point is used by ubuntu so i had to install mandriva all over again but this made mandriva become the booting system:

   - mandriva splash screen:
     mandriva
     ubuntu
*choosing ubuntu gives:
     ubuntu
     other operating systems:
     winxp
*now i want to totally remove mandriva and stick to ubuntu but i am afraid that suppressing mandriva partition with gparted for instance will
definitely not allow any system to boot
*of course i can choose ubuntu as a booting system but i still will have to do it with mandriva again
*any idea....
*thanks in advance....

---

### Post by cariboo on 2009-04-11
If you remove Mandriva, you can use [thread=224351]this[/thread] howto to repair grub.

Jim

---

### Post by djallalnamri on 2009-04-12
*hello
*i put myself in trouble when i used gparted live cd to delete mandriva partition and i could even resize the ubuntu one
*since the system was booting with mandriva i lost my boot!!!!
*so i spend the whole night looking for solutions using your links and others unsuccessfully
*it is only at dawn when i typed "e" that i knew the root device was not 4 as detected by grub but 5:(hd0,5) instead of (hd0,4) so i went again googling until i found this:[https://lists.ubuntu.com/archives/kubuntu-users/2008-August/030612.html](https://lists.ubuntu.com/archives/kubuntu-users/2008-August/030612.html)!!!!
*it was the solution and all i needed to do was to change 5 with 4 and now i boot on ubuntu and removed the mandriva partition as well...
*thanks for reply...:popcorn:

---

