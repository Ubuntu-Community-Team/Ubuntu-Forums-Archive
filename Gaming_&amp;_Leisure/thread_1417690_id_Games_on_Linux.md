---
title: "id Games on Linux"
date: 2010-02-27
forum: Gaming &amp; Leisure
---

### Post by talhaguy on 2010-02-27
Anyone here have experience with installing id games that are ported to Linux?

I am considering doing it, so I was wondering if there are any hiccups or whatnot.

---

### Post by ShadowTek on 2010-02-27
I could only get Doom3 to work by switching to OSS sound, but I had to disable its surround sound because it wouldn't work properly. Other than that, it worked fine for me.

You should find plenty of info for particular games if you do a forum search for the name of the game.

---

### Post by calis1981 on 2010-02-28
id software games can be pretty easy to install, there are a lot of guide to help get through any troubles you have, i just got return to castle wolfenstein work natively under linux, i had the original, not GOTY, so it was a bit of a pain, had to patch a windows install of it to 1.41 before it would work natively

---

### Post by MaximB on 2010-02-28
ALL id software games that have a native Linux client (pretty much ALL id software's games) run on Linux and easily installed or/and have a native Linux client.

---

### Post by Technophobia on 2010-02-28
[http://zerowing.idsoftware.com/](http://zerowing.idsoftware.com/)

Haven't had a single problem. Not even with pulse.

---

### Post by Brebs on 2010-03-01
> **ShadowTek said:**
> I could only get Doom3 to work by switching to OSS sound
Presumably that's pulseaudio screwing things up again. ALSA should of course work.

> **ShadowTek said:**
> but I had to disable its surround sound because it wouldn't work properly.
ID screwed up the surround sound in Linux, but there is [a fix](http://forums.gentoo.org/viewtopic-p-4173170.html#4173170).

---

### Post by ShadowTek on 2010-03-01
> **Brebs said:**
> Presumably that's pulseaudio screwing things up again. ALSA should of course work.
Actually, if I "sudo killall pulseaudio", ALSA won't work the next time I start Doom3.


> ID screwed up the surround sound in Linux, but there is [a fix]("http://forums.gentoo.org/viewtopic-p-4173170.html#4173170").lol  As I've said before, I have an additional problem that isn't covered in the thread that you are referencing.
[http://ubuntuforums.org/showpost.php?p=8666055&postcount=12](http://ubuntuforums.org/showpost.php?p=8666055&postcount=12)

I describe the issue here:
[http://ubuntuforums.org/showpost.php?p=8229497&postcount=17](http://ubuntuforums.org/showpost.php?p=8229497&postcount=17)

I'd still like to solve the problem if anyone knows what the deal is.

---

### Post by rajeev1204 on 2010-03-01
The OSS  fix was needed way back in dapper drake upto 9.04 i would say.

Quake 4 works just fine with pulseaudio, so now you can hear music and frag at the same time :)

---

### Post by juancarlospaco on 2010-03-01
I have installed Doom 3, installer of 1.3/1.4 version dont work, i use version 1.1.

Try to install Resurrection Of Evil (expansion pack CD) dont work, because an internal error.

Try to install Quake 4, the installer on ID Software FTP seems corrupted, all of them,
downloaded on Linux, with WGET, CRC fail.

Quake Wars i installed the Demo works perfectly.

:)

---

### Post by u235sentinel on 2010-03-01
> **juancarlospaco said:**
> I have installed Doom 3, installer of 1.3/1.4 version dont work, i use version 1.1.

Try to install Resurrection Of Evil (expansion pack CD) dont work, because an internal error.

Try to install Quake 4, the installer on ID Software FTP seems corrupted, all of them,
downloaded on Linux, with WGET, CRC fail.

Quake Wars i installed the Demo works perfectly.

:)

the corruption problems with Quake 4.. I wonder if it's the same problem I had.  I purchased a copy on DVD thinking it would work.  CRC errors all the way with the ID installer from their ftp site.  They sent me another but this time it was a CD version.  Works just fine.  

The DVD apparently was good.  Just for some reason it had trouble installing with the linux installer.  Windows installed just fine from the disk I noticed.

A friend has a DVD version which I had the same problems under linux.  CD copies worked great.  Didn't get very far in testing when I figured out which works and which didn't :-)

---

### Post by ShadowTek on 2010-03-01
> **juancarlospaco said:**
> Try to install Quake 4, the installer on ID Software FTP seems corrupted, all of them,
downloaded on Linux, with WGET, CRC fail.


If the FTP files are corrupted, you could try getting it from *their* torrent. That's where I got my Doom3 installer.

---

### Post by juancarlospaco on 2010-03-01
> **ShadowTek said:**
> If the FTP files are corrupted, you could try getting it from *their* torrent. That's where I got my Doom3 installer.

Doom3 installers on ID Software FTP works perfectly for me, 
but the Quake 4 seems broken.

---

### Post by Brebs on 2010-03-02
For installing Quake 4 from DVD, see [my script](http://forums.fedoraforum.org/showthread.php?t=189064).

Regarding CRC errors - there's not much we can do, if your Internet connection is so crappy.

---

### Post by u235sentinel on 2010-03-02
> **juancarlospaco said:**
> Doom3 installers on ID Software FTP works perfectly for me, 
but the Quake 4 seems broken.

I'll bet it's crc errors from the Quake disk.  I'm also betting you had the same problems I had with the installer.  I had another copy sent to me (cd version) and it worked fine.  So now I have a couple copies my kids and I play on.  Works for me but just make sure you have the cd version.

---

### Post by juancarlospaco on 2010-03-02
> **u235sentinel said:**
> I'll bet it's crc errors from the Quake disk.  I'm also betting you had the same problems I had with the installer.  I had another copy sent to me (cd version) and it worked fine.  So now I have a couple copies my kids and I play on.  Works for me but just make sure you have the cd version.

No, i got the DVD version, with checked integrity, 
but without mounting the DVD i run the installer, 
on the beginning it self-checks and fails.

---

### Post by juancarlospaco on 2010-03-02
> **Brebs said:**
> For installing Quake 4 from DVD, see [my script](http://forums.fedoraforum.org/showthread.php?t=189064).


I got Quake 4 from DVD, but i dont have the paths on the script.

cd ~/.gvfs/QUAKE4.iso/SETUP/Data
bash: cd: /home/juan/.gvfs/QUAKE4.iso/SETUP/Data: No existe el fichero ó directorio
cd ~/.gvfs/QUAKE4.iso/SETUP/DATA
bash: cd: /home/juan/.gvfs/QUAKE4.iso/SETUP/Data: No existe el fichero ó directorio
cd ~/.gvfs/QUAKE4.iso/SETUP/RSRC
ls
AUTORUN.EXE  QUAKE4.ICO  UNINSTAL.EXE


I have /SETUP/RSRC and dont have /Setup/Data on my Quake 4 DVD :(

also i have on the DVD root dir:
SETUP_1.BIN, (...), SETUP_5.BIN

---

### Post by caravel on 2010-03-02
I have Doom3/RoE and Quake4 all running perfectly.  Just ensure you don't run the game as root.  It's a case of first running the installer as root, then dropping in the paks from you disc(s) (don't overwrite any paks provided by the installer) and then run the game as a normal user.  For Quake4 for you'll have to edit the config file in your ~ to change the language from spanish to english (unless of course you want it in Spanish) but that's it.

---

### Post by Brebs on 2010-03-02
> **juancarlospaco said:**
> SETUP_1.BIN, (...), SETUP_5.BIN
They've changed the installation routine, just to annoy us. The [Gentoo installer](http://sources.gentoo.org/viewcvs.py/*checkout*/gentoo-x86/games-fps/quake4-data/quake4-data-1.0.2147.12.ebuild) wouldn't handle your DVD either :(

---

### Post by juancarlospaco on 2010-03-02
> **caravel said:**
> I have Doom3/RoE

How do you install RoE please ???

---

### Post by handy on 2010-03-03
The following link, shows how well id games Quake engine is functioning, on an ATi HD2600Pro/256 card, using Arch & the -git open source drivers:

[http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-15774-26987-2834](http://global.phoronix-test-suite.com/index.php?k=profile&u=anon-15774-26987-2834)

Which, when I watched the Phoronix Test Suite go through the motions with the Quake engine games, was smooth as can be, & actually awesome, as I saw just how many people/bots were playing simultaneously.

The id Quake engine games were incredibly fast & smooth all the way.

Bodes well for ATi owners in the near future I think... ;)

---

