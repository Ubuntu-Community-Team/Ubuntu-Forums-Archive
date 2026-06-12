---
title: "how do i copy dvds?"
date: 2006-02-18
forum: Desktop Environments
---

### Post by kasemodz on 2006-02-18
well the title says it all. How do i copy dvds? I've installed k3b but somehow i think it only supports cd copying.

---

### Post by alfonz on 2006-02-18
try installing [dvdrip]("http://www.exit1.org/dvdrip/")

---

### Post by nalmeth on 2006-02-18
k3b will copy dvds. Just right click on the lower half of the window to add shortcuts like "copy DVD" "encode video" etc.

Most video DVD's will be too big for a DVD-r, so unless you have dual-layer DVD's, you'll need DVD Shrink to shrink the VIDEO_TS files to 4.4 gigs. Here's the howto for setting up DVD Shrink

[http://ubuntuforums.org/showthread.php?t=78611](http://ubuntuforums.org/showthread.php?t=78611)

Shrink the files either to new Video_ts, or to an .iso image. I've had more success with the latter. Use k3b to do the actual burning.

If you just want to encode the DVD to an avi you can use dvd::rip, but I prefer acidrip.

sudo apt-get install acidrip

EDIT: Also make sure you have libdvdcss2 installed!

---

### Post by ubuntu-mike022465 on 2006-02-18
You can also try xdvdshrink (the linux version) that way you don't have to use wine, but the only problem with that is you won't get your menus as they are now.  As far as I know, it doesn't support dual layer burning.

Have fun.  \\:D/ 


M

---

### Post by syklitengutt on 2006-02-18
is there a prog with gui like xdvdshrink that also 
copy the menu like dvdshrink for windows does?

---

### Post by monkeywork on 2006-02-18
I personally stick with DVD Decrypter and DVD Shrink running them via Wine.  I decrypt from DVD -> ISO then ISO -> Shrink -> Shrunk ISO then burn by right clicking the ISO in gnome and choosing burn.

---

### Post by Treebeard on 2006-02-18
I use 'dvdbackup' to copy to disk, 
'mkisofs' to create an iso and 'dvdrecord' to burn the iso to DVD.

I found this how-to on the net:
[http://dvd.chevelless230.com/]("http://dvd.chevelless230.com/")

But I guess it's easier with a GUI :-)

---

### Post by ubuntu-mike022465 on 2006-02-18
Additionally, you can grab a copy of it from [http://distro.ibiblio.org/pub/linux/distributions/texstar/pclinuxos/apt/pclinuxos/2004/RPMS.updates/dvdshrink-2.6.1-1tex.noarch.rpm](http://distro.ibiblio.org/pub/linux/distributions/texstar/pclinuxos/apt/pclinuxos/2004/RPMS.updates/dvdshrink-2.6.1-1tex.noarch.rpm)
and use Alien or kpackage to install it.

---

### Post by ions on 2006-07-02
Put the DVD you want to copy in the drive and...

$ dd if=/dev/dvd of=DVD.iso bs=2048

You can also use vobcopy.  Although I haven't tried it on Ubuntu yet it goes something like:

$ vobcopy -m

---

### Post by Shampyon on 2006-07-05
I've found it pretty easy so far to use k9copy (installed through Syanaptic with all repositories enabled). 
Disc in > Reads > Rips > Burns/Burns .iso
Options are pretty limited for folks used to DVD Decrypter and DVD Shrink, but it's worked pretty well for me so far.

---

### Post by orb9220 on 2006-07-06
Does winAvi work with wine? 

I used it all the time in windows. And it is a great converter and encoder

Select avi,mpegs,mov,wmv and convert into one another or VCD,Svcd, or my fav DVD.

---

