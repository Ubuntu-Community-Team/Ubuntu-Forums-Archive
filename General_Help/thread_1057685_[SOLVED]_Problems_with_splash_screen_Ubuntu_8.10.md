---
title: "[SOLVED] Problems with splash screen Ubuntu 8.10"
date: 2009-02-02
forum: General Help
---

### Post by kbloem on 2009-02-02
Ok i finally got it using usplash :popcorn:


1.) Run in terminal : [COLOR="RoyalBlue"]sudo apt-get remove usplash --purge[/COLOR]
2.) Download following files [libsplashy](http://http://alioth.debian.org/frs/download.php/2461/libsplashy1_0.3.10-1_i386.deb) en [Splashy](http://alioth.debian.org/frs/download.php/2462/splashy_0.3.10-1_i386.deb) 
3.) Just double click them in gnome. First libsplashy..... 
4.) in [COLOR="RoyalBlue"]/boot/grub/menu.lst[/COLOR] add option [COLOR="RoyalBlue"]VGA=791[/COLOR] in kernel line.
5.) Reboot

At reboot you will see an ugly pinguin. If you like it keep it that way but if you don't follow these steps.
1.) In [COLOR="RoyalBlue"]/etc/splashy/themes/default[/COLOR] you can change [COLOR="RoyalBlue"]background.png[/COLOR] to your own image but you have to name it the same. 
2.) In [COLOR="RoyalBlue"]theme.xml[/COLOR] you can change the location of the loading bar and also the color settings.
3.) Run from terminal [COLOR="RoyalBlue"]mkinitramfs -o /boot/initrd.img-`uname -r`[/COLOR]

This worked for me. Good Luck

---

### Post by luvsaraf on 2010-06-21
> **kbloem said:**
> Ok i finally got it using usplash :popcorn:
 
 
1.) Run in terminal : [COLOR=royalblue]sudo apt-get remove usplash --purge[/COLOR]
2.) Download following files [libsplashy]("http://http://alioth.debian.org/frs/download.php/2461/libsplashy1_0.3.10-1_i386.deb") en [Splashy]("http://alioth.debian.org/frs/download.php/2462/splashy_0.3.10-1_i386.deb") 
3.) Just double click them in gnome. First libsplashy..... 
4.) in [COLOR=royalblue]/boot/grub/menu.lst[/COLOR] add option [COLOR=royalblue]VGA=791[/COLOR] in kernel line.
5.) Reboot
 
At reboot you will see an ugly pinguin. If you like it keep it that way but if you don't follow these steps.
1.) In [COLOR=royalblue]/etc/splashy/themes/default[/COLOR] you can change [COLOR=royalblue]background.png[/COLOR] to your own image but you have to name it the same. 
2.) In [COLOR=royalblue]theme.xml[/COLOR] you can change the location of the loading bar and also the color settings.
3.) Run from terminal [COLOR=royalblue]mkinitramfs -o /boot/initrd.img-`uname -r`[/COLOR]
 
This worked for me. Good Luck
 
when i tried this, my image appears when i shutdown my computer but the pinguin appears during boot-up.
Do you know what can be the problem

---

