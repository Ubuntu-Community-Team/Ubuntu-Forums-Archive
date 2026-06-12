---
title: "how can i change the resolution of my bootsplash???"
date: 2006-06-01
forum: Desktop Environments
---

### Post by chokes on 2006-06-01
hi all
since the last RC i cant have my bootsplash at 1280x1024 so... where can i change this? tanx;)

---

### Post by Anduu on 2006-06-01
Using this chart add vga=*** to the end of your kernel line in /boot/grub/menu.lst


```
      colour          depth   | 640x480  800x600  1024x768 1280x1024

      256             (8bit)  |  769      771       773      775
      32000           (15bit) |  784      787       790      793
      65000           (16bit) |  785      788       791      794
      16.7 Mill.      (24bit) |  786      789       792      795

```

Example:

title		Ubuntu, kernel 2.6.15-23-k7
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda2 ro quiet splash [COLOR="Red"]vga=795[/COLOR]
initrd		/boot/initrd.img-2.6.15-23-k7
savedefault
boot

---

### Post by chokes on 2006-06-01
Tanx a lot anduu! it worked!

---

### Post by Anduu on 2006-06-01
WooT!

:p

---

### Post by NotJustANewbie on 2006-06-01
Thanks so much!
Why wasn't this enabled as default anyway?!?
Its the only bug I found in the whole of Ubuntu Dapper so far and it seems like such a big problem because it affects the terminals as well ](*,) 

The Ubuntu team should fix this officially!
But thanks again for the quick-fix!:cool:

---

### Post by john280z on 2006-06-02
Thanks Anduu,

   For my Server install, I needed "vga=785" to get it to display correctly in MS Virtual PC(it runs in 16 color mode).

johnm

---

### Post by the.nightfly on 2006-06-15
Hy all! I'm newbie in Ubuntu, and I've a question.

How can I change the "default" ubuntu bootsplash screen?

I've installed Ubuntu Dapper Drake 6.06 with nvidia vga.
I want to enable [this bootsplash]("http://www.kde-look.org/content/show.php?content=38978").

How can I do this?


[COLOR="Silver"][SIZE="1"]srry for my english..[/SIZE][/COLOR]

---

### Post by The General on 2006-11-30
Sorry to bump this, but I have a widescreeen monitor, is there any way to set it to 1680x1050? If not, is there any way I can get a squished boot splash or something, so that when it displays it on my monitor it doesn't look stretched?

---

### Post by kinson on 2006-12-01
> **Anduu said:**
> Using this chart add vga=*** to the end of your kernel line in /boot/grub/menu.lst


```
      colour          depth   | 640x480  800x600  1024x768 1280x1024

      256             (8bit)  |  769      771       773      775
      32000           (15bit) |  784      787       790      793
      65000           (16bit) |  785      788       791      794
      16.7 Mill.      (24bit) |  786      789       792      795

```

Example:

title		Ubuntu, kernel 2.6.15-23-k7
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hda2 ro quiet splash [COLOR="Red"]vga=795[/COLOR]
initrd		/boot/initrd.img-2.6.15-23-k7
savedefault
boot

Woot !! Thanks man ! :D

I had the problem of my laptop not supporting the default boot res, so I kept having to manually set it everytime at boot, now I dont need to anymore !! :D I was looking for this.

I found a similar advice earlier, but I didn't realli understand it, and I put vga=800x600 ](*,)  Stupid me :P Owells, once bitten twice shy.

Muchos Gracias :)
Kinson

---

### Post by slugicide on 2008-07-16
> **The General said:**
> Sorry to bump this, but I have a widescreeen monitor, is there any way to set it to 1680x1050? If not, is there any way I can get a squished boot splash or something, so that when it displays it on my monitor it doesn't look stretched?

I'm looking for a solution to this, as well.  Any tips?

---

