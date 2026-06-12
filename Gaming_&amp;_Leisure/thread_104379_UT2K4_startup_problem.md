---
title: "UT2K4 startup problem?"
date: 2005-12-16
forum: Gaming &amp; Leisure
---

### Post by handy on 2005-12-16
I've installed my nVidia drivers, no prob's, got the SBLive working, great, now at last I can install ut2k4, my favourite game :smile:

I've patched to 3355, still the startmenu item does nothing, the shell does a little more, see below:

===============================================
root@BirdFish:/usr/local/games/ut2004# ls

Animations     Maps                    Speech        UT2004_EULA.txt
Benchmark      Music                   StaticMeshes  ut2004.xpm
ForceFeedback  openal_sources.tar.bz2  System        Web
Help           README.linux            Textures
KarmaData      sdl12_sources.tar.bz2   uninstall
Manual         Sounds                  ut2004

root@BirdFish:/usr/local/games/ut2004# ut2004

./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory

root@BirdFish:/usr/local/games/ut2004#
===============================================

It looks like I'll have to edit the ".ini" file(s)?  Is that the usual routine?

Any ideas?

Thanks in advance,

handy

---

### Post by handy on 2005-12-16
The /usr/lib/LibSDL-1.2.so.0 link file is sitting right beside the  

/usr/lib/LibSDL-1.2.so.0.7.1 file it is pointing to, just waiting to be found by ut2004?

Does anyone know the name of the file that I can edit to tell ut2k4 the location of the library that it is looking for?
 
Thanks for your time,

handy

---

### Post by handy on 2005-12-16
I reinstalled the game finding that there were 2 error messages that I had missed, one hiding above the blue install screen, the other being spat out at the end.

The 1st: couldn't link to "libgtk-1.2.so.0"

The 2nd:  couldn't find "libstdc++.so.5

I could only find the 2nd one in synaptic, so I installed it.

Then tried to run the game, it ran, without sound, but that is comparitively minor.

So, I then updated with patch 3355, copied my saves across & a few skins & bonus packs, went to run it, as dead as it was before, with the same error message as started it all??

Not happy.

So, now a have to think about installing it all again WITHOUT THE 3355 Patch, which is expedient???  With 5 CD's...

handy

---

### Post by Perfect Storm on 2005-12-16
I don't have UT games, but the 2. the libgtk, did you install it:
```

sudo apt-get install libgtk1.2

```

and it still saying error?

---

### Post by handy on 2005-12-16
Hi AI,
I did not install the libgtk-1.2 file, it ran after I installed the libstdc++ one?
Untill I patched to 3355?

Cheers,

handy

---

### Post by Perfect Storm on 2005-12-16
But try install it and see what it says.

---

### Post by handy on 2005-12-16
I have tried, but there is some kind of problem with my repository, they won't update tell me that there may be a network problem?  It is a fresh install this morning, so maybe it is an Australian  repository problem, I have no idea.
I'm left with no alternative but to reinstall without the 3355 patch, & then try to get the sound to work.

It's all good fun, untill I forget that I'm having fun :-)

handy

---

### Post by Harleen on 2005-12-16
After patching ut2004 you have to install the package libstdc++5 to make it work again.

---

### Post by handy on 2005-12-16
I wish that you had of been right for me Harleen...
I installed the update, reloaded the libstdc++5 file through synaptic & lost my working unpatched version of ut2k4 :-(

Any clues anybody?

I'll check the forum later, it's way past my bedtime.

Cheers,

handy

---

### Post by Perfect Storm on 2005-12-16
[QUOTE=Harleen]After patching ut2004 you have to install the package libstdc++5 to make it work again.[/QUOTE]

An reinstall of libstdc?

---

### Post by Harleen on 2005-12-16
[QUOTE=Artificial Intelligence]An reinstall of libstdc?[/QUOTE]

No, a first  install of the old libstdc++, which insn't installed by default. Only the libstdc++6 is installed by default. Unfortunally this tip doesn't seem to have helped. At least it had worked for me... 

What are the error messages, that UT still gives now?

This missing libstdc++.so.5 should have been fixed by installing the package libstdc++5.
The libgtk-1.2.so.0 is provided by libgtk1.2.
And the libSDL-1.2.so.0 comes together with UT2004. The version Ubuntu installs isn't needed or used here.

I currently don't know, which of the fixes did not work or we might have a completly different problem. (working as root might be one...)

---

### Post by handy on 2005-12-16
Thanks for your input people :-)

I installed using sudo,
Whether I call using sudo or not I get the following error:

handy@BirdFish:/usr/local/games/ut2004$ ut2004
./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory
handy@BirdFish:/usr/local/games/ut2004$

Before I installed the patch, I was upto a 1600x1200 game running slightly choppy at times, with no sound, with bonus packs & skins installed.  This ran fine from the "Applications/UT2004" menu.

Interesting huh?

handy

---

### Post by handy on 2005-12-16
I've just reinstalled ut2k4, it works fine from the menu in very high res', I'm not really one for playing this game on line, so the patch isn't essential to me I guess.

I think I'll start another thread re: the lack of in game sound?

Being very much in the steepness of the learning curve at the moment, I have other important things to install.  
After this sound problem is fixed, then onto wine, that should be a challenge.  :-)

Thanks for your help,

handy

---

