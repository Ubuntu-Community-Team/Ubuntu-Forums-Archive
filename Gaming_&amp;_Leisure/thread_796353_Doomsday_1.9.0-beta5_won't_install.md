---
title: "Doomsday 1.9.0-beta5 won't install?"
date: 2008-05-16
forum: Gaming &amp; Leisure
---

### Post by OpposingForce on 2008-05-16
Hi everyone.  I used to use ubuntu but I had to go back to windows when I got an XFI card which ubuntu didn't support.  But this week I just decided to go back, got the 8.04 distro, and followed a tutorial on these forums on how to install OSS4 which has some XFI support.  Well the sound works flawlessly now *knocks on wood* and everything is going well with linux for now.  Recently I decided I want to play one of my favorite PC games, doom.  So I got the "doomsday engine" because I have it on windows and it runs perfectly.  I got the latest version for linux and unpacked it, and everything.  I followed the readme instructions down to the 't' but something went wrong on the "sudo make install"

It started installing, got around to 30ish percent then I got this:

```

*snip TON of files above *snip*
writing ../../plugins/doom64tc/defs/anim.ded as defs/doom64tc/anim.ded
writing ../../plugins/doom64tc/defs/examplexg.ded as defs/doom64tc/examplexg.ded
writing ../../plugins/doom64tc/defs/E1M28xg.ded as defs/doom64tc/E1M28xg.ded
writing ../../plugins/doom64tc/defs/E1M01xg.ded as defs/doom64tc/E1M01xg.ded
writing ../../plugins/doom64tc/defs/E1M05xg.ded as defs/doom64tc/E1M05xg.ded
writing ../../plugins/doom64tc/defs/lights.ded as defs/doom64tc/lights.ded
writing ../../plugins/doom64tc/data/conhelp.txt as data/doom64tc/conhelp.txt
processing ../../plugins/doom64tc/data/lumps
writing ../../plugins/doom64tc/data/lumps/menufog.lmp as #.basedata/menufog.lmp
writing ../../plugins/doom64tc/data/lumps/m_therm2.lmp as #.basedata/m_therm2.lmp
writing ../../plugins/doom64tc/data/lumps/sndcurve.lmp as #.basedata/sndcurve.lmp
writing ../../plugins/doom64tc/data/lumps/pal18to8.lmp as #.basedata/pal18to8.lmp
closing /home/cory/deng-1.9.0-beta5/doomsday/build/doom64tc.pk3
[  0%] Built target Generate.pk3
Linking C executable doomsday
CMakeFiles/doomsday.dir/external/lzss/unix/src/lzss.o: In function `lzOpenChunk':
lzss.c:(.text+0x1744): warning: the use of `tmpnam' is dangerous, better use `mkstemp'
/usr/bin/../lib/libasound.so.2: undefined reference to `midiparser_input_buf'
/usr/bin/../lib/libasound.so.2: undefined reference to `midiparser_create'
collect2: ld returned 1 exit status
make[2]: *** [doomsday] Error 1
make[1]: *** [CMakeFiles/doomsday.dir/all] Error 2
make: *** [all] Error 2

```

at which point the installer stops and leaves the install incomplete.  I searched all over google, but nothing worked.  I did install all the libs needed, and also did install dependencies.  If anyone could help me out that would be great.

---

### Post by Grishka on 2008-05-16
perhaps you'd have more luck with beta5.1. you'll have to unpack it into beta5 folder before compiling, mind you.

---

### Post by disturbedite on 2008-05-16
you might see my post here for info about doomsday:
[http://ubuntuforums.org/showthread.php?p=4882554#post4882554](http://ubuntuforums.org/showthread.php?p=4882554#post4882554)

---

### Post by OpposingForce on 2008-05-16
Thanks for the replies, is there any other good doom port for linux?

---

### Post by Grishka on 2008-05-16
> **OpposingForce said:**
> Thanks for the replies, is there any other good doom port for linux?

there are many. check out this page: [http://doom.wikia.com/wiki/Source_ports#Unix.2FUnix-like](http://doom.wikia.com/wiki/Source_ports#Unix.2FUnix-like). ZDoom is quite good, also you can try PrBoom from the repos, but to each his own.

---

### Post by OpposingForce on 2008-05-16
Thanks, I actually got one called "Chocolate Doom" I had to go through hell and back to install it (no pun intended).  This was mostly because of permissions keeping me from copying game source files to where they needed to go, and having to "cd" and "sudo" everything.  It was a pain in the ***, but it works.  edit - I just installed timidity and now the musics working, so this linux port works flawlessly :D

---

### Post by disturbedite on 2008-05-17
> **OpposingForce said:**
> Thanks for the replies, is there any other good doom port for linux?
for a 3d source port, try vavoom.

for a 2d/semi 3d DEFINITELY get skulltag.  it is the best source port imo.
installing skulltag is extremely simple, but apparently "extremely simple" isn't simple enough for some ppl, so here are the instructions:
[http://ubuntuforums.org/showpost.php?p=4845224&postcount=3](http://ubuntuforums.org/showpost.php?p=4845224&postcount=3)

if you have any further questions, feel free to ask & i will try to help.

---

### Post by wingnux on 2008-05-17
[http://manualinux.my-place.us/doomsday.html](http://manualinux.my-place.us/doomsday.html)

This page helped me a lot when I tried installing doomsday on Ubuntu. The tutorial is in Spanish but it's really easy to follow.

---

