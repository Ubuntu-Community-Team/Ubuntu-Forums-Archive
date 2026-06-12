---
title: "LxDoom doesn't work"
date: 2007-07-25
forum: Gaming &amp; Leisure
---

### Post by azraelck on 2007-07-25
Ok, I couldn't get Doomsday to work, so I went back to trying to get LXDoom to work. I copied both the Doom and Doom2 wad files into usr/share/games, as an installation guide I found said. I also copied them into the usr/share/games/doom folder as well, after I found out that this was the actual directory it should be in.  

From the launcher it does nothing. From the terminal,  it shows this:

```
LxDoom v1.4.4 (http://lxdoom.linuxgames.com/)
Z_Init : Allocated 6016Kb zone memory
IWAD not found

```

It shows this whether I use -file to point it to the doom2 wad or not. 

Both wad files were pulled from the original CDs, off a Windows rerelease. They worked before in ZDoom and Doomsday (as well as Doom95), but both of them don't work in Linux whatsoever either. Apparently, there is no working Linux port of Doom. In a few I'm going to try to get ZDoom working under Wine. If anyone can claim to have either LxDoom working, or knows an actual working port, please let me know. Doomsday does NOT run, regardless of version I try, and ZDoom does not either.

---

### Post by DoktorSeven on 2007-07-25
Try
```
lxdoom -iwad /path/to/doom.wad
```

---

### Post by azraelck on 2007-07-25
```
pike@pike-desktop:~$ lxdoom -iwad /usr/share/doom/DOOM2.wad

LxDoom v1.4.4 (http://lxdoom.linuxgames.com/)
Z_Init : Allocated 6016Kb zone memory
IWAD not found


```

Yes, I know the wad is there. I've checked twice. I somewhat wish I still had windows, which it worked fine in.

This was installed through get-apt as well, if that helps.

*edit*
I reinstalled LxDoom using synaptic. Still showed the same error.

---

### Post by DoktorSeven on 2007-07-25
Well, it worked fine here.  All I know is that Doomsday works the best for me, though it is a bit tough to compile and the 1.9.0 betas are not exactly stable.  

I've got a Doomsday (deng) 1.8.6 package built on Ubuntu [here](http://doktorseven.miskie.net/files/deng_1.8.6-1_i386.deb) but it was done with checkinstall so it won't install its dependencies; from what I remember, it needs libsdl1.2, libsdl-mixer1.2, libsdl-net1.2, and libopenal0a, possibly more.  Frontend I made up is [here](http://gdoomsday.sf.net) (also checkinstall I think, but it only requires GTK so you should be good).

I can't guarantee it'll work, of course, but if you want Doom it might be worth a try.  Note my disclaimer in my sig. ;)

---

### Post by azraelck on 2007-07-25
Yeah, thank you anyway. I guess I'm stuck seeing what will work in Whine. :P If not, then I guess I'll be waiting for a working Linux port.

---

