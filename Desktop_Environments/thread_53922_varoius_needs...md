---
title: "varoius needs.."
date: 2005-08-02
forum: Desktop Environments
---

### Post by neighborlee on 2005-08-02
1) how do I make it possible to eject a CD via eject button on CDROM drive ?
2) wondering about status of livecd/installer ( not DVD I dont have dvd burner YET ) and GUI installer..can someone please point me to URL..I checked wiki but im not finding it sadly ;-)

3) are others using gnome with hoary, finding a unstable system ( random crashing)  or is this just me and possible bad ram ( Im thinking I should redownload iso and try again), although windows one day did offer this crud:::

instruction at 0x7c91185 referenced memory at 0x001c6f28. the memory could not be read < got that while in windowsXP one day so I wonder indeed if linux random crashing is symptomatic of this random ram issue and just showing up more often in linux for some reason ??...

thx
nl

---

### Post by ubuntu_demon on 2005-08-03
> **neighborlee]1) how do I make it possible to eject a CD via eject button on CDROM drive ?
[/QUOTE]

I don't know....If you can make it work it will probably be a hack.

cd's and dvd's are mounted in the filesystem. They can only be unmounted (unless forced) if no application is reading from it at that time. So actually this is a good method since it makes it harder to crash your applications on accident by ejecting the cd-rom

also clicking unmount is faster than pushing the cd-rom button (for me at least).


[QUOTE=neighborlee]
2) wondering about status of livecd/installer ( not DVD I dont have dvd burner YET ) and GUI installer..can someone please point me to URL..I checked wiki but im not finding it sadly  said:**
> 

[https://wiki.ubuntu.com/GraphicalInstaller](https://wiki.ubuntu.com/GraphicalInstaller)

they are trying to get this into breezy. Would be very cool if breezy has it :).
If breezy doesn't have it probably breezy+1 will have it.

[QUOTE=neighborlee]
3) are others using gnome with hoary, finding a unstable system ( random crashing)  or is this just me and possible bad ram ( Im thinking I should redownload iso and try again), although windows one day did offer this crud:::

instruction at 0x7c91185 referenced memory at 0x001c6f28. the memory could not be read < got that while in windowsXP one day so I wonder indeed if linux random crashing is symptomatic of this random ram issue and just showing up more often in linux for some reason ??...

thx
nl

Please give us as much information as possible. 

What crashes ? xorg? gdm ? nautilus? your kernel ? something else ?
What are you doing when "it" crashes ?
Are you using backports staging ? (you shouldn't if you want stability)
Are you using remotely mounted partitions ? (sometimes I have some problems with nautilus and samba but I haven't deeply investigated this yet)

---

### Post by az on 2005-08-03
If you do not see the grub menu when you boot, hit escape and boot into memtest86.  Let it run for a few hourse and see if you have some bad ram.

Ejecting a cd by pushing the button is supported by the supermount kernel patch, but, like in windows, it is not completely stable.  So it is not implemented in Ubuntu.

---

### Post by ubuntu_demon on 2005-08-03
[QUOTE=azz]If you do not see the grub menu when you boot, hit escape and boot into memtest86.  Let it run for a few hourse and see if you have some bad ram.
[/QUOTE]

I forgot to tell about that :)

[QUOTE=azz]
Ejecting a cd by pushing the button is supported by the supermount kernel patch, but, like in windows, it is not completely stable.  So it is not implemented in Ubuntu.[/QUOTE]

didn't know about that kernel patch. But I think a kernel patch for something like that is a hack :)

people shouldn't patch their kernel unless absolutely necessary because :
-it can be less secure
-it can introduce instability

---

### Post by neighborlee on 2005-08-03
[QUOTE=azz]If you do not see the grub menu when you boot, hit escape and boot into memtest86.  Let it run for a few hourse and see if you have some bad ram.

Ejecting a cd by pushing the button is supported by the supermount kernel patch, but, like in windows, it is not completely stable.  So it is not implemented in Ubuntu.[/QUOTE]

I am most curious ( and well meaning ) then as to why distros like Suse, Mandrake, Linspire, Xandros and im sure im missing some, ( mepis ?) use supermount ( supermount-ng ? ) if indeed its so unstable why would those fine , competent distros utilize this technology and risk alienating its userbase ( same for windows ) ?

I wonder also what is the proof that it is 'less stable' ?

I appreciate any information you can provide about this issue.

cheers :)
nl

---

### Post by neighborlee on 2005-08-04
[QUOTE=azz]If you do not see the grub menu when you boot, hit escape and boot into memtest86.  Let it run for a few hourse and see if you have some bad ram.

Ejecting a cd by pushing the button is supported by the supermount kernel patch, but, like in windows, it is not completely stable.  So it is not implemented in Ubuntu.[/QUOTE]

is this test a for sure sign of bad ram as in is the  program verifiably accurate ?

thx

---

### Post by ubuntu_demon on 2005-08-05
[QUOTE=neighborlee]is this test a for sure sign of bad ram as in is the  program verifiably accurate ?

thx[/QUOTE]
 you can find info about memtest86 here :
[http://www.memtest86.com](http://www.memtest86.com)

---

### Post by neighborlee on 2005-08-06
[QUOTE=ubuntu_demon]you can find info about memtest86 here :
[http://www.memtest86.com](http://www.memtest86.com)[/QUOTE]

I see no info about it, but I wonder if rambus ( which I have ) returns accurate values for this test..I imagine it makes no difference..?

thx
nl

---

