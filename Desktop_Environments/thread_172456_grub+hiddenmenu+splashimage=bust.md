---
title: "grub+hiddenmenu+splashimage=bust"
date: 2006-05-08
forum: Desktop Environments
---

### Post by louis_nichols on 2006-05-08
I tried the above combination on 2 pc's and didn't want to post about it till I was able to check it happens on more than one machine.

So, I activate the hiddenmenu and splashimage for grub. And what I get is the screen with the countdown and the splashimage visible only on the area of the screen that contains the text counting down (about a line of text half the screen wide).

This wasn't like this with fedora core, on my pc, so it's not grub's source code fault. Any ideas how to solve this? Would writing the grub to mbr from another distro make a difference, I wonder? Still, ubuntu should be able to solve this...

---

### Post by Herman on 2006-05-08
Hello, louis_nichols,
I had something like that happen to me at first too when I was experimenting with splashimages last week. One (small) problem is the instructions on the splashimage how-to website are written for Red Hat, so we have to do a little extra thinking to convert them to Ubuntu.
I don't know if it matters or not, but I just put my splashimage in my /boot directory, not my /boot/grub directory. The website says /boot/GRUB directory (capital letters).
My entry for the splashimage is one linespace under the #hiddenmenu command, which I have left commented out.
I made another linespace before the #pretty colours line.
Mine looks like the following:
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

splashimage=(hd0,1)/boot/Ubuntusplash.xpm.gz

# Pretty colours
#color cyan/blue white/blue
 My other computer is a laptop so I have three grub splashes it that one and I have added all three to the menu.lst in the same fashion so I can show off how nice Ubuntu is to people. I just comment out the two I don't want to show at the time.
My wife's computer has Ubuntu with the Kubuntu desktop, and I put a nice Kubuntu splashimage in hers too, so I know it will work, I've done it enough time in computers here. It's probably just something extremely trivial that so far has escaped your attention. Pay attention to exactly how the splashimage command is typed, (notice mine has no gaps). It will probably be something simple like that. :-D Regards, Herman

PS, If you are making your own splashimages like I did, check that you set GIMP to use a 14 color palette before you save it as .XPM format, that is important. That might be where your problem is too. I can't quite remember now which solutions I used for which problems I encountered. The instructions are all there on the how-to website, but it's easy to miss a detail here or there that turn out to be vital later on.

---

### Post by louis_nichols on 2006-05-09
Hi man! Thanks for the reply.

The thing is splashimages work for me, but not when activating hiddenmenu. So the behavior I described, I get it only when the countdown line is showig. If I press ESC, I get the whole image. Still, I'd like to be able to use it, as it worked perfectly with Fedora.

---

### Post by Herman on 2006-05-09
>  The thing is splashimages work for me, but not when activating hiddenmenu. Activating hidden menu? I'm not sure I understand what you mean by that exactly.
Leaving the hash (#) before the word 'hiddenmenu' means your GRUB menu will show up on boot-up.  That's the default setting.
Removing the hash (#) before the word 'hiddenmenu', causes the 'hiddenmenu' feature to be activated and hides the GRUB menu on boot-up unless you press your 'Esc' key.   
Well, that's the way I think of it anyway. So you would need the hash to be left in place, (as shown in my menu.lst snippet in the previous post), in order for your GRUB menu to be displayed with your nice splashimage, of course. Unless you want to have to press 'Esc' every time. That's how it's supposed to be. You can't have it both ways, unless, (probably), I'm not understanding you correctly.
:D (Herman)

---

### Post by louis_nichols on 2006-05-09
[QUOTE=Herman]Activating hidden menu? I'm not sure I understand what you mean by that exactly.
Leaving the hash (#) before the word 'hiddenmenu' means your GRUB menu will show up on boot-up.  That's the default setting.
Removing the hash (#) before the word 'hiddenmenu', causes the 'hiddenmenu' feature to be activated and hides the GRUB menu on boot-up unless you press your 'Esc' key.   [/QUOTE]

This is what I mean by activating the hiddenmenu. NSorry i wasn't more clear.


[QUOTE=Herman]So you would need the hash to be left in place, (as shown in my menu.lst snippet in the previous post), in order for your GRUB menu to be displayed with your nice splashimage, of course. Unless you want to have to press 'Esc' every time. That's how it's supposed to be. You can't have it both ways, unless, (probably), I'm not understanding you correctly.
:D (Herman)[/QUOTE]

That's the thing: I WANT the menu hidden. I don't want to see the options. Just the image and as little text as possible (i.e. the counting down bit). But I also want to have the image in the background, and this doesn't work.

---

### Post by Herman on 2006-05-10
If you want to reduce the amount of text that appears on your grub menu, just 'comment out' the lines you don't want to see, like this:

title        Ubuntu, kernel 2.6.15-22-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-22-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-22-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-22-386 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-22-386 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.15-22-386
boot

#title        Ubuntu, kernel 2.6.15-21-386
#root        (hd0,1)
#kernel        /boot/vmlinuz-2.6.15-21-386 root=/dev/hda2 ro quiet splash
#initrd        /boot/initrd.img-2.6.15-21-386
#savedefault
#boot

#title        Ubuntu, kernel 2.6.15-21-386 (recovery mode)
#root        (hd0,1)
#kernel        /boot/vmlinuz-2.6.15-21-386 root=/dev/hda2 ro single
#initrd        /boot/initrd.img-2.6.15-21-386
#boot

#title        Ubuntu, kernel 2.6.15-18-386
#root        (hd0,1)
#kernel        /boot/vmlinuz-2.6.15-18-386 root=/dev/hda2 ro quiet splash
#initrd        /boot/initrd.img-2.6.15-18-386
#savedefault
#boot

#title        Ubuntu, kernel 2.6.15-18-386 (recovery mode)
#root        (hd0,1)
#kernel        /boot/vmlinuz-2.6.15-18-386 root=/dev/hda2 ro single
#initrd        /boot/initrd.img-2.6.15-18-386
#boot

title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin 
boot

See, only my Ubuntu boot option and recovery mode and memtest options will show. All the extra kernels that have been left over after updates are still there. They won't show on my menu because I have 'commented' them out with hashes (#). Actually I could probably just delete them at some stage later on.
Will that help? You'll need the # in front of 'hiddenmenu', too, for it to show your menu to see your spashimage. :D Herman.

---

### Post by louis_nichols on 2006-05-10
thank you for the idea, but the thing that actually bothers me most about the menu is not the text itself but the square around it. :)

Really now! I don't see any reason why the splash image can displayed in the background of the menu, but not of the countdown text when menu is hidden.

---

### Post by Herman on 2006-05-10
Well I agree with you there, I had a real devil of a time getting the different colored panels in my Ubuntu and Kubuntu splashimages to fit that darned rectangle!
I had to boot and re-boot a huge number of times before I got it right. I finally did it though, by stubborn persistence and perseverance.
Here's a link to mine if you are interested to download them and have a look.
                      [Ubuntusplash]("http://www.users.bigpond.net.au/hermanzone/grubsplashes/Ubuntusplash.xpm.gz")    |     [Kubuntusplash]("http://www.users.bigpond.net.au/hermanzone/grubsplashes/Kubuntusplash.xpm.gz")
They fit the Grub menu rectangle for Dapper, but my wife is running Ubuntu Breezy, with the KDE desktop, and hers didn't fit. Breezy has a different size rectangle. 'Ho-hum'.....'Back to the drawing board', as they say.

If you download mine, you can either use them if you like them, or just open them with GIMP, and use them for a stencil to help you see where the edges of the rectangle are for helping you make your own easier. You could make your own over the top in the next layer in GIMP, for example.
If you have Breezy. it's only the bottom edge you'll have to experiment with to get it right. The top and side should line up. That would be easy to modify with GIMP.

Edit: Oh, I see you are using Dapper too, they should fit then, Regards, Herman

---

### Post by louis_nichols on 2006-05-10
Thanks! I'll try them. It might be a step forward in boot menu eye-candy :)

I posted a bug about this situation. I don't know where it resides, but it's not at all logical and someone should take care of it, at Ubuntu level or upstream.

---

