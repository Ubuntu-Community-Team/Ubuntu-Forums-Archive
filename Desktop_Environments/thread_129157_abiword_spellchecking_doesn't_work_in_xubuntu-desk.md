---
title: "abiword spellchecking doesn't work in xubuntu-desktop"
date: 2006-02-13
forum: Desktop Environments
---

### Post by noalternative on 2006-02-13
[INDENT] I have installed enchant, ispell, and aspell dictionaries, and all the plugins but it still won't work.  I tried to uninstall it, but it wants to uninstall the entire xubuntu-desktop.

This is also a problem in other distros I've tried like feather linux, Luit Linux and Damn Small Linux. When I google this problem, I also see this problem in red hat distros like Suse and Mandrake. I sought help at abiword's mailing list, but they weren't able to offer any solutions. They just said it was a thing with debian.  I am wondering if maybe it would be better to drop it from the distro altogether, and include siag office suite?  If the dictionary won't work in any known linux distro, why include it? [/INDENT]

Ok, I have found a resolution to this problem.

[COLOR="Red"]Problem solved:cool: 

According to this newsgroup thread in [linux.debian.bugs]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/58ad3a3aa1bffd5c/f63feef6cb9316c7?lnk=st&q=abiword+ispell&rnum=2#f63feef6cb9316c7"), abiword 2.x is looking for the dictionaries in the wrong place.

[INDENT] Quote:
According to strace output, looks for .hash files (deutsch.hash) only
in /usr/share/enchant/ispell and ~/.enchant/ispell. These directories
do not exist. Creating them and symlinks to .hash files makes abiword
actually perform the spell checking.[/INDENT]



In xubuntu you open up terminal, then enter su, then your password, enter "rox- filer", you will get rox filer with root privleges, then to go to /usr/share, then you right click and create a new folder called in enchant. Then you open the enchant folder. Then you open up a second root rox-filer through another terminal, and go to /usr/lib. Find the ispell folder then drag the ispell folder to the new /usr/share/enchant folder, and try to drop it. A dialogue will appear giving you the option to move, copy or link it. Choose link. A symlink will be created to /usr/lib/ispell. Now the dictionary in abiword will work. At least it did for me. I don't know where aspell dictionaries are located, but you probably have to go though the same process to get them working in abiword.

BTW, I think I remember installing ispell to get the dictionary working, so if you can't find the ispell folder in /user/lib you probably need to install it with apt-get or update manager.[/COLOR]

---

### Post by nalmeth on 2006-02-13
Is it just in xfce that you have this problem? Spellcheck works fine for me in gnome, and no installing extra dictionaries or libraries.

---

### Post by noalternative on 2006-02-13
[QUOTE=nalmeth]Is it just in xfce that you have this problem? Spellcheck works fine for me in gnome, and no installing extra dictionaries or libraries.[/QUOTE]

No, it also has the problem with fluxbox and icewm in damn small and feather.  There is a reason I don't use gnome.  It just runs too slow on my computer.

---

### Post by nalmeth on 2006-02-13
That's weird. Can you try gnome just to make sure it's not related to the desktop environment being used? Maybe try enlightenment too! 

Yeah, if I was still using my old computer, I'd probably go with something more compact, but on a fast computer, I'm willing to spend some cpu.

---

### Post by noalternative on 2006-02-14
I don't have gnome installed.

---

### Post by noalternative on 2006-02-17
[QUOTE=noalternative][INDENT] I have installed enchant, ispell, and aspell dictionaries, and all the plugins but it still won't work.  I tried to uninstall it, but it wants to uninstall the entire xubuntu-desktop.

This is also a problem in other distros I've tried like feather linux, Luit Linux and Damn Small Linux. When I google this problem, I also see this problem in red hat distros like Suse and Mandrake. I sought help at abiword's mailing list, but they weren't able to offer any solutions. They just said it was a thing with debian.  I am wondering if maybe it would be better to drop it from the distro altogether, and include siag office suite?  If the dictionary won't work in any known linux distro, why include it? [/INDENT]

Ok, I have found a resolution to this problem.

[COLOR="Red"]Problem solved:cool: 

According to this newsgroup thread in [linux.debian.bugs]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/58ad3a3aa1bffd5c/f63feef6cb9316c7?lnk=st&q=abiword+ispell&rnum=2#f63feef6cb9316c7"), abiword 2.x is looking for the dictionaries in the wrong place.

[INDENT] Quote:
According to strace output, looks for .hash files (deutsch.hash) only
in /usr/share/enchant/ispell and ~/.enchant/ispell. These directories
do not exist. Creating them and symlinks to .hash files makes abiword
actually perform the spell checking.[/INDENT]



In xubuntu you open up terminal, then enter su, then your password, enter "rox- filer", you will get rox filer with root privleges, then to go to /usr/share, then you right click and create a new folder called in enchant. Then you open the enchant folder. Then you open up a second root rox-filer through another terminal, and go to /usr/lib. Find the ispell folder then drag the ispell folder to the new /usr/share/enchant folder, and try to drop it. A dialogue will appear giving you the option to move, copy or link it. Choose link. A symlink will be created to /usr/lib/ispell. Now the dictionary in abiword will work. At least it did for me. I don't know where aspell dictionaries are located, but you probably have to go though the same process to get them working in abiword.

BTW, I think I remember installing ispell to get the dictionary working, so if you can't find the ispell folder in /user/lib you probably need to install it with apt-get or update manager.[/COLOR][/QUOTE]


KICK PROBLEM SOLVED

---

### Post by noalternative on 2006-04-16
[QUOTE=nalmeth]Is it just in xfce that you have this problem? Spellcheck works fine for me in gnome, and no installing extra dictionaries or libraries.[/QUOTE]

kicken it.

---

### Post by megabyte405 on 2006-04-19
AbiWord in Breezy should work just fine with aspell and aspell dictionaries (you need both components, not just the dictionaries, as Enchant is just a front-end to aspell, which might be where you were tripped up).  ispell is really a less-than-optimal solution.  For me, I have aspell and aspell-en, as well was aspell-es  (packages) installed with apt-get.  It is possible that these packages only come by default with the gnome install.

You also need a libenchant, but that's a hard dependency in apt, not a "recommends", so you should be OK.

Sorry for the very late reply, just going through and looking for people to help with AbiWord (I'm a dev...)

--Ryan

---

### Post by sidling on 2008-03-22
Hi,

I'm using sidux with kde and spent hours in abiword's spellcheking... thanks to your post I finally got it working!!! :)

greetings
florian

---

