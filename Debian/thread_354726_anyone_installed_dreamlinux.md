---
title: "anyone installed dreamlinux?"
date: 2007-02-06
forum: Debian
---

### Post by jclmusic on 2007-02-06
the installer for version 2.2 always seems to freeze for me at about 89%. i checked out their forums, but the help is very limited for those who (like me) don't speak Portuguese!

---

### Post by Rodneyck on 2007-02-06
> **jclmusic said:**
> the installer for version 2.2 always seems to freeze for me at about 89%. i checked out their forums, but the help is very limited for those who (like me) don't speak Portuguese!

I remember having problems with my old computer which had a built in graphics card in the MB, Intel, and their xorg initial setup. It has been awhile since I have used Dreamlinux, but I think I remember several other possible ways to install instead of the default. Work your way down the list of options that pops up in the beginning, I think one of the other ways worked for me after several attempts.

---

### Post by jclmusic on 2007-02-06
> **Rodneyck said:**
> I remember having problems with my old computer which had a built in graphics card in the MB, Intel, and their xorg initial setup. It has been awhile since I have used Dreamlinux, but I think I remember several other possible ways to install instead of the default. Work your way down the list of options that pops up in the beginning, I think one of the other ways worked for me after several attempts.

thanks, but i couldn't find an alternative installation or any similar option. do you know what this option is called?

---

### Post by Rodneyck on 2007-02-06
> **jclmusic said:**
> thanks, but i couldn't find an alternative installation or any similar option. do you know what this option is called?

I don't, because I have not used it in awhile, so working from memory (which is a crap shoot at this point) here. Do they have a text based install option or something similar that allows the user to select the hardware setup step-by-step?  I think it was something along those lines.

I remember finally being able to boot into a 640x4XX screen which s*cked, but it allowed me to then go in and edit the xorg.conf file.  In the end, I finally got everything set up. 

What is your system btw?

---

### Post by RAV TUX on 2007-02-06
moving to Debian (and derivatives) forum

---

### Post by jclmusic on 2007-02-07
nope, no text based install cd as far as i can see from their website. if only there was!

i found a guide on their website that said to completely wipe the drive 1st (i used the 'sudo shred -n 1 -v -z /dev/hdb' command from inside ubuntu which is on hda). it then said to partition the hard drive using the dreamlinux live cd, then reboot and install afterwards, skipping the partitioning bit. i did this, but with the same result. the only difference was that it froze quicker lol.

---

### Post by Rodneyck on 2007-02-07
Very strange. My only other thoughts are to make sure nothing but the basics are plugged into your computer. No wacom pads or usb hardware that might be giving you problems.  Many time it has to do with the graphic driver which is why I asked about your system.  Is it Intel?  

You might also search for help on the debian site, as Dreamlinux is Debian based.

---

### Post by jclmusic on 2007-02-07
my cpu is intel, but my graphics card is nvidia.

---

### Post by FuturePilot on 2007-02-28
This might be a wild shot, but maybe try flashing the BIOS. I had a similar issue with Ubuntu, it kept freezing during the install. After about the 8th try I decided to flash the BIOS and tada it worked.

---

### Post by darkenedday on 2007-03-03
I have also found that the ISO for dreamlinux seems to be somewhat touchy about burning (I had some errors on one of my didsks burned at 16x, 4x managed it though) you may want to try testing the media (if that's an option) I've also found that it also has problems with certain cd-rom drives, I was installing on my sister's PC when it continually froze, I then replaced the cd-rom drive with a newer one I had laying around and it installed quickly and without a hitch, this is an old amd k6-2 machine running at 500mhz with a really old ATI voodoo graphics chip (dreamlinux is said not to like ati, but is very nvidia friendly, this shouldn't be your problem) my recomendation is to try using a different cd-rom drive, maybe you have a slave set up? best advice I can offer, solved the problems on more than just this one pc

hope it helps!

---

