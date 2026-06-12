---
title: "How to change Grub menu resolution?"
date: 2006-01-20
forum: Desktop Environments
---

### Post by blackant on 2006-01-20
I am trying to change the resolution of the grub menu, which is before the splash screen.

But couldn't find a way to do so.
Can anyone offer some advise?

Thank you.

---

### Post by probe45 on 2006-01-20
To set a higher resolution in grub you need to add a " vga=xxx" line to your kernel line


possible values for that line are:
```

                640x480 800x600 1024x768 1280x1024 1600x1200
---------------+-------+-------+--------+---------+---------
256 (8 bit)    |  769     771     773       775       796
32,768 (15 bit)|  784     787     790       793       797
65,536 (16 bit)|  785     788     791       794       798
16.8M (24 bit) |  786     789     792       795       799

```

example:

title		Ubuntu, kernel 2.6.15-12-386 
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-12-386 root=/dev/hdb3 [COLOR="Red"]vga=791[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.15-12-386
savedefault
boot

Good luck :)

---

### Post by frodon on 2006-01-20
To change the GRUB image : [http://ubuntuforums.org/showthread.php?t=30341](http://ubuntuforums.org/showthread.php?t=30341)

---

### Post by probe45 on 2006-01-20
frodon no advence but by just changing the image you dont get a higher resolution in your bootloader. You need to set a pointer in your kernel line like descriped above. But setting another splashscreen is also nice todo ;)

---

### Post by frodon on 2006-01-20
yes, i just wanted to give a cool link, because when you want to do something with GRUB screen you're always interested in changing the GRUB image ;)

---

### Post by blackant on 2006-01-20
actually I wanted to change the resolution at the grub menu selection.
which is at the begining of the loading of linux... :P

is there anyway?

---

### Post by rysiek on 2006-03-03
nope. GRUB, as for now, only allows 640x480 resolution in the bootmenu.

Cheers
Mike

---

### Post by Railsbuntu on 2008-03-19
Hi,

I'd like to change the resolution of my command line. I use a non-gui sever. Each time I put the vga=xxx I get a "input not supported" on my LCD screen. Am I changing the correct thing?

---

### Post by syms on 2008-03-19
this is possible. and why u giving hard tips? u can easily configure grub with this :popcorn::
sudo apt-get install startupmanager
then u can configure grub and splash screen easy with this graphical tool ;)

---

### Post by x1a4 on 2008-03-19
> **Railsbuntu said:**
> I'd like to change the resolution of my command line. I use a non-gui sever. Each time I put the vga=xxx I get a "input not supported" on my LCD screen. Am I changing the correct thing?

You get that error because Gutsy does not have the VESA Frame Buffer enabled by default.  There are two things you can do: 

1) Use **vga=ask** and when prompted with a menu to choose a display size, select **scan**.  This will scan your display for all sorts of sizes and give you a menu with supported display sizes for you to choose from.  Most of the sizes you will get will make very lousy text. 

2) Enable **vesafb**.  Have a look at my HOWTO entitled [Fix console fonts in Gutsy]("http://hex1a4.net/xubuntu/howto.php?htid=02").  If you follow these instructions correctly you will be able to use higher resolutions. 

Note: The above will not change GRUB's menu size.  To pretty up GRUB you need to replace it with GRUB-gfxboot.  See [thread=705334]this thread[/thread] for more info.

---

### Post by Railsbuntu on 2008-03-20
Hi x1a4,

after following you tutorial, here is what I get:

with vga=ask
> 
Video adapter: VESA VGA
Mode: COLSxROWS
0 0F00 80x25
1 0F01 80x50
2 0F02 80x43
...
I tried mode 1,2,3 and 6, they don't fit well on the screen.

If I put vga=793, I still get the "input not suported". What's the correct value for 1280x1024 :confused:

---

### Post by x1a4 on 2008-03-20
> **Railsbuntu said:**
> 
*<snip>*

I tried mode 1,2,3 and 6, they don't fit well on the screen.

If I put vga=793, I still get the "input not suported". What's the correct value for 1280x1024 :confused:

The modes you get are the modes supported by your screen when vesafb is not enabled.  I know, they stink.  Enable the VESA Frame Buffer at which time '763' will work correctly.

---

### Post by Railsbuntu on 2008-03-20
Well I followed your tutorial, and that's what I get. How can I know if framebuffer is correctly setup?

EDIT: lsmod shows that both vesafb and fbcon are loaded, it also shows "0" under the used by column.

EDIT2: I tried vga=792 (1024x792) and it works. The problem is that it is not the native resolution of my LCD.

---

### Post by x1a4 on 2008-03-20
> **Railsbuntu said:**
> Well I followed your tutorial, and that's what I get. 

The HOWTO details what I have done to get things working, and it should work.  I've had positive feedback from Xubuntu, Ubuntu and Kubuntu users.  Make sure you follow all the steps in the same order as listed, then reboot. 

Did you restart your computer after making changes?  Try a different colour depth and/or resolution.  773, 775, 790, 793, ...  and see which one works with your screen. 

> EDIT: lsmod shows that both vesafb and fbcon are loaded, it also shows "0" under the used by column.

This is most likely an indicator of the problem.  My output is this: 

vesafb   9092    1
fbcon   41760  75

---

### Post by Railsbuntu on 2008-03-20
With vga=792, I get figures under the "used by" for both vesafb and fbcon.

I have read a lot of discussion threads about that issue, and it seems people still have problems with kernel 2.6.22-14 which I have.

---

### Post by x1a4 on 2008-03-20
Thanks for letting me know it works at a lower resolution.  I only have 19" (diagonal) screen and use 1024x768 resolution, so I never encountered this problem--it just worked for me, and the few people who used my instructions.  I'll make a note in my HOWTO that higher resolutions may not work.  Once again thanks.

EDIT: Are you going to replace GRUB with GRUB-gfxboot to pretty up your GRUB menu?  If so I'd appreciate it if you could let me know how it goes and any problems you encounter.  I want to do it myself and write a HOWTO on how to do it and can use all the info I can get my hands on.

---

### Post by Railsbuntu on 2008-03-21
Hi x1a4,

No I will not change grub. I just wanted to have the correct resolution on my screen, because sometimes I need to directly connect to my box and with crap resolution editing with vim is nearly impossible.

I have found people who managed to tweak fb to use 1280x1024, but they added more complicated lines to some file, I have asked them for more info, I am waiting for their answers.

Thx for helping me out :KS

---

### Post by excogitation on 2008-03-21
Since there are the Grub specialists here:

Isn't it possible to use Pretty Colors and a splashimage at the same time?
Or do I have to specify those colors (background/text) within the image -
and if so - how?

---

### Post by x1a4 on 2008-03-21
> **excogitation said:**
> Since there are the Grub specialists here:

GRUB specialists?  Not in this thread. :)

> Isn't it possible to use Pretty Colors and a splashimage at the same time?
Or do I have to specify those colors (background/text) within the image -
and if so - how?

In my experience you can either have colours or a background image.  If I have some time I'll google around and see if it's possible.  Most likely though, to have a prettier GRUB installing GRUB-gfxboot is the only way.

---

### Post by x1a4 on 2008-03-21
> **Railsbuntu said:**
> I just wanted to have the correct resolution on my screen, because sometimes I need to directly connect to my box and with crap resolution editing with vim is nearly impossible.

I know what you mean.  When I installed Gutsy that's the first thing I noticed and the first thing I changed.  I'm in a console all the time playing around, breaking then repairing my system. :lol:

> I have found people who managed to tweak fb to use 1280x1024, but they added more complicated lines to some file, I have asked them for more info, I am waiting for their answers.

Would you mind letting me know how to do it?

> Thx for helping me out :KS

You're welcome.  Be sure to mark this thread as solved.  (Click on 'Thread Tools' > 'Mark thread as solved')

---

### Post by Railsbuntu on 2008-03-22
This is what needs to be added:
> video=vesafb:1280x1024-24@60,mtrr vga=795
But I don't know where to put it, and the guy who posted that seems to be gone, I contacted him but got no reply up to now.

I just jumped in this thread, so I cannot mark it as solved.

---

### Post by excogitation on 2008-03-22
Put it in here:
/boot/grub/menu.lst

but I don't know if that: > video=vesafb:1280x1024-24@60,mtrr
will work.

---

