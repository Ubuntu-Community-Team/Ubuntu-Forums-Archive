---
title: "Pcsx2 help"
date: 2010-12-19
forum: Gaming &amp; Leisure
---

### Post by surfingonmusic on 2010-12-19
i'm trying to build pcxs2 from source from what [this guy]("http://ubuntuforums.org/showthread.php?t=399165&page=16") says to do
but i keep getting this error.

[I][B]zerogs.h:41: fatal error: Cg/cg.h: No such file or directory
compilation terminated.
make[1]: *** [libZeroGSogl_a-GSmain.o] Error 1
make[1]: Leaving directory `/home/paul/pcsx2/plugins/gs/zerogs/opengl'
make: *** [install-recursive] Error 1
Error with building plugins[/B][/I]
 
it wont recognise the plugins! i have them in a folder on my desktop.

---

### Post by thatguruguy on 2010-12-19
If you are running 32-bit ubuntu, you can use the official pcsx2 repository, available [here]("https://launchpad.net/%7Egregory-hainaut/+archive/pcsx2.official.ppa").

If you are running 64-bit, you can install the repository [here]("https://launchpad.net/%7Emicove/+archive/experimental").

In either event, once you install the appropriate repository you can simply install pcsx2 from synaptic.

---

### Post by surfingonmusic on 2010-12-20
it still says 'could not open /plugins directory' same for the bios

this is the error in the terminal 
(<unknown>:9938): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.26.0/gobject/gsignal.c:3081: signal name `depressed' is invalid for instance `0x8c61418'

=/thanks for this btw

---

### Post by surfingonmusic on 2010-12-20
update! 
got it working sort of, now it's giving me this error when i try to load a game

(IsoFS) Invalid partition descriptor encountered at block 0x10: ''
Closing plugins...
    Closing SPU2
    Closing PAD
    Closing GS
(pxActionEvent) IsoFS could not find the root directory on the ISO image.(thread:EE Core)
    File/Object: IsoFS

i have a game in the cddrive and i  tried to load an IMG

---

### Post by thatguruguy on 2010-12-20
Sounds like the iso or disc is bad. Does this happen on every iso you have?

---

### Post by surfingonmusic on 2010-12-22
ok now i'm not getting the error anymore, it just crashes straight away. it does give me a message though, had to crash it several times to get the time to read it.

HLE warning: ELF file does not have a path

i'm not trying to load an ELF file though, i get the same message when i DO try and load an elf. this happens for every disc, iso and elf file yup :(

---

### Post by wingnux on 2010-12-23
You'll have more luck asking on the official PCSX2 forum: forums.pcsx2.net

---

### Post by surfingonmusic on 2010-12-24
ok it works now...nearly
tried to load final fantasy X and it just says 

Impossible block clearing failure

doesn't crash and everything seems to be working, kingdom hearts works (i use the cd for that and iso for final fantasy)

---

### Post by thatguruguy on 2010-12-24
Not every game works.

---

