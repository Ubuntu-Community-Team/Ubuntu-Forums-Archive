---
title: "How to solve  the grub Error17"
date: 2009-04-27
forum: General Help
---

### Post by nst_chn on 2009-04-27
System:Ubuntu8.10
/boot is a dependent partition.

I search the Internet and follow the method.
run on Live-CD
In the terminate
```

sudo grub
find /boot/grub/stage1

```
Then return:Error 15 file not found.
I try many times for other file.I find a file and know the exact directry.
One result:Error 15 file not found.
In the menu.lst,it not contain "root(hdX,Y)"....
menu.lst:
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=68dbc408-6dc0-4e8c-a6b0-2d0318472cc8 ro locale=zh_CN

## default grub root device
## e.g. groot=(hd0,0)
# groot=d6d9b05e-99ad-4138-93cf-e8c717797ecd

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.10, kernel 2.6.27-14-generic
uuid        d6d9b05e-99ad-4138-93cf-e8c717797ecd
kernel        /vmlinuz-2.6.27-14-generic root=UUID=68dbc408-6dc0-4e8c-a6b0-2d0318472cc8 ro locale=zh_CN quiet splash 
initrd        /initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid        d6d9b05e-99ad-4138-93cf-e8c717797ecd
kernel        /vmlinuz-2.6.27-14-generic root=UUID=68dbc408-6dc0-4e8c-a6b0-2d0318472cc8 ro locale=zh_CN  single
initrd        /initrd.img-2.6.27-14-generic

title        Ubuntu 8.10, kernel 2.6.27-13-generic
uuid        d6d9b05e-99ad-4138-93cf-e8c717797ecd
kernel        /vmlinuz-2.6.27-13-generic root=UUID=68dbc408-6dc0-4e8c-a6b0-2d0318472cc8 ro locale=zh_CN quiet splash 
initrd        /initrd.img-2.6.27-13-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
uuid        d6d9b05e-99ad-4138-93cf-e8c717797ecd
kernel        /vmlinuz-2.6.27-13-generic root=UUID=68dbc408-6dc0-4e8c-a6b0-2d0318472cc8 ro locale=zh_CN  single
initrd        /initrd.img-2.6.27-13-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        d6d9b05e-99ad-4138-93cf-e8c717797ecd
kernel        /vmlinuz-2.6.27-7-generic root=UUID=68dbc408-6dc0-4e8c-a6b0-2d0318472cc8 ro locale=zh_CN quiet splash 
initrd        /initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        d6d9b05e-99ad-4138-93cf-e8c717797ecd
kernel        /vmlinuz-2.6.27-7-generic root=UUID=68dbc408-6dc0-4e8c-a6b0-2d0318472cc8 ro locale=zh_CN  single
initrd        /initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        d6d9b05e-99ad-4138-93cf-e8c717797ecd
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by sahabcse on 2009-04-27
Hi

Paste the o/p of sudo mount. For giving the mount we can identify the / partition mounted drive. After that we can easily fix the grub error. For fixing the grub error please follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)

---

### Post by nst_chn on 2009-04-27
But,
```

grub> find /boot/grub/stage1

Error 15: File not found


```
And can you tell me the specific solution,especially the code.
I am a freshman.Thanks.

---

### Post by sahabcse on 2009-04-27
If you installed a /boot partition, do
find /grub/stage1

---

### Post by nst_chn on 2009-04-27
Thank you very much.
return: (hd0,6)

I guess that I should shutdown the LiveCD and restart the computer now.
If the promble wasn't solved.
Please help me.

---

### Post by sahabcse on 2009-04-27
After that you have to run two steps. Pls follow below url for details

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by nst_chn on 2009-04-27
OK,everything goes well now.
Thank you very much!
In Chinese is:&#38750;&#24120;&#24863;&#35874;&#24744;&#65281;

---

