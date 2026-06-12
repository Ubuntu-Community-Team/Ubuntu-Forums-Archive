---
title: "Upgrade from 386 to 686 questions"
date: 2005-04-15
forum: Desktop Environments
---

### Post by pruett57 on 2005-04-15
Okay, so I upgraded from Warty to Hoary then updated to the 686 kernal.
Now if you look in Grum it shows the old 386, the upgraded 386 and now the new 686...so my question is I just leave them there and as we upgrade they stay?

Or is there a way to clean this up? Not only in Grub bc I assume it's just a delete the entries solution. Do I do an apt-get remove of the old kernals?

thanks

jp

here is my grub file

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by luca_linux on 2005-04-15
You can remove the old kernel packages and manually delete the old kernel entries in your grub.lst.

---

### Post by XDevHald on 2005-04-15
Someone might explain this better than me but I'll give it a shot.

the 386 is the main kernel/image for debian, so the image 386 image boot is the main image for your sys, that is why if you try to remove it, it'll take everything with it, the i686 is a step up from there and basically reconfigs it's self to the 386 and just makes it's self more useful the libs.

In all words as a n00b I am to the kernels and images is that, yes you will need to keep the 386 kernels and images as it is a requirement to keep them on there.


Let's see what the others have to say, in which might be more self explainitory than what I just gave to you.

---

### Post by az on 2005-04-15
You can do this from synaptic.  Just remoce the appropriate linux-image packages.  The point in leaving them there is to provide you with a bootable system if there is a problem with the new kernel.

---

### Post by jorgepeixoto on 2005-04-16
if you remove the apropriante linux packages for 386 in synaptic, you will unistall the old kernel, and it's entries will be automatically removed from grub. Your system will work with the new kernel. Easy, isn't it?
Just make shure you only remove the correct pakages.

---

### Post by Ubuntist on 2006-06-06
Using Synaptic as suggested removed most of my old kernals -- thanks!

I still have an old custom kernal that I'd like to get rid of.  Being custom-compiled, it does not show up in Synaptic.  How should I remove it?

---

### Post by jorgepeixoto on 2006-06-06
It depends on how you compiled it... If you did it "the debian way", you actually generated a debian package and installed it. It will show up in Synaptic (but I don't know what it's name will be, there is some time I don't compile a kernel in Ubuntu).

If you have compiled it "the wrong way", than I believe the only way is to 
delete the kernel in /boot
delete the modules (I believe they are in /lib/modules/name-of-the-kernel)
If you haven't delete the source from /usr/src, delete it
remove the entries in /boot/grub/menu.list

And don't compile a kernel "the wrong way" ever again...

And of course: before you delete things in /lib/modules and in /boot, be very careful, as you can make your system unbootable (you would have to use a livecd to fix it).

---

### Post by Ubuntist on 2006-06-07
Thanks, jorgepeixoto -- I must have compiled it "the Debian" way, because I did find a couple of kernel...custom entries in Synaptic after all.

---

### Post by Ubuntist on 2006-06-07
... [after a re-boot] I've removed the custom kernels and everything still seems to work fine (I was a little nervous that I might be removing the wrong thing in Synaptic)....  Thanks again!

---

