---
title: "DVD writing probs, K3B, GnomeBaker + Bonfire"
date: 2006-06-14
forum: Desktop Environments
---

### Post by meatbop on 2006-06-14
Hi

I've just jumped ship to Linux from windows, been gong well so far, my wireless network card autodected and "just worked" saving me the ndis wrapper hassles that put me off on my last attempt with knoppix, but I'm having grief burning DVD's.

I'm trying to burn data DVD-R's using a Pioneer 109.  The files are mixed media (avi etc) on an NTFS partition.  The built in functionality in the file browser works OK but writing the ISO before burning just takes too long.

I installed K3B after reading that it's the most featurefull, it works but only at < half the speed the media is rated for and I'm setting the burn speed to, ie 8 speed burns at ~4 speed, 4x at ~2x. 

 In either case the speed occasionaly drops to 0.  Checking the logs there is always at least one instance of  "*:-? the LUN appears to be stuck writing LBA=310h, retry in 141ms*" though this does not happen immediately before the speed drop.

On one occasion the burn failed completely, in the error log it gives "[I]:-? the LUN appears to be stuck writing LBA=121b10h, retry in 0ms
:-[ WRITE@LBA=80121b10h failed with SK=2h/ASC=04h/ACQ=08h]: Resource temporarily unavailable
:-( write failed: Resource temporarily unavailable[/I]"

I've attached the logs for a few attempts, accidentaly didn't save the one for the total fail though.

Also while burning the file manager "*You have inserted a blank disk*" dialogue box sometimes pops up repeatedly.

GnomeBaker seems to only be able to burn DVD ISO's - does "on the fly" mean that you don't have to do an ISO first?  Is there an additional package I can add to give it this functionality?

Bonfire gives the "unable to access" dialogue when I drag the files in from the the file manager.  Does it need write access to the files it's burning for some reason?

If anyone can help me fix the problem with one of these three, or recomend another application to use I'd be gratefull.

---

### Post by mjm115 on 2006-06-14
If you're using K3B, you have to disable KDED in System Settings.  This is a [known issue]("http://k3b.plainblack.com/message-board/slow-burns-and-a-fix") in K3B.

---

### Post by meatbop on 2006-06-14
Thanks for the quick answer, I'm using Gnome rather than KDE but I'll disable automount and try again.

Edit: No joy, I went to System > Preferences > Removeable media and unchecked the "Mount removable media when inserted" option but the disk still appears on the desktop and when I try burning it's still at half speed.

---

### Post by DDM on 2006-06-14
I'm in the same boat here. My 8x DVD burner burns at 2.5x, making me very sad.

---

### Post by zad on 2006-06-15
Where could i find Bonfire ive googled it but cant find it :S anyone help please :)

btw ive got the opposite to you mine wont burn at 4x i select it but it still goes to 8x :(

zad

---

### Post by meatbop on 2006-06-15
[QUOTE=zad]Where could i find Bonfire?[/QUOTE]

[http://perso.orange.fr/bonfire/index.htm](http://perso.orange.fr/bonfire/index.htm)

---

### Post by zad on 2006-06-15
ta :)

zad

---

### Post by meatbop on 2006-06-15
Unchecking automount solved the problem, though it didn't seem to change at first, even after a restart, everything groovy now though, thanks mjm115.

Have you tried this DDM?

---

### Post by goahead on 2006-06-15
Having the same problem here, burn speed drops to 0 when it has burnt around 47%...

This time it only got to 0,6% :(

 25493504/4436852736 ( 0.6%) @0.0x, remaining 842:07
  25493504/4436852736 ( 0.6%) @0.0x, remaining 859:25
  25493504/4436852736 ( 0.6%) @0.0x, remaining 868:04
  25493504/4436852736 ( 0.6%) @0.0x, remaining 879:36
  25493504/4436852736 ( 0.6%) @0.0x, remaining 888:15
:-( unable to WRITE@LBA=30a0h: Input/output error
:-( write failed: Input/output error
/dev/hdd: flushing cache
:-[ FLUSH CACHE failed with SK=2h/ASC=3Ah/ACQ=00h]: No medium found
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=2h/ASC=3Ah/ACQ=00h]: No medium found


Some1 said that my burner must be broken, but it aint its brand new and burning works like a charm in suse10.1 and windoze..

---

