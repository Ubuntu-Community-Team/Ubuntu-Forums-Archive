---
title: "Grub splash screen gone after new kernel"
date: 2006-01-08
forum: General Help
---

### Post by cb951303 on 2006-01-08
Hello, this is my first post
I've been using Slackware for 5 years and now I'm migrating to Ubuntu for package management :) I hope it will suit my needs :P

Anyway here is my problem:
After installing Ubuntu, I did a kernel compile(2.6.12) with make-kpgk, and everything went OK. I'm also sure that I enabled the console framebuffer (statically) and I also tested it with "vga=0x318" option in menu.lst. Framebuffer works great but there is no more the beautiful "Ubuntu splash screen with bar". I checked the menu.lst and I'm sure that there is a "splash" option. 
Any help would be appreciated.

PS: Sorry for my bad english...

Here is my menu.lst in case you need it:

```

default		0
timeout		10
#hiddenmenu

title		Ubuntu, kernel 2.6.12.1 Default 
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/sda3 ro quiet splash vga=0x318
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.12.1 Default (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz root=/dev/sda3 ro single
initrd		/boot/initrd.img
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous 
root		(hd0,2)
kernel		/boot/vmlinuz.old root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img.old
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic Previous (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz.old root=/dev/sda3 ro single
initrd		/boot/initrd.img.old
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-9-amd64-generic
boot

title		Ubuntu, kernel 2.6.12.1 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12.1 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12.1
savedefault
boot

title		Ubuntu, kernel 2.6.12.1 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12.1 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12.1
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
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by Thirsteh on 2006-01-08
I know this is not very helpful but just thought I'd say;

You really don't need to do your own kernel compiles in Ubuntu, the kernels that come with the distribution are as topnotch as precompiled kernels can be.

---

### Post by Azriphale on 2006-01-08
And its a whole lot easier to not compile your own...
The Ubuntu team keeps the kernelup to date with all the latest security fixes as soon as they become available, and then they immediately provide the updates to the users. 

I have never used usplash, except with Ubuntu, and I have never compiled a kernel in Ubuntu, so I'm afraid I can't help you.

But you may be assured that there are no security flaws in the default kernel. Or, at least, they get fixed as soon as they are found.

---

### Post by cb951303 on 2006-01-08
First of all thanks for replys
but I think you miss the point here.
Compiling my own kernel isn't about security!
First of all security patches are applied directly to the source. As long as I download the source from Ubuntu repository I get all the security patches.
(This is what I did)

Also compiling a custom kernel is definitly needed. I'm sorry but there is no "as topnotch as precompiled kernels can be". When I did a "lsmod" with the generic kernel, I saw at least 12 modules that aren't needed. So, why should I keep them ?
The idea behind a generic kernel is to make it work in every hardware. My hardware isn't every hardware so ... :D

> And its a whole lot easier to not compile your own... If I wanted to be easier I would go with windows :D 

Also kernel compiling isn't hard at all, with a basic knowledge of linux everyone can  do it(There is a very good doc in wiki too)

Anyway, please no offense, these are my thoughts also the ubuntu splash has nothing to do with my kernel compiliation. I'm pretty sure that I should only turn something on and that's all, so if anyone has an idea please let me know

peace!

---

### Post by Azriphale on 2006-01-08
Sorry I can't help.

I'm not saying I haven't compiled my own kernel, I have. Just not in Ubuntu. I've just become lazy lately :) 
I mean't that last time I compiled a kernel, I was using a distro without any fancy splash things.

I may actually sake a shot at it again, because about all the unneeded stuff, I agree with you. But I'm going back to work tomorrow. So I won't have time. Then its back to university and there's even less time. :(

---

### Post by Kaijec Torsf on 2006-01-10
HHAHAHAHahaAHhahaa...... that was funny,

have the same problem though, not as funny....
wonder whats the deal? all my options are correct (I think, most likely not)

however I noticed that in your config line vga= (whatever) the first digit is 0...

mebbe that could be it? hrmmmmm.... :confused:

---

### Post by numer on 2006-01-10
I was going to post about the same thing...  I did not build my own kernel; however, I added a VGA=791 to my kernel parameters because whatever the default resolution for the splash is, it looks crappy on my laptop.  The splash went away...

---

### Post by cb951303 on 2006-01-13
[QUOTE=Kaijec Torsf]HHAHAHAHahaAHhahaa...... that was funny,

have the same problem though, not as funny....
wonder whats the deal? all my options are correct (I think, most likely not)

however I noticed that in your config line vga= (whatever) the first digit is 0...

mebbe that could be it? hrmmmmm.... :confused:[/QUOTE]
the 0x means that's a hexadecimal number. It's not the problem. 
I think i should reinstall usplash and also it's said that usplash installs the image files to initrd image. As long as I don't use an initrd(I don't anymore) I can't use usplash...

:/

---

### Post by Azriphale on 2006-01-13
Wait. I read somewhere recently that the vga option sets it to a certain resolution _text console_.

what happens if you boot without the vga= option at all?

---

