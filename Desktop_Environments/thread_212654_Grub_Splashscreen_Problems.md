---
title: "Grub Splashscreen Problems"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Grim_n_Evil on 2006-07-10
For the past several hours I have been trying to install a Grub splashcreen but with little success. I got the image to show at boot, however I still have the following problems:
1) The boot menu is enermous and non-transparent and hides most of the image. I uninstalled the unnecessary kernel images with the hope that the menu window will shrink. It didn't. 
2) After my last restart the highligh bar from the boot menu had disappeared and the font looked somewhat different (a size smaller maybe). 

I read in a thread somewhere that the missing highlight bar is a Grub bug, however it was still there this morning and I can't really think of anything I could have done to cause this. 

Does anyone have solutions to these problems?

---

### Post by greengrocer on 2006-07-11
From my experience with Grub, it is not as flexible as Lilo when it comes to the asthetics of the boot menu.

In Grub, the boot menu text always takes up about half of the screen area and covers much of the splash screen.

The colours of the menu text are configurable in: /boot/grub/menu.list

To set the colours of the text and highlight bar when using a splashscreen, you cannot simply use settings such as green and white and so on in menu.list

To control the text and highlight bar colours, you have to use in the menu.list file, something like:

foreground  = ffffff
background  = 000000

(for example: ffffff is white and 00ff00 is bright green)

Regards,
Greenie

---

### Post by Grim_n_Evil on 2006-07-11
Thanx for your reply. I kinda fixed it by changing the splashscreen and uncommenting the ##Pretty Colors. I have no idea what exactly happened but it looks great now so I'm not touching it anymore :mrgreen:

---

### Post by alingatong on 2006-07-31
The grub no higlight bug is is still there when we use the ubuntu splashscreen having a black background. And I think no one is fixing this small bug. 

Changing the splashcreen into an image without a black background or no splashscreen at all.

---

### Post by Xappe on 2006-08-16
> **alingatong said:**
> The grub no higlight bug is is still there when we use the ubuntu splashscreen having a black background. And I think no one is fixing this small bug. 

Changing the splashcreen into an image without a black background or no splashscreen at all.

I struggled for quite a while before I got a decent background image (black background) and usable colors. The secret is 

foreground =<color>
background =<color> (seems to set the color of the highlight and the text shading)
shade=0 (disables text shading)

now I want to know if one can disable the frame around the menu and maybe remove/edit the usage text at the top/bottom.

---

