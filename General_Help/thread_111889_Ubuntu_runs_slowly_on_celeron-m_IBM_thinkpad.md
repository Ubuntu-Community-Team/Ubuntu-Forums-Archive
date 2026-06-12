---
title: "Ubuntu runs slowly on celeron-m IBM thinkpad"
date: 2006-01-03
forum: General Help
---

### Post by th3james on 2006-01-03
Hi

Im running breezy on an IBM thinkpad. Its hardly the highest spec ever:

celeron-M 1.3Ghz (i believe this is supposed to equate to a 2.4 desktop processor)
256 ram
64mb shared intel graphics
20 gig HDD

however, the performance its giving me is very poor in ubuntu, and its worse than i think it should be by a long way.
the performance is so poor i installed enlightenment, and integrated it into gnome in an attempt to speed it up, it still lags dreadfully.
Some examples of performance:
applications like konqueror and amaroK take about 30 seconds to start, with 100% CPU usage for the duration
the screen display lags poorly when switching apps, or desktops
sound crackles if it is being played when i try 2 perform even the simplest tasks e.g. switching desktops.

as you would expect, with such a small amount of ram, i am eating into swap, but this performance is still really poor
to test out if it was my installation, i tried a knoppix livecd to see if the performance was better, its performance was much faster, and alot closer to what i would expect from this spec. when i tried an ubuntu livecd, the performance was the same as it is for my ubuntu installation

i have ubuntu installed on two desktops, which are slightly more powerful, and the performance is immeasurably higher,

any suggestions as to whether or not this performance is normal, or any ways to improve it would be appreciated.

here are some readouts that may be helpful:

cox@teh:~$ sudo hdparm /dev/hda
Password:

/dev/hda:
multcount = 0 (off)
IO_support = 0 (default 16-bit)
unmaskirq = 0 (off)
using_dma = 1 (on)
keepsettings = 0 (off)
readonly = 0 (off)
readahead = 256 (on)
geometry = 62016/15/63, sectors = 58605120, start = 0
cox@teh:~$ sudo hdparm -Tt /dev/hda

/dev/hda:
Timing cached reads: 1948 MB in 2.00 seconds = 972.20 MB/sec
Timing buffered disk reads: 34 MB in 3.10 seconds = 10.97 MB/sec

thanks in advance

---

### Post by kenweill on 2006-01-03
try to add "noapic" and "apic=off" in your kernel parameter

See if it works. I've had problems on IBM machines before and that solves my problem. I hope it works for you too.

---

### Post by th3james on 2006-01-03
Sorry, your gonna have to help me, how do i add those to my kernel parameter?

thanks for the quick reply, this forum does seem to be great compared to some of the others ive used

---

### Post by kenweill on 2006-01-04
Open a terminal. Then do type this command.

sudo gedit /boot/grub/menu.lst

after that, search for the line with something that contains vmlinuz.
I can't describe it coz im using Windows as of now, but the last two word in the line is "quiet" and "splash". From there, add the word "noapic" and "apic=off".

Then save it then exit.

Its usually found in the last portion of the file. The line without the "#" sign. The lines with "#" sign are just comments.

See if it works.

---

### Post by kenweill on 2006-01-04
Look for this line: (or something like this, it depends on your installation)

kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash

and then add "noapic" and "apic=off".
It should now be

kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash noapic apic=off

---

