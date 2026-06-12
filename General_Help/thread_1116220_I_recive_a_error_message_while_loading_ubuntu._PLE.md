---
title: "I recive a error message while loading ubuntu. PLEASE HELP!"
date: 2009-04-04
forum: General Help
---

### Post by krine11 on 2009-04-04
Hi there. I first want to start off that every time when my computer loads right a black screen pops up and says the following : Cannot Display this video mode -- Optimum Resolution 1280 x 1024 60Hz.

My Graphics card : 

ATI Raiden Xpress 200.

=====================================

I do not have any drivers downloaded for my graphics card to let you know, I also am useing Ubuntu 8.10 (for about nearley 3 weeks now) and want to fix this issue because it kind of looks wierd just seeing a error while loading but rather than that when my intire screen loads everything seems perfectlly fine, its fast and so but that load screen error seems major in my oppnion. Can you please give me a solution and as well not that hard like go to terminal or something because i need real step by step solutions since i am still a bit new to this.

-Thanks!

---

### Post by ibuclaw on 2009-04-04
When the bootloader loads, press **ESC**, and press '**e**' to go to the edit menu.
Next, scroll down to the **kernel** line and press '**e**' again.

Add to the end of the line:
```
 vga=ask
```
Press **Enter** and '**b**' to boot your computer.

You'll get a prompt to choose which resolution you want the console to be in.

Select one with the required spec for your monitor (1280 x 1024 60Hz) and remember the three digit code you entered/chose.

If usplash shows without error. To make this permanent, edit your menu.lst bootconf.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

sudo gedit /boot/grub/menu.lst
```
Locate the following section:
> 
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

And put vga=**123** (replace 123 with the code for your monitor resolution) on the defoptions= line.

After saving and quitting, run:
```
sudo update-grub
```
To make the changes take effect.

Regards
Iain

---

