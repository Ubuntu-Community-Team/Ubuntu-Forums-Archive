---
title: "Stepmania crashes (BG Animations?)"
date: 2006-01-30
forum: Gaming &amp; Leisure
---

### Post by dakilla on 2006-01-30
hello i have got a problem that i cant find any solution to.. so now i am asking for some help..

nearly everything works fine..
when i am starting stepmania this warning comes:

Couldn't load driver ALSA: Not enough substreams for hardware mixing, using software mixing
ALSA: Software mixing at 44100hz
Sound driver: ALSA-sw
/////////////////////////////////////////
WARNING: Unknown lights driver name:
/////////////////////////////////////////
but the sound works greate and all..
and i have animated characters that works fine..
but when i try to run a song with video as BG it crashes...
and this displayes

ptrace failed: Operation not permitted
ptrace failed: Operation not permitted
ptrace failed: Operation not permitted

and in the "/tmp/crashinfo.txt" the only error i can find is:

Thread: Main thread
        ../../src/RageSurface_Load_PNG.cpp:42
        ../../src/RageSurface_Load_PNG.cpp:42
        ../../src/RageSurface_Load_PNG.cpp:42
        ../../src/RageTextureManager.cpp:108 RageTextureManager::LoadTexture(Songs/DDR Anime 1st Mix/Chobits/ChobitsIntro.avi).        ../../src/arch/MovieTexture/MovieTexture.cpp:86 Assertion 'DriversToTry.size() != 0' failed

plz help me!

---

### Post by gomecin on 2013-02-01
I got the problem with the crashinfo.txt saying the stuff about 
 RageSurface_Load_PNG.cpp:42
started to happend when my sidebar icons turned to be big.
Tha graphics card controller was the bad guy in the story, after a system upgrade something changed with it.
MY STEPMANIA WORKED AGAIN BY ACTIVATING THE PROPIETARY DRIVER OF MY FGLRX ATI/AMD
and surprisengly the sidebar icons became small again.
I post this because after a long search nobody wrote how to solve the issue

---

