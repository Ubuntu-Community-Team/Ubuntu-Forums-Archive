---
title: "Is there a way to change resolutions on the usplash screen when booting?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by irv on 2006-06-19
I have a high end video card and a 21" monitor with great resolution, but the usplash screen is in low resolution which is not pleasant to the eye
Is there a way to change resolutions on the usplash screen when booting?
Is there a configuration file that can be edited to do this?

---

### Post by Ramses de Norre on 2006-06-19
Add a vga= option to your kernel line in /boot/grub/menu.lst.
The highest rate I know about is vga=795 wich is 1280*1024 and depth 24.

---

### Post by irv on 2006-06-19
[QUOTE=Ramses de Norre]Add a vga= option to your kernel line in /boot/grub/menu.lst.
The highest rate I know about is vga=795 wich is 1280*1024 and depth 24.[/QUOTE]
I added the vga=795 to the menu.lst. in the grub folder in the boot folder and restarted the computer.
> # menu.lst - See: grub(8), info grub, update-grub(8) These smilies are the number 8.
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'. 
          
default		0

vga=795

And it booted the same resolution. "LOW". Does this line need to be the first thing in the menu?

---

### Post by Ramses de Norre on 2006-06-19
You need to add it to your kernel line like this: ```
title           Ubuntu, kernel 2.6.15-25-k7
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.15-25-k7 root=/dev/sda1 ro quiet splash **vga=795**
initrd          /boot/initrd.img-2.6.15-25-k7
savedefault
boot

```

---

### Post by raptros-v76 on 2006-06-19
you need to do it this way: 

```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **vga=791**

...

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash **vga=791**
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

```

---

### Post by Ramses de Norre on 2006-06-19
That's also possible, things added to the defoptions line are applied to all kernels when you run sudo update-grub or when new kernels are installed.

---

### Post by raptros-v76 on 2006-06-19
yes, i always add important things to the defoptions, i had some other stuff going on there at one point, (dont need it any more), and had an experience that wasnt so pleasant after a kernel upgrade. theres a reason why one should always have a bootable linux disk on hand

---

### Post by irv on 2006-06-19
Ok, I added it to this line:
> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro ht=on quiet splash **vga=795**
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot
but now when I boot it said "You passed an undefined mode number". 
It give me an opption to to change modes, so I just picked one but all it does is changes the number of columns and rows. In fact, I never even got the splash screen.

---

### Post by raptros-v76 on 2006-06-19
ok. you need to install svgalib
sudo aptitude install svgalib-bin
then reboot

---

### Post by irv on 2006-06-19
[QUOTE=raptros-v76]ok. you need to install svgalib
sudo aptitude install svgalib-bin
then reboot[/QUOTE]
Well, I did the install of svgalib-bin, rebooted and got the same message. I then took the vga=795 out rebooted and got the usplash back with the low res. ](*,) 
I guess I feel like that smily beating his head against the brick wall.
Thanks anyway for all the help. 
It's great seeing people helping people on this forum!

---

### Post by Anduu on 2006-06-19
Use this handy dandy chart and try some different numbers.

```
      colour          depth   | 640x480  800x600  1024x768 1280x1024

      256             (8bit)  |  769      771       773      775
      32000           (15bit) |  784      787       790      793
      65000           (16bit) |  785      788       791      794
      16.7 Mill.      (24bit) |  786      789       792      795
```

---

### Post by leech on 2006-06-19
I've found that some hardware doesn't like using that form of the vga= line.  I had to use the hex conversion for one of my computers so that it would work right.  

```
 Colours 	 640x400  640x480  800x600  1024x768  1152x864  1280x1024  1400x1050  1600x1200
4 bits 	            ?        ?      0x302      ?         ?          ? 	       ?          ?
8 bits  	  0x300    0x301    0x303    0x305      0x161     0x307        ?        0x31C
15 bits             ? 	   0x310    0x313    0x316      0x162     0x319      0x340      0x31D
16 bits             ?      0x311    0x314    0x317      0x163     0x31A      0x341      0x31E
24 bits             ?      0x312    0x315    0x318       ?        0x31B      0x342      0x31F
32 bits             ?        ?        ?        ?        0x164       ?          ?          ?
```

Also, it looks like this table is a bit fuller on the Gentoo wiki.

```
	640x480  800x600  1024x768  1280x1024  1152x864  1600x1200
8 bit 	  769	   771	    773        775       353        800
15 bit 	  784      787      790        793       354        801
16 bit 	  785      788      791        794       355        802
24 bit 	  786      789      792        795        x         803
```

---

### Post by irv on 2006-06-20
[QUOTE=Anduu]Use this handy dandy chart and try some different numbers.

```
      colour          depth   | 640x480  800x600  1024x768 1280x1024

      256             (8bit)  |  769      771       773      775
      32000           (15bit) |  784      787       790      793
      65000           (16bit) |  785      788       791      794
      16.7 Mill.      (24bit) |  786      789       792      795
```[/QUOTE]
That did the trick. I guess the 795 was just over what my system could handle. The setting I went with was 791.
Thanks again for all the help.

---

### Post by Anduu on 2006-06-22
[QUOTE=irv]That did the trick. I guess the 795 was just over what my system could handle. The setting I went with was 791.
Thanks again for all the help.[/QUOTE]

I still find it strange you can't do 795...my system is not high end(AthlonXP 1.8GHz/Radeon9600...)and I can do it no problem.

Check the documentation for your monitor and see what resolutions/refresh rates it is capable of.Mine will do up to 1600x1200@75hz

---

### Post by egorgry on 2006-06-23
The best and easiest way to find out your supported resolution for the framebuffer is this nice little tool hwinfo --frambuffer

you may need to sudo apt-get install hwinfo I don't think it installs by default. Hope this helps. You should be able to do a higher resolution than that. my laptop does 1400x1050 on a 15 inch screen and my 20" LCD nvidia 6800 combo does 1600x1200

---

