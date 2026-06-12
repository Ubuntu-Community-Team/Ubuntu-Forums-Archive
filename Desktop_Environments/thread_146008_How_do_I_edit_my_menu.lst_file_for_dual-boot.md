---
title: "How do I edit my menu.lst file for dual-boot?"
date: 2006-03-17
forum: Desktop Environments
---

### Post by ardchoille on 2006-03-17
I have a second hard drive and like to tinker with different distros and was wondering about something - the 2nd hd will probably have several distros installed, each one installed over the previous one. I was looking at the /boot/grub/menu.lst and, if I am right, I should be able to install a distro as a dual-boot and just not install the MBR portion of it. My /boot/grub/menu.lst file has the following:

```

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 vga=791 ro quiet
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

```

So, if I am thinking correctly, I can just install a distro as dual-boot and add some lines to my current menu.lst file.. something like:

```

title		Fedora Core 5
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 vga=791 ro quiet
initrd		/boot/initrd.img-2.6.15-10-386
savedefault
boot

```

If this is true, then all I really need to know is the proper entries for the below red text:
Line 2: root		[COLOR="Red"](hd0,0)[/COLOR]
Line 3: kernel		[COLOR="Red"]/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2[/COLOR] vga=791 ro quiet
Line 4: initrd		[COLOR="Red"]/boot/initrd.img-2.6.15-10-386[/COLOR]

Am I right about this? If so, how do I find out what the above text in red should be? If I'm not right about this, what is the best way to add a dual-boot distro without installing the MBR stuff?

---

### Post by Blairboy on 2006-03-17
This might help you out [http://www.openbg.net/sto/os/xml/grub.html#menu](http://www.openbg.net/sto/os/xml/grub.html#menu)

---

### Post by ardchoille on 2006-03-17
Yes! That is very good info. Thanks for posting it :)
So, I was headed in the right direction, just need to tweak a few paths.

---

