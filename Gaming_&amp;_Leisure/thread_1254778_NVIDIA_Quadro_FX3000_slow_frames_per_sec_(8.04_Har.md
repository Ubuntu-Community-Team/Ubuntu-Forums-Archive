---
title: "NVIDIA Quadro FX3000 slow frames per sec (8.04 Hardy)"
date: 2009-08-31
forum: Gaming &amp; Leisure
---

### Post by Rambetter on 2009-08-31
I have 2 desktop computers with quite similar hardware.  I initially installed 8.04 Hardy onto both, and then switched over to Debian Lenny.  However, I had a problem with Hardy that I am now having as well with Lenny.  So my problem applies to both Hardy and Lenny.

I posted in the Debian Forums here: [http://forums.debian.net/viewtopic.php?f=7&t=44727](http://forums.debian.net/viewtopic.php?f=7&t=44727) but I will repeat that post here.

=======================
I have 2 desktop computers, both with fresh installs of Debian Lenny i386 32 bit (5.0.2). They both have relatively similar hardware, only the newer desktop has slightly newer hardware. Well it turns out that I get very poor frames per second when playing 3D video games using the newer desktop, and I get very good frames per second when using the older desktop.

Here are the specs for both:

NEWER DESKTOP:
cpu: 3.2 GHz Pentium 4 Hyperthreading, 800 MHz FSB
ram: 2x1 GB DDR PC3200 (400 MHz)
motherboard: Intel D865PERL, supporting AGP 8x
graphics card: NVIDIA Quadro FX3000 256 MB AGP 8x
storage: using SATA hard drive & disc drive

OLDER DESKTOP:
cpu: 2.8 GHz Pentium 4, 533 MHz FSB
ram: 2x1 GB DDR PC2700 (333 MHz)
motherboard: Intel D845PEBT2, supporting AGP 4x
graphics card: NVIDIA Quadro 4 750XGL 128 MB AGP 4x
storage: using IDE hard drive & disc drive

I have the 96xx (legacy) NVIDIA drivers installed on both computers, as Debian packages. This is a correct version of the drivers for both graphics cards. I have removed my .nvidia-settings-rc on both computers to ensure that the graphics card settings are default. I have removed all the config files for the video game I'm playing to ensure that the graphics settings are default. The older computer is connected via VGA to a 1024x768 LCD display, and the newer one is connected via DVI to a 1680x1050 LCD display. To test both computers equally, I'm running the video game in 1024x768 mode on both computers (tried fullscreen and windowed mode, made no difference).

So, now the bottom line. I get 2 to 3 times the frame rate on my older computer. That's 40 frames per sec on the newer computer compared to about 100 on the older one, on the same level on the same server spectating the same player. On some maps (levels) I do get the full 125 frames per second on both computers, but on any "normal" level I get only 40 frames per sec on the newer computer.
 
I'm trying to see if any of the hardware on the newer desktop is faulty. I ran memtest86+ on the newer desktop, and it runs very fast and no errors.

Does anyone have any idea why th performance for the 3D video game is so much worse on the newer computer? Everything else on the newer computer works fine, and runs faster than on the old computer.

Coud the problem be something else, like the fact that the newer computer has hyperthreading available (and enabled)? Or maybe the FX3000 was not meant to play games on?

---

### Post by bl33d on 2009-08-31
thats an nv35 class card. you can usee the 169.xx driver in hardy for it.

---

### Post by Rambetter on 2009-08-31
I tried using the newer driver in both Hardy and Lenny.  I decided against it because it just made the FPS issue even worse.  Also, some other bugs appear with the newer drivers that don't appear with the 96xx series.

The FX3000 is a pretty old card, and the 96xx driver series became lagacy after the FX3000 was released, so that justifies my using them.

But, thank you for your input.

---

### Post by bl33d on 2009-08-31
> **Rambetter said:**
> I tried using the newer driver in both Hardy and Lenny.  I decided against it because it just made the FPS issue even worse.  Also, some other bugs appear with the newer drivers that don't appear with the 96xx series.

The FX3000 is a pretty old card, and the 96xx driver series became lagacy after the FX3000 was released, so that justifies my using them.

But, thank you for your input.

but its a geforce 5XXX class card. it should work ;L

---

### Post by Rambetter on 2009-08-31
On my two desktops, I switched graphics cards on both.
I plopped the Quadro 4 750XGL into the newer computer and the FX3000 into the older computer.
The low fps follows the graphics card.  In other words, the new computer with the 750XGL is now running very fast 3D.  Funny thing is, I have 2 FX3000's and they are both slow on both computers.  No idea why this is happening.

---

