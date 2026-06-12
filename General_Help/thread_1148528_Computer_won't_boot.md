---
title: "Computer won't boot"
date: 2009-05-04
forum: General Help
---

### Post by Imoen on 2009-05-04
My computer won't boot and I really don't want to loose everything I have on it. It was working fine but Skype kept saying it couldn't start because it was already running even after I killed any skype processes, so I thought I should just restart and see if that would help. Now I get the press esc to select boot options message and after that my monitor just goes black and flashes no signal. I have tried editing out quiet and it made no difference. I have not installed the update to 9.04 so I believe I'm using 9.03 (9.04 does not have a driver for my video card). Please help me, I'm a Ubuntu noob and have no idea how to fix errors like this.

---

### Post by roger_1960 on 2009-05-04
Hi

Have you tried pressing ESC?  Does it give you a boot menu?  If so go to "recovery mode" and then at the prompt type

> startx

and return.  Did that work?

---

### Post by Imoen on 2009-05-04
I tried this, pressing esc and selecting recovery mode. The screen goes black and "out of range" in a box starts to move about my screen, the same as it does in regular mode and no prompt ever appears.

---

### Post by roger_1960 on 2009-05-04
Mmm

I have no idea!  My next move would be to get a USB stick or external drive and try to boot from a live CD and copy my data off the hard drive.  Then try posting again in hardware & laptops if you get no more informed response here.

Sorry, but I'm out of my depth.....

---

### Post by Imoen on 2009-05-04
Thanks for trying, I'll post there and see what they can think of. I'm downloading to run the livecd so I can at least save my files that I don't want to loose.

---

### Post by Imoen on 2009-05-04
Well, I guess I won't even be able to do that. The livecd just gives me the same out of range issue as the hard drive. This is terrible! This is the same hardware I have had in my computer for over a year and have never used anything different in Ubuntu so I can't see any reason that it just suddenly doesn't work.

---

### Post by Imoen on 2009-05-04
After more searching it seems this could be an issue with my monitor settings in the grub loader according to [https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer) although I have no idea why they would have changed. 

Anyway, I am using an ATI X1650 Pro video card with an [Asus VW198 LCD monitor](http://usa.asus.com/products.aspx?l1=10&l2=87&l3=581&l4=0&model=1883&modelmenu=2)

I have no idea how to change the settings if this is the issue since I can't seem to load anything to even edit the configuration.

---

