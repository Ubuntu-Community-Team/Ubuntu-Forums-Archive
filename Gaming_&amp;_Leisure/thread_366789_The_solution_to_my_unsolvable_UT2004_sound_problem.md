---
title: "The solution to my unsolvable UT2004 sound problem"
date: 2007-02-21
forum: Gaming &amp; Leisure
---

### Post by markfoged on 2007-02-21
Finally, I got my sound working in UT2004, but it took all afternoon!

I'm convinced, that I have tried EVERYTHING suggested on these forums, and related ones.
If this solution to the no sound problem is already posted somewhere, I apologize.

What I did, knowing that the UT2004 Linux Demo's sound had worked perfectly last time I was bored at the university, was to install the demo, grab the openal.so from the UTDEMOPATH/System folder, and copying it into my original game folder's System subfolder (UTGAMEPATH/System).

This solved my problems, and even though I know it's not the most pretty solution, it is none the less a solution :)

~Kim

---

### Post by shamanu on 2007-02-21
Here's what I did ( I don't know if anybody sugested it yet):
- open Synaptic and install libopenalpp-cvs1, and libopenal-cvs-dev (it is the c++ writen version of openal)
- copy and rename libopenalpp.so.1.0.0 to openal.so in the System folder inside of the installation folder of UT
- then run the game and enjoy the sound 
 (hope it works for you as it does for me)

---

### Post by nalmeth on 2007-03-20
To anyone without sound in UT2004, in edgy all I had to do was install this package, mentioned above:
```
libopenalpp-cvs1
```

---

### Post by shanek on 2007-06-26
shamanu's solution worked just fine for me too

---

### Post by suriver on 2007-07-26
All you need to do is to install the package **libopenal0a** and link /usr/lib/libopenal.so.0 to your UT2004 System directory as openal.so.

$ apt-get install libopenal0a
$ ln -s /usr/lib/libopenal.so.0 <path-to-ut2004>/System/openal.so

Linking libopenalpp seams to work, too, but it's obviously the wrong choice.

---

### Post by chronusdark on 2007-08-08
anyone know how to fix crackley sound?

---

### Post by wouterh on 2007-09-18
I also had crackley sound, fixed it by copying the openal.so lib from the UT2004 demo "System" directory to the "System" directory of the full game. (overwriting the openal.so thats already there)

Sound should now be clear and the quality much better!

---

### Post by beefcurry on 2007-10-08
Tried this in gutsy with both libopenal and libopenalpp. Both times I did not get a sound. I believe the packages should be the same in Gutsy and Edgy and I do not see where I went wrong. Can someone attach a working version of openal.so so I can try please? That would be alot of help.

---

### Post by kikos on 2007-11-29
Here is another way to get the sound working (credit to [http://icculus.org/lgfaq/#setopenaldrvr](http://icculus.org/lgfaq/#setopenaldrvr) )

You can set OpenAL to use a specific driver in the terminal.  Open an ubuntu terminal and type this at the prompt:

```
echo "(define devices '(driver))" > ~/.openalrc
```

Where driver is one of the following depending on your configuration:

```
# native (OSS)
sdl (Simple DirectMedia Layer backend, see above Q/A)
arts (arts backend)
esd (ESounD backend)
alsa (ALSA)
waveout (Output a wav file)
null (no sound)
```

For example, if your sound driver is sdl you type:

```
echo "(define devices '(sdl))" > ~/.openalrc
```

Also there is a section in your ~/.ut2004/System/UT2004.ini called ALAudio.ALAudioSubsytem.  Make sure that in this section that the line is:
```
UseDefaultDriver=False
```

If you are not sure about which driver to use, use trial and error until you figure out which one works.

---

### Post by kikos on 2007-11-29
After I patched UT2004 to the latest version (a patch from year 2005), the sound was messed up again.  Only way I was able to fix this was by checking the box for using low sound quality.  This box is found in the settings menu of ut2004.

---

