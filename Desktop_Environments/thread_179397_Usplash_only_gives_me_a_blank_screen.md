---
title: "Usplash only gives me a blank screen"
date: 2006-05-19
forum: Desktop Environments
---

### Post by konradsa on 2006-05-19
Hi,

After some automatic update recently (I don't know when exactly it happened), usplash does not work anymore for me. All I get when booting and shutting down is a blank screen. I am using usplash 0.2-4 on Dapper 6.06 (all up-to-date) on a HP dv1000 laptop (Intel GM915 graphics). Like I said, it always worked before and I did not touch anything that could break it.

---

### Post by konradsa on 2006-05-19
Btw, reinstalling usplash does not make a difference.

---

### Post by konradsa on 2006-05-20
*bump*

Does nobody have any idea?

---

### Post by mamato on 2006-05-20
do ```
sudo dpgk-reconfigure linux-image-(your kernel version)
``` It should fix it.

---

### Post by konradsa on 2006-05-20
[QUOTE=mamato]do ```
sudo dpgk-reconfigure linux-image-(your kernel version)
``` It should fix it.[/QUOTE]


Nope, unfortunately it did not do anything. 

](*,) 

For kicks, I also installed and configured kubuntu artwork for usplash, but still blank screen only.

Here is my menu.lst, in case that is the problem:
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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-22-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-22-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-22-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-22-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-22-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-22-386
boot

title		Ubuntu, kernel 2.6.15.7-ubuntu1-2.6.15-22.35-uv
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15.7-ubuntu1-2.6.15-22.35-uv root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15.7-ubuntu1-2.6.15-22.35-uv
savedefault
boot

title		Ubuntu, kernel 2.6.15.7-ubuntu1-2.6.15-22.35-uv (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15.7-ubuntu1-2.6.15-22.35-uv root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15.7-ubuntu1-2.6.15-22.35-uv
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by konradsa on 2006-05-20
Ok,

I found out some more information. I am using a custom kernel

kernel 2.6.15.7-ubuntu1-2.6.15-22.35-uv

with an undervolt patch. The kernel works perfectly, but no usplash.

However, when I boot the standard 

kernel 2.6.15-22-386

usplash works. Did I misconfigure the kernel maybe or what went wrong?

---

### Post by konradsa on 2006-05-20
Ok,

I recompiled my kernel now, with all standard options, Processor selected Pentium M, and the Ubuntu undervolt patch from 

[http://linux-phc.sourceforge.net/](http://linux-phc.sourceforge.net/)

Again, usplash does not work. Can anyone confirm that usplash does not work correctly with the 2.6.15.7 kernel sources from the ubuntu repository, or may this problem be related to the undervolt patch? I did not have this problem with the same patch on the 2.6.15.6 sources.

---

### Post by o_fortuna on 2006-05-20
Usplash must be compiled into the kernel, if I'm correct. I personally have no clue how to do this though, sorry. :(

If it were me, I'd just start "sudo dpkg-reconfigure" any linux packages I could, including usplash, but I don't know if it will work.

---

### Post by tigrux on 2006-05-20
[QUOTE=konradsa]Hi,

After some automatic update recently (I don't know when exactly it happened), usplash does not work anymore for me. All I get when booting and shutting down is a blank screen. I am using usplash 0.2-4 on Dapper 6.06 (all up-to-date) on a HP dv1000 laptop (Intel GM915 graphics). Like I said, it always worked before and I did not touch anything that could break it.[/QUOTE]

I had the same problem and I realized I was forgetting this in the config:
```

CONFIG_FB_VESA=y

```

Also, be sure fbcon is built-in

---

### Post by Potto007 on 2006-05-23
[QUOTE=konradsa]
Again, usplash does not work. Can anyone confirm that usplash does not work correctly with the 2.6.15.7 kernel sources from the ubuntu repository, or may this problem be related to the undervolt patch? I did not have this problem with the same patch on the 2.6.15.6 sources.[/QUOTE]

I can confirm that usplash does **not** work with my custom kernels after an update about a week or so ago. Unfortunately, I didn't note which day it was... I assumed for several days that it was a problem with the usplash package, and that it would be fixed -- it happened like a day or so after that UGLY splash was implemented and then reverted.

Usplash works fine with my Ubuntu kernel image, but that is unfortunately 2.6.15-19-386, the latest I can get that works with my SATA system. I have reinstalled usplash, to no avail; and the compile options were configured properly.

-Paul

---

### Post by konradsa on 2006-05-23
[QUOTE=Potto007]I can confirm that usplash does **not** work with my custom kernels after an update about a week or so ago. Unfortunately, I didn't note which day it was... I assumed for several days that it was a problem with the usplash package, and that it would be fixed -- it happened like a day or so after that UGLY splash was implemented and then reverted.

Usplash works fine with my Ubuntu kernel image, but that is unfortunately 2.6.15-19-386, the latest I can get that works with my SATA system. I have reinstalled usplash, to no avail; and the compile options were configured properly.

-Paul[/QUOTE]


Thanks Paul for confirming this problem,

maybe we should submit a bug report, does anybody know how to do that?

-- Sascha

---

### Post by thasheep on 2006-05-23
I had the same problem (w/ 2.6.17-rc*) but it was fixed when I downgraded to usplash-0.1* (pre crap artwork). If you can't find it in /var/cache/apt/archives then you can get the i386 version [from me](http://213.100.40.206/ubuntu/usplash_0.1-36_i386.deb).
After reading [the changelog](http://changelogs.ubuntu.com/changelogs/pool/main/u/usplash/usplash_0.2-4/changelog), I saw that version 0.2-3 started loading the framebuffer modules differently and now uses the script /usr/share/initramfs-tools/scripts/init-top/framebuffer (from initramfs-tools) to do that. This shouldn't pose problem, but I haven't worked out how to make it work yet. Maybe try making sure you enable vesafb, vga16fb and fbcon as modules in the in the kernel config. Also, try adding vga=791 (or whatever you like) to you kernel line in grub

---

### Post by konradsa on 2006-05-23
[QUOTE=thasheep]I had the same problem (w/ 2.6.17-rc*) but it was fixed when I downgraded to usplash-0.1* (pre crap artwork). If you can't find it in /var/cache/apt/archives then you can get the i386 version [from me](http://213.100.40.206/ubuntu/usplash_0.1-36_i386.deb).
After reading [the changelog](http://changelogs.ubuntu.com/changelogs/pool/main/u/usplash/usplash_0.2-4/changelog), I saw that version 0.2-3 started loading the framebuffer modules differently and now uses the script /usr/share/initramfs-tools/scripts/init-top/framebuffer (from initramfs-tools) to do that. This shouldn't pose problem, but I haven't worked out how to make it work yet. Maybe try making sure you enable vesafb, vga16fb and fbcon as modules in the in the kernel config. Also, try adding vga=791 (or whatever you like) to you kernel line in grub[/QUOTE]

Thanks, the downgrade actually helped. I will be waiting for the final Dapper release now before messing around with it any further. Hopefully they will fix it until then.

Sascha

---

### Post by leech on 2006-05-23
Firstly, the problem with submitting a bug report on a custom kernel is that it has nothing to do with the Ubuntu itself.  They can try to apply the undervolting patch to an official kernel, but I'm not sure if/when that will happen.

Secondly, did you make sure that the proper modules, etc are built into your custom kernel?  What I would have personally done to create the custom kernel is to first off, get the proper .config file from the kernel you're basing the patched one on.  For example in /usr/src/linux-headers-2.6.15-23-k7/.config.  Just copy that .config file over to where the source tree is, and it's already configured.  Then apply the undervolting patch.  Change the .config file where the undervolting is turned on, and you're good to go.

Also, not sure if you did this, but create it with the debian utilities for creating kernel packages.  That way Grub will automatically be updated in the proper way.

Usplash does NOT require recompilation of the kernel.  That was the whole point behind Usplash, is that it is a userland only utility for doing bootsplashes, unlike the Gentoo, Suse way etc.

Leech

---

### Post by konradsa on 2006-05-23
Well,

I am not using a vanilla kernel, but I am compiling my kernel from the linux-source-2.6.15-23.35 package. As far as I understood, Ubuntu patches and config is already in there. Please correct me if I am mistaken.

And I doubt the problem lies with the undervolt patch, but I think that the 2.6.15.7 version from the Ubuntu repository in general has this problem with usplash. As I mentioned above, the patch did not cause such problems on the older kernel versions and I doubt it does now.

---

### Post by Potto007 on 2006-05-23
[QUOTE=leech]Firstly, the problem with submitting a bug report on a custom kernel is that it has nothing to do with the Ubuntu itself.  They can try to apply the undervolting patch to an official kernel, but I'm not sure if/when that will happen.

Secondly, did you make sure that the proper modules, etc are built into your custom kernel?  What I would have personally done to create the custom kernel is to first off, get the proper .config file from the kernel you're basing the patched one on.  For example in /usr/src/linux-headers-2.6.15-23-k7/.config.  Just copy that .config file over to where the source tree is, and it's already configured.  Then apply the undervolting patch.  Change the .config file where the undervolting is turned on, and you're good to go.

Also, not sure if you did this, but create it with the debian utilities for creating kernel packages.  That way Grub will automatically be updated in the proper way.

[/QUOTE]

That is why I haven't posted a bug report.... I was afraid that since it was using source from outside the Ubuntu tree, it would not be considered. However, in response to your second paragraph: I copied the config from the previous kernel image to .config in my /usr/src/linux directory.... and I used make-kpkg to build the kernel image and headers.... then installed using dpkg -i .... as one should do in a Debian distro.

I am guessing that it does have to do with a different use of the framebuffer that wasn't in my config... although that is strange to me since I used the Ubuntu config as a start. Whatever... I guess I'll just use the old version of Usplash.

-Paul

---

### Post by dooooomi on 2006-05-24
Same problem here. Even when I build a vanilla 2.6.16 kernel using *exactly* the same config as the latest Ubuntu kernel, and build it with make-kpkg, usplash doesn't work, all I get is blank screen.

And actually I do consider it a bug in Ubuntu when it causes problems like this with a vanilla kernel. So, does anyone know how to fix it?

---

### Post by Pausanias on 2006-05-25
I will try to replicate this problem with Dapper's own 2.6.15 kernel and post a bug report if I get the same issue.

---

### Post by Pausanias on 2006-05-26
OK, I solved the problem, at least for my setup. The solution was to disable the following options

CONFIG_FB_NVIDIA
CONFIG_FB_VGA16

and to compile the following two modules directly into the kernel:


CONFIG_FRAMEBUFFER_CONSOLE
CONFIG_FB_VESA

If you have an nVidia card this may work too. A sweet side-effect of this is that my framebuffers are no longer messed up after resuming from suspend.

---

### Post by dooooomi on 2006-05-26
Ok, problem found. When building a vanilla kernel with make-kpkg, the initrd does not include the module fbcon. Without that module, usplash can't work.

I added fbcon to /etc/mkinitramfs/modules, rebuilt the kernel, et voilà, usplash worked. The image was slightly distorted (wrong aspect ratio), because the Ubuntu kernel uses a screen resolution different from the vanilla kernel, but apart from that it was fine.

Do you think this qualifies as a bug in Ubuntu? This affects everyone who wants to build his own kernel, doesn't it?

[edit]
Ok, Pausanias, you were faster ;)
Of course building fbcon directly into the kernel will also work, but I still think that should not be neccessary, and it should be in the initrd by default.
[/edit]

---

### Post by konradsa on 2006-05-28
> **dooooomi]Ok, problem found. When building a vanilla kernel with make-kpkg, the initrd does not include the module fbcon. Without that module, usplash can't work.

I added fbcon to /etc/mkinitramfs/modules, rebuilt the kernel, et voilà, usplash worked. The image was slightly distorted (wrong aspect ratio), because the Ubuntu kernel uses a screen resolution different from the vanilla kernel, but apart from that it was fine.

Do you think this qualifies as a bug in Ubuntu? This affects everyone who wants to build his own kernel, doesn't it?

[edit]
Ok, Pausanias, you were faster  said:**
> 

Yes, I think it qualifies as a bug, especially since the older kernel versions obviously included the right options by default. Maybe it is just an omission in the current version.

UPDATE
That did not fix my problem though! ](*,) 
All it shows me upon booting is:
Loading the kernel...
0 <--- A zero

And then it boots normally in text mode, but no usplash screen! :-k

---

### Post by Potto007 on 2006-05-30
[QUOTE=konradsa]Yes, I think it qualifies as a bug, especially since the older kernel versions obviously included the right options by default. Maybe it is just an omission in the current version.

UPDATE
That did not fix my problem though! ](*,) 
All it shows me upon booting is:
Loading the kernel...
0 <--- A zero

And then it boots normally in text mode, but no usplash screen! :-k[/QUOTE]

The same thing happened to me, zero and all... until I added back VGA16FB into my config. Once I did that, along with the other aforementioned options (framebuffer_console and fb_vesa) selected, I got back my Usplash. Just got it working this morning. -- What a pain for a pretty little screen I only see for about 30 seconds!  :)

Hope you guys get it working.... 

-Paul

---

### Post by konradsa on 2006-05-30
[QUOTE=Potto007]The same thing happened to me, zero and all... until I added back VGA16FB into my config. Once I did that, along with the other aforementioned options (framebuffer_console and fb_vesa) selected, I got back my Usplash. Just got it working this morning. -- What a pain for a pretty little screen I only see for about 30 seconds!  :)

Hope you guys get it working.... 

-Paul[/QUOTE]


Dude,

you are the man!

CONFIG_FB_VGA16
CONFIG_FRAMEBUFFER_CONSOLE
CONFIG_FB_VESA

is the magic combination you need to get this baby to work. Thanks to everyone that helped!

---

### Post by Jasman on 2006-05-30
[quote=dooooomi]
I added fbcon to /etc/mkinitramfs/modules, rebuilt the kernel, et voilà, usplash worked. 
[/quote]

This and the above suggestions for compiling into the kernel worked for me. Thanks.

---

### Post by Potto007 on 2006-05-31
[QUOTE=konradsa]Dude,

you are the man!

CONFIG_FB_VGA16
CONFIG_FRAMEBUFFER_CONSOLE
CONFIG_FB_VESA

is the magic combination you need to get this baby to work. Thanks to everyone that helped![/QUOTE]

Lol! :D  I'm glad it worked for you too.... I know you were probably just as frustrated as I was!

-Paul

---

### Post by Toxicity999 on 2006-05-31
Just go with splashy or something... I mean if your into a custom kernel and getting that deep into things splashy might be for you it handles things alot better and no kenrnel patching required that I know of (wewt.)


Edit: yea... just skimmed through the rest of the thread... sorry should have done that before hand ;) still the advice applies.

---

