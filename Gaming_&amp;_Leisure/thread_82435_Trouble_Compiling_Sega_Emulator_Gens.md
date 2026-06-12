---
title: "Trouble Compiling Sega Emulator Gens"
date: 2005-10-26
forum: Gaming &amp; Leisure
---

### Post by kate_lar on 2005-10-26
I'm a new Ubuntu user, Breezy if running great on my HP pc with an Athlon.
I'm trying to compile the Sega Emulator "Gens" (from: [http://sourceforge.net/projects/gens/](http://sourceforge.net/projects/gens/) ) and when I type "configure" I get

 ./configure
bash: ./configure: /bin/sh^M: bad interpreter: No such file or directory

I've been able to compile other things (Zsnes, among other things) after using synaptic to get gcc, make, various development libraries, etc.
I'm not a programer, help! :confused:

---

### Post by GIBson3 on 2005-10-26
I'm not sure it would cause the issue, but that Configure file has a "windows" escape character on the end (that's the ^m)  Getting rid of that would be my first guess.  Try opening the configure file up (gedit, vi, emacs, nano, etc) and get rid of the ^M's, then try running it.

---

### Post by kate_lar on 2005-10-27
Thanks so much for your help! I went into Kate and changed the "configure" file from "End of Line - Microsoft" to "End of Line - Unix" and that got me quite a bit further.
Though now when I type "configure" it acts like it's getting somewhere but then says:

/debug/gens-debug.Po: No such file or directory

Any suggestions?

---

### Post by -DarkMind- on 2005-12-10
im bored about gens, this program never compile :(

someone have the .deb??

---

### Post by phanboy_iv on 2006-01-04
Acutally, I run the Windows version of Gens+ under wine and with some configging it runs better that the current "native" linux version. SegaCD/Sega 32x support works very well too.

---

### Post by endy on 2006-01-14
I got gens-rc3 to compile, I did have to edit the "GensForLinux/src/gens/emulator/g_main.c" file and remove the "static" on line 753 to get it to compile but it seems to have done the trick.

---

