---
title: "UT2004 64bit: very slow anti tcc check"
date: 2011-02-04
forum: Gaming &amp; Leisure
---

### Post by gamon on 2011-02-04
Hi, I'm playing Unreal Tournament 2004 on Ubuntu 10.10 64bit: when I connect to a server that embeds Anti TCC (only tested version 2009r6) I experience quite long freeze periods (30 seconds up to more than 1 minute, and yes, I mean complete freeze, not just a slow down) during the Anti TCC check at the start of online matches, precisely during "verifying classes" or "verifying your client" (depending on how Anti TCC is set on the server) operation; after that the game runs flawlessly. Sometimes those long freezes make me get even kicked for idling.
This does** not** happen on Ubuntu 10.10 32bit at all (installed on the same machine), so it's obviously architecture-related.
Is there somebody who can reproduce the problem? Or know how to solve it? Or just wants to say his/her opinion?
Thank you!

---

### Post by rizzeh on 2011-02-05
Same thing happens here, i put up with it tbh, no big deal.

---

### Post by gamon on 2011-02-05
Thanks rizzeh, but this is not how linux works: if it's a bug in Anti TCC we should report it to the developers, not just "put up with it" ;)
Maybe I'll wait for somebody else to confirm the issue, then I'll report this, if you want you can then help testing it, keep reading this to see how things evolve.

EDIT: I can reproduce the issue also on Arch Linux 64 bit

---

### Post by rizzeh on 2011-02-05
the bug is also on debian 64x, both squeeze and sid. 
But really it ain't half as bad as UT'99 anti-cheat client problems. End up playing ut in wine zzz.

---

### Post by gamon on 2011-02-05
Good job, now 4 distros are tested!
I don't expect thousands of people replying to this thread, as I don't know how many use UT2k4 on Linux 64bit distros, so I've reported the bug to Wormbo anyway, this is the link:
[http://www.unrealadmin.org/forums/showthread.php?t=7656&page=2#post160463](http://www.unrealadmin.org/forums/showthread.php?t=7656&page=2#post160463)

@ rizzeh
I don't have UT'99, so I cannot test its anti-cheat here, but to end up playing in wine it's got to be very buggy :(

EDIT:
As Anti TCC seems not to be maintained any  longer, for those reading here with the same problem, the next-best  workaround is to launch the 32-bit version of UT2004 from your 64-bit  system by installing 32-bit libraries: this has no impact at all on the  game performance, so have no fear.
In Arch Linux 64, the libraries to install are: (for other distros, the names could vary)

lib32-sdl
lib32-libstdc++5
lib32-nvidia-utils (this is for NVidia cards, if you have an ATI card or  you use another driver anyway, you have to install the analogous 32-bit  version of this package, if applicable)
lib32-alsa-oss
lib32-openal

But this is not enough, you have to link the 32-bit libSDL and openal  into the ...ut2004/System/ directory: (here I suppose you have installed  the game in ~/.ut2004/) (the lib32 path could change depending on your  distro)

$ mv ~/.ut2004/System/libSDL-1.2.so.0 ~/.ut2004/System/libSDL-1.2.so.0.backup
$ mv ~/.ut2004/System/openal.so ~/.ut2004/System/openal.so.backup
$ ln -s /usr/lib32/libSDL-1.2.so.0 ~/.ut2004/System/libSDL-1.2.so.0
$ ln -s /usr/lib32/libopenal.so ~/.ut2004/System/openal.so

Lastly, don't forget to edit your .../ut2004/ut2004 script to launch the  32-bit executable inside System directory (thus actually restoring it  to default).
Now you should be done, enjoy!
 		 	 		 		 		 		 		 		 		 		 		 	 		 			 			 				[IMG]http://www.unrealadmin.org/forums/images/misc/progress.gif[/IMG] 				[[IMG]http://www.unrealadmin.org/forums/images/buttons/edit.gif[/IMG]]("http://www.unrealadmin.org/forums/editpost.php?do=editpost&p=160536")

---

