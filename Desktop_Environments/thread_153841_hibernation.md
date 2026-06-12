---
title: "hibernation"
date: 2006-04-01
forum: Desktop Environments
---

### Post by peanut butter on 2006-04-01
how does hibernation work? when i tried it it just wouldnt start up so i had to do a hard reboot and samba is now broken. any help would be very much appreciated. if someone has some pointers on how to hibernate a computer:KS

---

### Post by jshein on 2006-04-01
Laptop or desktop? What CPU? What kernel are you running?

I am running an Acer TravelMate 4400 Laptop with a Turion 64 CPU. Running the i386 kernel or k7 kernel, it would not hibernate and CPU freqeuncy scaling was broken. Simply by running the i686 kernel, everything works. Hibernate, suspend to ram, and CPU frequency scaling.

---

### Post by peanut butter on 2006-04-02
it is a 64 bit desktop amd sempron. running the i386 kerenel because of lack of packages in the 64 bit edition of ubuntu.:)

---

### Post by jshein on 2006-04-02
On a whim, try installing the i686 kernel and see what that does for you.

Also have you looked into this thread?
[http://ubuntuforums.org/showthread.php?t=75443](http://ubuntuforums.org/showthread.php?t=75443)

---

### Post by peanut butter on 2006-04-02
sadly i cant try the i686 kernel because there is alredy lots of data on this machine.
that suspend thing sounds dangerous.

---

### Post by jshein on 2006-04-03
Installing a new kernel image will not affect your existing data. It will install along side your exisiting kernel, and you will have the choice of what kernel to boot from in the grub menu when your pc is started.

The following line will install the i686 kernel
#sudo apt-get install linux-image-686

the other thing that you may need to do to enable hibernation, is to identify the swap partition to resume from.

#sudo nano /boot/grub/menu.lst

look for the line that is called kopt, and put a line in that refers to your swap partition "resume=<swap>"

Mine looks like this for a Turion64 Laptop
# kopt=root=/dev/hda3 ro resume=/dev/hda2 noapic nolapic pci=assign-busses

---

