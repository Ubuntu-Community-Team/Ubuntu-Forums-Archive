---
title: "How to flash BIOS?"
date: 2011-03-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vladyaro on 2011-03-19
How would someone go about flashing the BIOS on a dell studio 1536? I was going to try this: 
[http://linuxchronicles.wordpress.com/2010/06/22/flashing-a-dell-bios-in-ubuntu-or-debian/](http://linuxchronicles.wordpress.com/2010/06/22/flashing-a-dell-bios-in-ubuntu-or-debian/)
But i am not sure that it will work correctly. So if that will work please tell me and if it wont then please give me another solution. 
Thank you. :popcorn:

---

### Post by CloseYetFar on 2011-03-19
I just flashed my ubuntu netbook with freedos usb image. Updating Bios in a Dos environment. 

Download and extract FreeDos from here:
[http://derek.chezmarcotte.ca/wp-content/uploads/2009/08/FreeDOS-1.0-USB-Boot.img.bz2](http://derek.chezmarcotte.ca/wp-content/uploads/2009/08/FreeDOS-1.0-USB-Boot.img.bz2)

Get an empty USB flash drive and apply the image with "dd if=FreeDOS-1.0-USB-Boot.img of=/dev/sdx" the x being what ever letter the drive mounted as, it was sdb for me. 

YOU CANT use dd with the flash drive mounted, so unmount it.

After dd is finished mount the flash drive and copy the bios update files to it and restart booting from the flash drive. Run the flash program from within freedos.

---

### Post by CoolJohnB on 2011-03-20
I flashed my BIOS by using an XP boot disk (It booted to the DOS command line) and having the BIOS flash on a USB flash drive, XP recognised this as Drive C: and I just ran the program from there, worked great!

---

