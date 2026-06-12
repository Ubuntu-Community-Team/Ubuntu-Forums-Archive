---
title: "Fiddle the Mac OS X Starcraft Installer for Linux?"
date: 2006-03-11
forum: Gaming &amp; Leisure
---

### Post by ed_agamemnon on 2006-03-11
Does anyone think it might be possible to fiddle the Mac OS X Starcraft Installer to run the game natively in Linux? A .dmg installer is available from Blizzard ([http://www.blizzard.com/support/?id=msc0411p]("http://www.blizzard.com/support/?id=msc0411p")) - but unfortunately I haven't as yet got inside the archive. The .dmg file format is a Mac-only thing and is (I think) an equivalent to .iso disc images. I've had no luck using dmg2iso (either with the Perl script or win32 binary) to convert the archive.

Can someone with a Mac unpack/repack the installer files for Linux and host them somewhere?

I know you can get good results running Starcraft under Wine; I'm just curious... :)

---

### Post by knalle on 2006-03-11
WINE is a windows emulation layer so the Mac installer will not work afik

---

### Post by simplyw00x on 2006-03-11
OSX runs a UNIX base (Darwin). I think the OP is working off this starting-point to get it to run on linux. I'd say it wasn't possible, due to shared libraries and cuh that it would depend on, but have a go.

---

### Post by ed_agamemnon on 2006-03-11
I'm not asking for help running a Mac binary under Wine (wouldn't that be a bit stupid?)... I want to know how I can unpack a Mac .dmg archive (or if someone with a Mac can do it for me) so I can look at the contents...

---

### Post by ubtpenguin on 2006-03-11
well,

Only method I know is that 

Just find friend who has mac and open dmg and copy contents to CD.

---

### Post by molai2 on 2006-03-12
Try this program, [DMG2ISO]("http://vu1tur.eu.org/tools/"). It can convert a dmg file to an iso image. I ran across this a few days ago but never got a chance to try it out. 

Let us know if it works!

---

### Post by engla on 2006-03-12
If anyone wants to know, I can play starcraft with OSX running in a window on my ubuntu install.. (mac-on-linux project)

It's quite nice, since Starcraft doesn't do any hardware rendering it runs just like it uses to, everything works.

Sadly, 3D is not handled at all by mac-on-linux so Warcraft 3 doesn't work at all.

---

### Post by ed_agamemnon on 2006-03-13
Great! The Mac-on-Linux thing is dead interesting! :) 

Sadly I've been down the dmg2iso route and can't get it to successfully convert the .dmg either under Windows or Linux. There's quite a lot of information on that program on the forum and a good number of people sharing similar problems unfortunately!

Could you (engla) maybe convert the file for me from inside your mac-on-linux?
Or anyone with a real Mac? - I just want the files inside!

---

### Post by arcanistherogue on 2006-03-13
Wow, that just might make an apple laptop my best laptop choice.  I was worried about gaming on teh go, I really want:

Warcraft 2
Quake 1-3
Doom 1-2
Starcraft
Ut1999

Quakes, dooms, and unreal are covered by linux, but it would be awesome to get my favorite strategy games working with mac on linux.

---

### Post by slux on 2006-03-14
Is there an universal binary version of Starcraft available? If not, it's a totally pointless excercise to fiddle with the PPC stuff on a PC. You won't get it to run except with emulation...

---

### Post by ed_agamemnon on 2006-03-14
From reading the release notes with the Mac OS X Installer, I'm fairly certain that it installs the PC version directly from the original Starcraft CD. There's been no Starcraft release other than the PC one that I know of and is named on the Blizzard website as "PC/Mac Hybrid CD-ROM"... Therefore I assume that the binaries are indeed universal. - I could always be wrong though :)

---

### Post by arcanistherogue on 2006-03-14
I am a pretty big gamer, and have installed SC on many computers in a LAN.  I also installed it on about 3 macs when i was over one of my friends house. 

The installer uses all the files from the CD, they are all on there, as with all blizzard games.

Anyway, could you do that same thing you are using mac on linux for with VMWare and windows?  I have an x86 system dual booting XP and Ubuntu, could i get into windows on ubunutu and run starcraft?  That would be amazing, as I could run Xfire also.

---

### Post by jdodson on 2006-03-15
Starcraft running on vanilla wine works well enough.  Unless you are on PPC or some other arch.

Oh well, the joys^H^H^H^Hevils of propretary software.

---

