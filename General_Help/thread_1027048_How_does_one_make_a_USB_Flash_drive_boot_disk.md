---
title: "How does one make a USB Flash drive boot disk?"
date: 2008-12-31
forum: General Help
---

### Post by jlh68 on 2008-12-31
I have followed the various procedures to make a flash drive boot disk without any of them producing a viable unit.

Does anyone have any real instructions on how to do it?

I have used a 2GB Kingston DataTraveler, a recently downloades ISO file burned to a CD.  I used the System>Administration>Create a USB Startup disk on my Ubuntu 8.10 desktop.  The flash drive says it is formated as MSDOS, which is VFAT.

---

### Post by dcstar on 2008-12-31
> **jlh68 said:**
> I have followed the various procedures to make a flash drive boot disk without any of them producing a viable unit.

Does anyone have any real instructions on how to do it?

I have used a 2GB Kingston DataTraveler, a recently downloades ISO file burned to a CD.  I used the System>Administration>Create a USB Startup disk on my Ubuntu 8.10 desktop.  The flash drive says it is formated as MSDOS, which is VFAT.

Some Flash drives just cannot be made boot devices because they won't allow data to be written to the place the BIOS boot loader starts with.

I once had a drive that I just could not get to be a boot device, I got another (newer) drive and it worked perfectly with the same instructions. Subsequently every other drive I had got has been able to be made bootable.

Try another drive.

---

### Post by Sunspore on 2008-12-31
Hi, you might want to refer to here for the answer.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)


:popcorn:

---

### Post by eBoxNet on 2008-12-31
> **jlh68 said:**
> I have followed the various procedures to make a flash drive boot disk without any of them producing a viable unit.

Does anyone have any real instructions on how to do it?

I have used a 2GB Kingston DataTraveler, a recently downloades ISO file burned to a CD.  I used the System>Administration>Create a USB Startup disk on my Ubuntu 8.10 desktop.  The flash drive says it is formated as MSDOS, which is VFAT.

i am using 3 Kingston DataTraveler flash drives to boot various computers on my network.

with one of those i had the same problem as you,i manage to solve this problem by using UNetbootin to create the ubuntu bootable flash drive.

its very easy and fast.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

i forced to use windows version but linux version should work fine of course.

hope this helps. ;)

"i also had another probelm when i was trying to make it through System>Administration>Create a USB Startup disk i was getting a  shell command only when i was booting from my flash drive"

---

### Post by thomas228 on 2008-12-31
> **eBoxNet said:**
> i am using 3 Kingston DataTraveler flash drives to boot various computers on my network.

with one of those i had the same problem as you,i manage to solve this problem by using UNetbootin to create the ubuntu bootable flash drive.

its very easy and fast.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

i forced to use windows version but linux version should work fine of course.

hope this helps. ;)

"i also had another probelm when i was trying to make it through System>Administration>Create a USB Startup disk i was getting a  shell command only when i was booting from my flash drive"

Hi

The unibootin method worked for me to create a liveusb from the iso download in both 8.04 and 8.10 on 2GB thumbs

For a viable thumb installation I used an 8GB thumb using 2 GB as swap an 6GB for 8.04.
The threads I used were [http://ubuntuforums.org/showthread.php?t=1017566&page=2](http://ubuntuforums.org/showthread.php?t=1017566&page=2) post #14 and [http://ubuntuforums.org/showthread.php?t=1021772](http://ubuntuforums.org/showthread.php?t=1021772)

Works great

Good luck 

TOM

---

