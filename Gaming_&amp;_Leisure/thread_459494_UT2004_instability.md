---
title: "UT2004 instability"
date: 2007-05-30
forum: Gaming &amp; Leisure
---

### Post by Death_Sargent on 2007-05-30
unreal tournament crashes every time i try to play a large map. 

sometimes it crashes randomly. 

Can anyone help me?

im on ubuntu 7.04 

dual 3.2 gig processors

1024mb ram

64mb ati radeon 9800 vram (using propreitary driver)

---

### Post by _simon_ on 2007-05-30
Have you got the latest patch, 3369-2?

If not, [get it here](http://www.3dgamers.com/dlselect/games/unrealtourn2k4/ut2004-lnxpatch3369-2.tar.bz2.html)

Just extract it to your UT2004 folder.

---

### Post by Death_Sargent on 2007-05-30
I have the latest patch from the official UT website.

---

### Post by Cappy on 2007-05-30
The one on the official site is the old version 3355. 3369-2 fixed my UT2004 crashes. You need it =-/

---

### Post by Death_Sargent on 2007-05-31
tried it still crashed my system

---

### Post by Cappy on 2007-05-31
Sometimes the temporary files become corrupt. The game will recreate the files when they are removed. If this doesn't fix the problem you can always move back your old files:
```

mv ~./ut2004/Cache ~./ut2004/CacheOld
mv ~./ut2004/System/User.ini ~./ut2004/System/Userold.ini
mv ~./ut2004/System/UT2004.ini ~./ut2004/System/UT2004old.ini

```

You're using 32-bit Ubuntu, right?

---

### Post by Death_Sargent on 2007-05-31
yes i am using 32 bit ubuntu only the files are in diff location i will try

---

### Post by Death_Sargent on 2007-05-31
ok its still crashing on large maps

---

### Post by Death_Sargent on 2007-05-31
anyone?

---

### Post by Cappy on 2007-05-31
That should have been:
```

mv ~/.ut2004/Cache ~/.ut2004/CacheOld
mv ~/.ut2004/System/User.ini ~/.ut2004/System/Userold.ini
mv ~/.ut2004/System/UT2004.ini ~/.ut2004/System/UT2004old.ini

```

---

### Post by Death_Sargent on 2007-06-02
yeah i got that still no luck though

---

### Post by Jimbob17 on 2007-06-10
> **Death_Sargent said:**
> yeah i got that still no luck though

Did you fix this?? I had a similar problem on my system and I finally tracked it down to the RAM settings in the BIOS. Mine were set to Turbo or something and I changed this to 'By SPD' and the crashes disappeared.

HTH

---

### Post by Death_Sargent on 2007-06-10
i don't even have those options in my bios

---

### Post by Eazy© on 2007-06-11
In your ut2004.ini try with changing VARSize=32 to VARSize=64 under [OpenGLDrv.OpenGLRenderDevice]

Dont know if it will help, but it's worth a try :)

---

### Post by Jimbob17 on 2007-06-11
> **Death_Sargent said:**
> i don't even have those options in my bios

I take it you have a desktop system? As mine was RAM related, you could try removing a stick of RAM and testing UT2004. If it doesn't crash, try swapping the installed RAM with the other stick of RAM and repeat ...

When I had the problems with UT2004, I didn't have any problems when running in Windows 2000 ... so Linux may be a bit picky on the RAM (well, that's the way I see it).

If this doesn't help then I'm not quite sure what to suggest next.

---

### Post by Death_Sargent on 2007-06-11
> **Jimbob17 said:**
> I take it you have a desktop system? As mine was RAM related, you could try removing a stick of RAM and testing UT2004. If it doesn't crash, try swapping the installed RAM with the other stick of RAM and repeat ...

When I had the problems with UT2004, I didn't have any problems when running in Windows 2000 ... so Linux may be a bit picky on the RAM (well, that's the way I see it).

If this doesn't help then I'm not quite sure what to suggest next.

no i have a laptop just can't find the jumpers to give me better bios control which i really want becuase the makers over clocked the thing

---

### Post by Death_Sargent on 2007-06-11
> **Eazy© said:**
> In your ut2004.ini try with changing VARSize=32 to VARSize=64 under [OpenGLDrv.OpenGLRenderDevice]

Dont know if it will help, but it's worth a try :)

Tried this and it did not work

but thanks for the sujjestion

---

