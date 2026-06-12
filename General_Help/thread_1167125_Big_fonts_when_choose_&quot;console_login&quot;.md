---
title: "Big fonts when choose &quot;console login&quot;"
date: 2009-05-22
forum: General Help
---

### Post by paulocr on 2009-05-22
Hello,

I have a done a fresh install out of the cd for Ubunty Jaunty so it has detected all my video settings, etc. The GUI works perfect with GNOME and KDE however if when I am in the login screen I choose Console Login I will get the suppossed console but the fonts are huge and can not be used.
I have faced these problems in the past with other Ubuntu versions and I tend to think that is caused by xorg.conf which I have customized in the previous versions but in this case I have not changed it so I find it strange. I have never been able to fix this.

do you have any ideas?

Thanks,

Paulo

---

### Post by wanchai on 2009-05-23
I am not 100% sure whether I understand what you mean by "choose Console Login" when you are at the logon screen. Will that get you into the same console as pressing CTRL-ALT F1 when you are in Gnome? (CTRL-ALT F7 will get you back.) If that's the case, here is how I changed the resolution of the console on my laptops:

sudo gedit /etc/usplash.conf
add two lines:
xres=1024
yres=768

sudo gedit /etc/modprobe.d/blacklist-framebuffer
then comment out the line: blacklist vesafb

sudo gedit /etc/initramfs-tools/modules
At the end of the file, add these two separate lines :

fbcon
vesafb

sudo update-initramfs -u


Finally, open your menu.lst file:

sudo gedit /boot/grub/menu.lst

add vga=791 (to have a 1024*768 resolution) to the kernel lines as well as to defoptions

On my desktop everything is the same except that I have xres=1280 and yres=1024.
Whenever you change /etc/usplash.conf you need to run update-initramfs again.


P.S. What I'm talking about here has nothing to do with xorg.conf, so may I missed your point.

---

### Post by paulocr on 2009-05-26
Hi wanchai,

Thanks for your response.
The Console Login is available in Ubuntu's login screen when you click on Menu but only with KDM, I hadn't noticed it is not available in GDM.

I did what you suggested but the issue persists.

---

### Post by wanchai on 2009-05-26
Hello Paulo,

Sorry, I don't have KDE, so I can't help you with that.

My thought was that maybe this console logon that you mentioned drops you back to the same console that you would get when you hit CTRL-ALT F1 or F2 or F3, etc. This feature is available in various Linux versions regardless of any graphical desktop. It's available even if you don't install any X server. Can you confirm whether this console is the same as the one you're talking about?

And were you able to change the resolution of this CTRL-ALT-F1 console?

---

### Post by Girl™ on 2009-05-26
> **wanchai said:**
> If that's the case, here is how I changed the resolution of the console on my laptops: [...]


I've been able to do this only by having *vga=791* in menu.lst. I'm not sure you actually need all the rest.

---

### Post by paulocr on 2009-05-26
This has not solved the issue.
Have you placed vga=791 in two different places in your menu.lst?

Wanchai said I should put it in the kernel options as well as the defoptions. I only placed it in one place as: defoptions=vga=791

---

### Post by paulocr on 2009-05-26
I forgot to respond to wanchai's question. The steps provided did not fix the ALT+F1 console

---

### Post by wanchai on 2009-05-26
Girl™, you may be right. That's a typical thing, I'm trying to achieve something, doing many steps, then after I get the result, I rarely go back to find out what is the minimum set of steps needed to achieve this goal.

Paulo, having the vga=791 on the kernel line is the one that counts. The default options are used only when menu.lst is rebuilt after an upgrade with a new kernel. So, if you put this option only on the kernel line, and not in the defoptions, it will disappear after the next kernel upgrade.

Here is what I have, you may also have splash and/or quiet on the kernel line, but they are independent of the vga option:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=vga=791

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            c883a218-858e-4065-a2bb-db7bfb9d9faa
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=c883a218-858e-4065-a2bb-db7bfb9d9faa ro vga=791
initrd          /boot/initrd.img-2.6.28-11-generic
quiet
```

---

### Post by paulocr on 2009-05-28
Thanks for posting your menu.lst file wanchai!!

I hadn't quite understood where I needed to add the lines. I did get an error about a video more unavailable and I got a list of available modes so I chose 311 and it worked like a charm.

Thanks a lot to both of you!!

---

### Post by paulocr on 2009-05-28
It was not 311 actually but "0x0305"

Thanks!!

---

### Post by wanchai on 2009-05-28
Glad that it now worked for you. Apparently you can also use vga=ask, then you'd always get a list to choose from. 

Here is a list of the numbers in hex, but you can also use the corresponding decimal values:

```

    | 640x480  800x600  1024x768 1280x1024
----+-------------------------------------
256 |  0x301    0x303    0x305    0x307   
32k |  0x310    0x313    0x316    0x319   
64k |  0x311    0x314    0x317    0x31A   
16M |  0x312    0x315    0x318    0x31B   

```

source: [http://www.mjmwired.net/kernel/Documentation/fb/vesafb.txt](http://www.mjmwired.net/kernel/Documentation/fb/vesafb.txt)

---

