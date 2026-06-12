---
title: "SDL_net"
date: 2006-08-31
forum: Gaming &amp; Leisure
---

### Post by audioboxer217 on 2006-08-31
Does anybody know how to get SDL_net installed.  I am trying to install Warzone 2100 Ressurection and it is asking for this. I have looked around in the repositories and cannot seem to find it.  I went to [http://www.libsdl.org]("http://www.libsdl.org") but there are no deb files for SDL_net and the only binaries are the source. (is it possible to install an RPM on a Debian system?) 

Sorry for all the questions, I am still relitively new to the Linux world, although I've been working with computers for several years.

---

### Post by ZylGadis on 2006-08-31
It is certainly possible to install rpms in debian - see the manual page of alien (besides, binary is not equal to source :) ). However, I don't believe sdl_net is not in the reps. Have you tried all kinds of searches on sdl?

---

### Post by audioboxer217 on 2006-08-31
I searched for "sdl" and looked through all the results and still got nothing.

The source was the only thing that had a binary file.  I wish they had a bin file that would install the software.  That's the way I have installed several things.  I still don't completely understand building software from source.  Maybe someone could just help me with that.

I also read somewhere that using 'alien' should be a last resort as it does not always work.

---

### Post by aanderse on 2006-08-31
sudo apt-get install libsdl-net1.2 and sudo apt-get install libsdl-net1.2-dev should work

---

### Post by audioboxer217 on 2006-08-31
> **aanderse said:**
> sudo apt-get install libsdl-net1.2 and sudo apt-get install libsdl-net1.2-dev should work
Thanks, I will give that a try.  I didn't even think to look for libsdl.

<b>EDIT:</b> That worked.  Thanks for the help guys.  also the lib thing was true for another package that was missing.  I have also decided from this ordeal that I don't really like .package files.  They are as broken as RPM.

Long live Debian

---

### Post by switchrodeo720 on 2008-10-19
I was having the same "sdl_net" problem when trying to install vdrift in 8.04. Once I installed the libs everything worked perfectly.

---

