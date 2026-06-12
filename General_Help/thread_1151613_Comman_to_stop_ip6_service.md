---
title: "Comman to stop ip6 service"
date: 2009-05-07
forum: General Help
---

### Post by colau on 2009-05-07
Hi,
Is there any command to stop the ipv6 service?

---

### Post by rob1408 on 2009-05-07
I assume you mean ipv6.  If you are using a recent kernel (2.6.29) you can try adding 'ipv6.disable=1' to the grub kernel command line.  Open a terminal and type 'Sudo gedit /boot/grub/menu.lst' then look for your kernel line.

---

### Post by colau on 2009-05-07
> **rob1408 said:**
> I assume you mean ipv6.  If you are using a recent kernel (2.6.29) you can try adding 'ipv6.disable=1' to the grub kernel command line.  Open a terminal and type 'Sudo gedit /boot/grub/menu.lst' then look for your kernel line.

Got nothing in the kernel line.
[html]
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		cb7c4f7d-45b6-4011-8b13-a47f471401f2
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cb7c4f7d-45b6-4011-8b13-a47f471401f2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
[/html]

---

### Post by rob1408 on 2009-05-07
It looks like you're running 2.6.28, this only works with 2.6.29.

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cb7c4f7d-45b6-4011-8b13-a47f471401f2 ro quiet splash 

That is the line you add ipv6.disable=1 to.  But you'll need to update your Kernel to do this.  Is your connection noticeably slower ?  If not I wouldn't bother.

---

### Post by colau on 2009-05-07
> **rob1408 said:**
> It looks like you're running 2.6.28, this only works with 2.6.29.

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cb7c4f7d-45b6-4011-8b13-a47f471401f2 ro quiet splash 

That is the line you add ipv6.disable=1 to.  But you'll need to update your Kernel to do this.  Is your connection noticeably slower ?  If not I wouldn't bother.

Should I add like this?

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cb7c4f7d-45b6-4011-8b13-a47f471401f2 ro quiet splash ipv6.disable=1

It is 2.6.28.
Browsing is comparatively slower.
And every now and then it stops loading the page.

Then ping [www.google.com](www.google.com) from the terminal says
ping: unknown host [www.google.com](www.google.com)

Then I re-adjust the pppoe connection running pppoeconf.

---

### Post by rob1408 on 2009-05-07
Yes but you'll have to update your kernel from 2.6.28 to 2.6.29.

---

### Post by colau on 2009-05-07
> **rob1408 said:**
> Yes but you'll have to update your kernel from 2.6.28 to 2.6.29.
No other way to stop ipv6 service?
And can you tell why does the Networkmanager Applet show the cross sign all the time though I am browsing?

And what is the command to update the kernel?
Will it work?
[html]
aptitude install kernel
[/html]

---

### Post by rob1408 on 2009-05-07
Unfortunately I'm unaware of any other way to globally disable ipv6 on Jaunty.  You can disable it on Firefox although that will only help regarding browsing.

 [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) 

2.6.29 is towards the bottom.  It comes in .deb form and you will need the linux-image file for your architecture (i386 or 64).

---

### Post by colau on 2009-05-07
> **rob1408 said:**
> Unfortunately I'm unaware of any other way to globally disable ipv6 on Jaunty.  You can disable it on Firefox although that will only help regarding browsing.

 [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) 

2.6.29 is towards the bottom.  It comes in .deb form and you will need the linux-image file for your architecture (i386 or 64).
I downloaded linux-image-2.6.29-020629-generic_2.6.29-020629_i386.deb
Will this work?
dpkg -i linux-image-2.6.29-020629-generic_2.6.29-020629_i386.deb

And would you please tell how to disable ipv6 from firefox?

---

### Post by Brandon Williams on 2009-05-07
Please use the search function before posting!

[This thread](http://ubuntuforums.org/showthread.php?t=1139386) already has discussion of disabling ipv6 with specific suggestions and links to other sources of information.

---

