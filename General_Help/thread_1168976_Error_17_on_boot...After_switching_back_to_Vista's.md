---
title: "Error 17 on boot...After switching back to Vista's boot manager.  PLEASE HELP!!"
date: 2009-05-24
forum: General Help
---

### Post by rrogerstx on 2009-05-24
For whatever reason I decided to switch back to vistas boot manager on my dual boot Ubuntu 9.04/Vista system.  

I ran EasyBCD 1.7.2 in Vista and enabled Vistas boot manager.
Then I added the NeoGrub Bootloader and added the Ubuntu boot options to the config file.

Now when I boot I get error 17 if I select any of the Ubuntu boot options.

Here is a copy of my NeoGrub configuration.

# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# [http://neosmart.net/wiki/display/EBCD](http://neosmart.net/wiki/display/EBCD)


title		Ubuntu 9.04, kernel 2.6.28-11-generic

uuid		33e7e061-8f42-4a4a-b54d-3f5859858dc9

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=33e7e061-8f42-4a4a-b54d-3f5859858dc9 ro quiet splash 

initrd		/boot/initrd.img-2.6.28-11-generic

quiet



title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)

uuid		33e7e061-8f42-4a4a-b54d-3f5859858dc9

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=33e7e061-8f42-4a4a-b54d-3f5859858dc9 ro  single

initrd		/boot/initrd.img-2.6.28-11-generic



title		Ubuntu 9.04, memtest86+

uuid		33e7e061-8f42-4a4a-b54d-3f5859858dc9

kernel		/boot/memtest86+.bin

quiet

At this point I don't care if I get vista's boot manager to work or switch back to ubuntu's boot manager.  I just want to be able to get back to my ubuntu desktop again.  So help fixing vista's boot loader or re-enabling ubuntu's boot loader....either will work.

---

