---
title: "boot customizations"
date: 2009-01-16
forum: General Help
---

### Post by crazyness003 on 2009-01-16
Hello. Not a pressing issue.
I just wanted to know how i can customize my boot sequence.

First, GRUB~
I know there's a GRUB2 that can make your menu screen look very nice. 
*[Q]* Is it hard to install GRUB2 and does it come with some unforseeable consequences after installing?
*[Q]*Also, is configuring it the same as regular GRUB?

Post-GRUB~
After the grub menu list, I don't like using usplash, so instead I watch the pretty white text zoom by. But in order to make it look nicer:
*[Q]* Is there any way to make the text of a raw boot, smaller and change the color or background?

Splashy as an alternative~
I've heard of splashy used as an alternative to uslpash, but didnt get enough info on it.
*[Q]*What benefits does splashy have over usplash?

This one is for diagnostics~
Some of the text that flies by is hard to catch, and I have no intention of sitting in front of my computer with a camera, and hope I got what I need.
*[Q]*Can one make all the text of a boot dump to a file for later viewing? 
I tried using Boot Chart, but I seem to have failed at it.

I was gonna post this i Desktop Effects and Customizations...but it kinda dosnt fall within that category.
Thanks for any input.

---

### Post by crazyness003 on 2009-01-21
sorry to sound so petty: bump

---

### Post by mcduck on 2009-01-22
1. I've never tried Grub2, can't help you with that. I'd assume the configuration would be pretty similar to Grub, but installing it might not be that easy..
-----

2. While in Grub menu, highlight your current boot line & press "e" to enter edit mode. Then highlight the kernel line and press "e" again to edit it. Now, add "vga=ask" to the end of the line, press enter and then "b" to boot. You'll get a message that tells you to press enter to show available graphics modes, do that and you'll get a list of what resolutions/color depths are available for you.

Pick one you like, enter it's number (and memorize that number for now). Ubuntu will now boot using that resolution (which will make the boot text & consoles prettier.

If everything seems to work fine and you like the resolution you selected, edit /boot/grub/menu.lst and add "vga=*yournumber+256*" to the end of the kernel line (so, if the number yous elected during boot was 536 you add "vga=792" to menu.lst. (792 would be 1024x768 with 32-bit colors)

To make this setting stay even after kernel updates add the same vga-entry to the line with "#defoptions=splash quiet" (in the default options section of menu.lst)

Color or background image is possible, but as far as I know requires compiling your own kernel to add support.. :/

If you want, I can give you instructions how to change the "[ ok ]"-messages during boot to green but that will add annoying garbage to the boot log file you also wanted to enable..

You can get a bit of extra terminal eyecandy by installing Bashish, which is an easy tool for changing command prompt themes. If I remember right some of the themes had a colored background..
-----

3. I used Splashy for a while before Usplash was introduced. Based on that, I can't see any benefits over using Usplash.
-----

4. Edit /etc/default/bootlogd and change "BOOTLOGD_ENABLE=No" to "BOOTLOGD_ENABLE=yes". Now the boot messages should be logged into /var/log/boot

---

### Post by crazyness003 on 2009-01-22
Thanks man. You get a medallion when they come back!
So, splashy really dosnt give extra candy huh? Meh, If i can get the console to look nice, it wont be necessary for any splash.

And I guess im just gonna have to experiment with GRUB2. 

And, even tho you said it adds extra garbage to the log, it would be nice to see how it looks with green [ok]'s

Also, when I used sam (start-up manager), I could get the splash progress bar to show AND a "less verbose console" to run thru commands below it. What controlls that, and how would one be able to implement that without a splash, yet still have "less verbose" things?

I just wanna learn the smart way (also, if possible which manual do I f*ng read to get this info? :D)

---

