---
title: "Xorg display modes, DVI vs. VGA"
date: 2009-01-29
forum: General Help
---

### Post by Slim Odds on 2009-01-29
First off, this is a question about X (Xorg).
 
 Ok, I'm a linux geek from way back. I love using linux and highly recommend it to most folks. But, every once in a while there are the occasional frustrations that make you want to pull your hair out (and I don't have any to spare).
 
 Here's the latest one for me and I'm hoping that someone can give me some pointers.
 
 I reconfigured some slightly older machines. This machine has a older GeForce FX 5200 video card with dual outputs (DVI and VGA). My display is an Acer AL2016W (1680x1050).
 
 Here's the issue:
[INDENT]If I connect my display to the DVI output, X incorrectly determines that the resolution is 1600x1200. Also, if I go to a console (Ctrl-Alt-F1) the display receives an invalid mode and goes blank.
[/INDENT][INDENT]If I connect my display to the VGA output, X correctly uses 
1680x1050 and the console is fine.
[/INDENT]
I would prefer to use the DVI (it is preferred to use digital than analog, right?).
 
 Any ideas?
 
Thanks.....

---

### Post by dcstar on 2009-01-29
> **Slim Odds said:**
> First off, this is a question about X (Xorg).
 
 Ok, I'm a linux geek from way back. I love using linux and highly recommend it to most folks. But, every once in a while there are the occasional frustrations that make you want to pull your hair out (and I don't have any to spare).
 
 Here's the latest one for me and I'm hoping that someone can give me some pointers.
 
 I reconfigured some slightly older machines. This machine has a older GeForce FX 5200 video card with dual outputs (DVI and VGA). My display is an Acer AL2016W (1680x1050).
 
 Here's the issue:
[INDENT]If I connect my display to the DVI output, X incorrectly determines that the resolution is 1600x1200. Also, if I go to a console (Ctrl-Alt-F1) the display receives an invalid mode and goes blank.
[/INDENT][INDENT]If I connect my display to the VGA output, X correctly uses 
1680x1050 and the console is fine.
[/INDENT]
I would prefer to use the DVI (it is preferred to use digital than analog, right?).
 
 Any ideas?
 
Thanks.....

The video card is not supplying the correct info for the DVI port, manually set the resolution using the Nvidia-settings tool.

---

### Post by Slim Odds on 2009-01-29
> **dcstar said:**
> The video card is not supplying the correct info for the DVI port, manually set the resolution using the Nvidia-settings tool.

It does not list the correct resolution.... there is a long list, but not 1680x1050.

---

### Post by penetal on 2010-06-20
Sorry for reviving an old thred but I have the same screen but an ATI 4870-X2 graphics card hence I have no vga output only 2 DVI so I use DVI -> VGA connector and I have the same Sh*tty problem. It is making me insane and I remember once I could fix this in xorg.conf but now that simply will not work. Have you managed to find a good solution for this extremly annoying problem? Best Regards

---

