---
title: "Display problems after 1st boot"
date: 2006-08-09
forum: Desktop Environments
---

### Post by ashughes on 2006-08-09
OK, to start off, here is my computer configuration:

Asus A8V motherboard (Via KT800 chipset)
1GB DDR-400
AMD64 4000+
Sapphire Radeon X800XL 256MB PCI-e
Maxtor 250GB ATA/133 HDD
LG 8x24x4 CD/DVD RW (ATA/133)
Samsung Syncmaster 700IFT 17" CRT monitor

OK, here is my story:

First off, I was using Badger for a few months with no 3D.  Which I was quite content with after days of battling with my Radeon, to no avail.  Since I heard Dapper was out, I decided to give it a try.  This has not gone well at all.

When I boot with the CD, it comes up to the CD boot menu where I can select Live or Install, but either way I go, I just get a blank screen right after the boot menu.

So, under advisement of my own research done on the forums I tried the alternate CD last night.  The install goes great, and I get the standard "can't start x cuz ati is inferior crap" error.  So I go and reconfigure X to run off of VESA to get the display to work in 2D (same as I always did in Badger).  Voila, blank screen every time I boot now.

I tried ctrl+alt+backspace, ctrl+alt+Fx, and ctrl+alt+del, and nothing works.  Only way I get any response is if I force a powercycle.  Which just loops me through the boot process to the same blank screen.  Recovery mode results in the same.

The only way I can get it to boot is to re-install Dapper and have X crash with the default driver it loads, then I can get back to text mode.

I only tried running at 1280x10242@60Hz 24-bit (which worked in Badger) as I am not able to reconfigure unless I reinstall.  I am going to try to reinstall and run on 1024x768 tonight.  Hopefully it works.

Any other advice from people (keep in mind, I just want to get VESA to work right now for 2D...I will worry about getting 3D to work later) would be much appreciated.

I am this far from downgrading to a slightly slower Nvidia card as I dont have $300 to blow and I dont really do a lot of graphic intensive work (apart from the occasional game of Diablo 2 or Warcraft 3 or FNES, but I use windows for that).

Thanks for you time and any help that you may offer,

Anthony

PS. What if I tried the i386 instead of A64 version?  would this work on AMD64??

Anyway,  Thanks again...

---

### Post by deeek on 2006-08-09
> 
PS. What if I tried the i386 instead of A64 version? would this work on AMD64??


Sorry, I can't help you with your graphics problems, but I do believe that you would have less problems using the i386 version as opposed to the AMD64 version.  There would be no compatibility problems.

---

### Post by ashughes on 2006-08-09
what is the difference?....

One is 32 bit and one is 64 bit?

---

### Post by tseliot on 2006-08-09
Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vga" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

Boot as usual

---

### Post by deeek on 2006-08-09
> **ashughes said:**
> what is the difference?....

One is 32 bit and one is 64 bit?
Personally, I have always had some sort of problem or glitch when using the 64bit version.  Like flash, certain video codecs, etc.  I would try it.

---

### Post by ashughes on 2006-08-09
TSELIOT> I tried booting in recovery mode and I dont get to a command line, it boots to the same blank screen.

---

### Post by ashughes on 2006-08-09
The more and more I look into it, the more and more I think I should just try out the 32 bit version tonight.

Unless you folks have any other courses of action I can take, I will try that and let you guys know.

---

### Post by ashughes on 2006-08-09
Well, looks like i386 was the way to go.....so far.....*knock on wood*

The live cd worked flawlessly....it actually took longer for it to boot from the cd then it did to install it when I got in.

I had to change the driver to vesa, but it worked on vesa this time.  Now I am gonna go get the ati driver and see if I cant get this card working properly.

I will keep everyone posted....

---

