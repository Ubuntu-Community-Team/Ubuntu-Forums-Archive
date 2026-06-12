---
title: "Tiberian Sun Wine installation problem"
date: 2009-07-19
forum: Gaming &amp; Leisure
---

### Post by lacoidx on 2009-07-19
Hello!

I've just registered because i've googled the half of the net for a solution for this problem, pointlessly.

Read through many threads and it seems that no one had this problem before, i just guess that someone from here did.

So, here's the problem:

I have NRG images of the game cd's and want to install it with WINE on Jaunty, but of course it's a little tricky to mount NRG images into a filesystem directory, so i tried nrg2iso to convert them into ISO format then used the

mount -o loop ../cdimage.iso /media/iso

command. Then ran setup.exe from a file manager (with Win98 compatibility and virtual desktop wine config) and a window popped up with the message: "Please insert CD-ROM disc",  and i was unable to advance. Of course /media/iso is set as a CD-ROM drive in winecfg, as well as /media/cdrom0. Same result running from console,
but it gives an error message: "Warning: could not find DOS drive for current working directory '/home/nlcreations', starting in the Windows directory."

Then I tried to install the game on a virtual Windows XP (in Win98 compatibility mode), using the same ISO file. The result was exactly the same.
I think the problem is in the converted ISO image.

I've also tried to install Daemon Tools on this virtual box with no success, so somehow i want to try mounting the NRG file onto my filesystem without conversion. Found that fusenrg shall do that, but when i run it (as root), i get the error message: "Permission denied."

So i stuck here, if someone had this (or kind of this) problem please help me!

Thanks,

a linux gaming newbie

---

### Post by Grishka on 2009-07-20
use the original CD.

---

### Post by Clorow on 2009-07-20
Yeah, .nrg images are in no way standards. Use the original CDs - we're assuming here that you didn't pirate the games.

Also, this belongs on the Wine board - read the stickies!

---

