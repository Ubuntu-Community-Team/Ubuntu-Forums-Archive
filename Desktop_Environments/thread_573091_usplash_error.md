---
title: "usplash error"
date: 2007-10-11
forum: Desktop Environments
---

### Post by dexjul on 2007-10-11
Hi

I follow the instruction of usplash 

[https://help.ubuntu.com/community/USplashCustomizationHowto?highlight=%28usplash%29](https://help.ubuntu.com/community/USplashCustomizationHowto?highlight=%28usplash%29)

Im having a problem on 

gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o

usplash-artwork.c:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘has’

Thanks

---

### Post by ingo on 2008-02-25
Same here - bump.

Have you found a solution yet?

---

### Post by viperet on 2008-02-25
Open file usplash-artwork.c in editor - it contains error message - usualy because you .png uses more than 16 colors. Convert png to 16 colors or use pngtousplash in place of pngtobogl - it supports 256 colors...

BTW i followed all steps in that HOWTO, compiled my usplash picture into my-artwork.so, but it isnt working... just black screen with blinking text cursor in topleft corner during boot...

---

### Post by ingo on 2008-02-25
Thank you viperet, just the info I wanted ;)

I found out about too many colours about five minutes after posting - my image had 256 colours. Now I've got 16 but it tells me I've got 32!?! Must be missing something basic here.

I've successfully used splashy, but this does not work once you remaster your kubuntu... Thought I'd give the usplash devil a go but am a little stumped at the mo.

BTW, did you make sure you switched assigned colours around?

---

### Post by ingo on 2008-02-25
Right, did a 256 colour 800x600 piccie, rearranged the colour map, saved it as BMP, used imagemagick to convert it to png, did pngtousplash to convert it to c (2.8MB!) and did not get the error message in post #1. Hurray!

However, after replacing the Kubuntu splash with my own, I get the blinking cursor syndrome PLUS I lost my tty 1-6 and am not amused! Tired now, will try again tomorrow.

---

### Post by viperet on 2008-02-26
> **ingo said:**
> Right, just managed to get your blinking cursor PLUS I lost my tty 1-6 and am not amused! Tired now, will try again tomorrow.

Same result... Tried everything, 16, 256 colors - just blank screen and no text consoles

---

### Post by ingo on 2008-02-26
OK, so I chose the standard kubuntu usplash theme again in the vain hope that tty 1-6 would reappear but they haven't. I reckon it is time to have a look at launchpad and file a bug since this is _bad_. Having said that I am pretty new to how grub settings interact with g/kdm and the sort of impact they have. 

EDITED - tty 1-6 are back :) In /boot/grub/menu.lst I changed the # defoptions line to read ```
# defoptions=quiet splash
```OK, now no splash at all, but at least I have my terminals back. 

There is more to investigate...

---

### Post by ingo on 2008-02-26
This is getting somewhat of a monologue but here goes:

I edited my /etc/usplash.config to 800*600, did a sudo update-initramfs -u and now I have the kubuntu splash and my terminals. Never had this before... 

However, my own splash is still not working which suggests that something must have gone wrong in its creation. Methinks the colour mapping is at fault because there are the greatest number of steps involved, i.e. either I borked it or the conversion to bmp and subsequent imagemagick conversion to png borked it. Three steps...

In any case, assuming that I got it right the next fault could be made by the gimp during its bmp conversion. AFAIK a straight export to png is not recommended. Has anybody ever got this to work? If so, which image format did you choose? And how did you then convert it to png?

The mind boggles :)

---

### Post by viperet on 2008-02-26
Dont think problem is in color mapping - custom usplash doesnt working at all - even with bad palette

---

### Post by ingo on 2008-02-27
I have found two pieces of software that take the sting out of creating your own usplash theme: First one allows you to preview whatever you have produced without having to go through the tedious process of rebooting every time - usplash-switcher at [www.getdeb.net/release.php?id=917](www.getdeb.net/release.php?id=917)

The second one, fasten your seatbelts, lets you create a theme from a picture of your choice by simply running a script!!! TheeeMahn has cooked this up for us [http://forumubuntusoftware.info/viewtopic.php?f=23&p=4796](http://forumubuntusoftware.info/viewtopic.php?f=23&p=4796)

I've started testing already...

---

