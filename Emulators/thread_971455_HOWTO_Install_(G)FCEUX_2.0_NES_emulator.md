---
title: "HOWTO: Install (G)FCEUX 2.0 NES emulator"
date: 2008-11-05
forum: Emulators
---

### Post by punkrockguy318 on 2008-11-05
These steps should work to install the latest version of the FCE UltraX (FCEUX) NES/Famicom emulator in Ubuntu.

1.  Install necessary dependencies. 

```

sudo apt-get install scons libsdl1.2-dev subversion libgtk2.0-dev

```

2.  Open a terminal (Applications... Accessories... Terminal) and obtain source from subversion.
```

svn checkout http://svn.code.sf.net/p/fceultra/code/fceu/trunk fceultra

```

3. Change directory into the fceultra folder.

```
cd fceultra/
```

4.  Build and install fceux.

```
sudo scons install
```

And that's it!  You can also grab an older version of fceux from the Ubuntu repositories, but the latest and greatest can be obtained and compiled from subversion.

If you would like to contribute, or run into any issues, feel free to join us in #fceu on irc.freenode.com.  You can also file bugs to our tracker ([http://sourceforge.net/p/fceultra/bugs/](http://sourceforge.net/p/fceultra/bugs/)).  Please note that you may not receive an immediate response in IRC -- idling is key.

Enjoy!

---

### Post by Calculon64 on 2008-11-08
Does this work Ubuntu 8.10 64-bit?

---

### Post by punkrockguy318 on 2008-11-09
> **Calculon64 said:**
> Does this work Ubuntu 8.10 64-bit?

yes that's what i develop and test fceux on

---

### Post by punkrockguy318 on 2008-11-10
i just changed the dependency in the tutorial to libsdl1.2debian-alsa instead of libsdl1.2debian-pulseaudio.  The esd driver seems to work better with fceux and is still compatible with pulseaudio, so I would suggest installing that if you're having trouble with sound.

---

### Post by keyshawn on 2008-11-14
thanks, worked with no problems on my end. 

I have a question though:

How can I save on this ?

I presume there is save state support since fceu had it, but I couldn't find any mention of it in the documentation 

thank you again for your work on FCEUX.

---

### Post by punkrockguy318 on 2008-11-15
> **keyshawn said:**
> thanks, worked with no problems on my end. 

I have a question though:

How can I save on this ?

I presume there is save state support since fceu had it, but I couldn't find any mention of it in the documentation 

thank you again for your work on FCEUX.

yeah the docs need to work

select state with numbers 0-9.. save with f5, load with f7

---

### Post by droazen on 2008-11-17
I installed fceux from source due to sound not working properly in the ubuntu-packaged fceu -- and it works, but after about 10 minutes the sound suddenly becomes very garbled and static-y and remains that way until the rom is closed. Any ideas about what might be causing this would be greatly appreciated! I am running hardy with pulseaudio removed, and esound and libsdl1.2debian-alsa installed.

---

### Post by punkrockguy318 on 2008-11-18
> **droazen said:**
> I installed fceux from source due to sound not working properly in the ubuntu-packaged fceu -- and it works, but after about 10 minutes the sound suddenly becomes very garbled and static-y and remains that way until the rom is closed. Any ideas about what might be causing this would be greatly appreciated! I am running hardy with pulseaudio removed, and esound and libsdl1.2debian-alsa installed.

this has actually been fixed in subversion, which will be released in version 2.0.4.  this release should get put out sometime this month i believe, but if you really want some nice working sound check out the svn repository on sourceforge

---

### Post by droazen on 2008-11-18
> **punkrockguy318 said:**
> this has actually been fixed in subversion, which will be released in version 2.0.4.  this release should get put out sometime this month i believe, but if you really want some nice working sound check out the svn repository on sourceforge

Oh AWESOME that's great news -- it's always very satisfying when a problem I'm having turns out to be a known bug that's been fixed :guitar: I'll check out the svn version tonight -- thanks!

---

### Post by billc123 on 2008-11-22
The problem i have with the one from the ubuntu repository is in full screen mode the mouse cursor remains in the center of the screen. Does anyone know if that is fixed in the newer version?

---

### Post by punkrockguy318 on 2008-11-23
> **billc123 said:**
> The problem i have with the one from the ubuntu repository is in full screen mode the mouse cursor remains in the center of the screen. Does anyone know if that is fixed in the newer version?

yes we've fixed that in 2.0

---

### Post by Chunky Dunk on 2008-11-25
When I try to compile, it fails at step 4 with:
```
sh: o: not found
Copy("bin/fceux", "src/fceux")
scons: *** [bin/fceux] src/fceux: No such file or directory
scons: building terminated because of errors.

```

---

### Post by punkrockguy318 on 2008-11-25
> **Chunky Dunk said:**
> When I try to compile, it fails at step 4 with:
```
sh: o: not found
Copy("bin/fceux", "src/fceux")
scons: *** [bin/fceux] src/fceux: No such file or directory
scons: building terminated because of errors.

```

make sure build-essential is installed

---

### Post by Chunky Dunk on 2008-11-25
> **punkrockguy318 said:**
> make sure build-essential is installed
That did the trick, Thanks. Now I feel like a bonehead for not making sure that stuff was installed! :oops:

---

### Post by billc123 on 2008-11-29
hi- I tried out the fceux 2.0.3. with gfce Ultra X 2.0.2 svn, but the mouse cursor still remains in the center of the screen when launching in full screen mode, there is some clicking noises when launching now, escape key doesn't exit the emulator now, and up and left don't seem to map with the gamepad.  

](*,)

---

### Post by billc123 on 2008-11-30
I figured out it is F1 to quit now instead of escape. But i still am having problems with up, and left on the gamepad, sound, and the mouse cursor in the new version. If anyone knows the answer please let me know- thanks...

---

### Post by Chunky Dunk on 2008-11-30
Does anyone know if the feature allowing you to speed up emulation by pressing the tilde key has been removed in this version?

---

### Post by punkrockguy318 on 2008-11-30
> **Chunky Dunk said:**
> Does anyone know if the feature allowing you to speed up emulation by pressing the tilde key has been removed in this version?

it's not removed, the hotkeys have moved..  = is to increase emu speed - is to decrease

you can't currently map these hotkeys very easily... if you relaly want to you can edit the config file by hand (~/.fceux/fceux.cfg) and insert SDL keymap codes but that's a little much for the average user :lolflag:  i'll probably get around to coding a gui for mapping the hotkeys once this semester is over ( a couple weeks )

---

### Post by punkrockguy318 on 2008-11-30
> **billc123 said:**
> hi- I tried out the fceux 2.0.3. with gfce Ultra X 2.0.2 svn, but the mouse cursor still remains in the center of the screen when launching in full screen mode, there is some clicking noises when launching now, escape key doesn't exit the emulator now, and up and left don't seem to map with the gamepad.  

](*,)

I can't reproduce your issue with the mouse in fullscreen, it's hidden for me.  This may have been fixed in the latest subversion, you might want to compile that and see if that fixes your issue.  Also, what processor arch are you running on?  I'm write and test on Ubuntu 8.10 x64.  Also, what window manager are you using ?

Sound has been cleaned up a lot in the subversion trunk, so a lot of sound issues should be fixed in 2.0.4.  I would check out and compile the latest subversion to get these fixes; it's quite a big improvement in sound quality.

The keybindings have moved.  The documentation is incomplete/inaccurate but here is the shitty SDL documentation link: [http://fceux.com/web/htdocs/fceux-sdl-docs.php](http://fceux.com/web/htdocs/fceux-sdl-docs.php)

What do you mean up and left don't map with the gamepad?  What keys are you attempting to map for up and left?  Is this on a keyboard or a joystick?  Also, make sure that you press each key TWICE when your configuring your gamepad.

I hope that helps you out a little bit.  A lot of things have been fixed lately, if you can't wait for the 2.0.4 release to enjoy the improvements, check out the svn.  And no, I have no idea when 2.0.4 will be released (when its ready lol)

---

### Post by punkrockguy318 on 2008-11-30
I just updated the sdl docs.  While they are still not complete, they are more current with the latest version of fceux.  [http://fceultra.sourceforge.net/docs.php](http://fceultra.sourceforge.net/docs.php)

check out the sdl faq and the sdl doc

enjoy!:guitar:

---

### Post by punkrockguy318 on 2008-11-30
> **billc123 said:**
> I figured out it is F1 to quit now instead of escape. But i still am having problems with up, and left on the gamepad, sound, and the mouse cursor in the new version. If anyone knows the answer please let me know- thanks...

f1 isn't quit, it's actually the cheat menu but this can only be accessed from the command line.  make sure you quit by closing the window or alt-f4 etc... if you don't launch from a terminal, f1 will cause fceux to keep running (not good)

---

### Post by billc123 on 2008-12-01
> This may have been fixed in the latest subversion, you might want to compile that and see if that fixes your issue. Also, what processor arch are you running on? I'm write and test on Ubuntu 8.10 x64. Also, what window manager are you using ?

I am running ubuntu 8.10, but not 64 bit. My cpu is Intel pentium dual core. The computer is a Dell inspiron 1525 laptop. How could I check the window manager? sorry, but I am still new to linux. 

where would I find the latest subversion? thanks- I used the source from above (first post in this thread). I don't know if the latest subversion is newer than that or no?

The gamepad is a Microsoft sidewinder USB gamepad. (i know no one likes MS, but i always liked that gamepad- lol). When I go to up for calibration it takes 3 times usually. I tried it over and over. Maybe it just doesn't like that game pad for some reason (probably because linux and MS are natural enemies- LOL). All the other functions on the gamepad work great, but not up and left. I had the same problem with the old version but finally got it to work somehow. I must have tried calibrating it at least 50 times and just got lucky once.  It is actually mapped correctly in the old one. Maybe I could just copy a config file from the old one to the new one since it works ok in the old one?

 But how can I close the window if it is full screen though? in the old version escape key worked- but other than alt enter, then click on the X,  I don't see how to close it correctly -thanks.

Bill

---

### Post by punkrockguy318 on 2008-12-05
> **billc123 said:**
> I am running ubuntu 8.10, but not 64 bit. My cpu is Intel pentium dual core. The computer is a Dell inspiron 1525 laptop. How could I check the window manager? sorry, but I am still new to linux. 

where would I find the latest subversion? thanks- I used the source from above (first post in this thread). I don't know if the latest subversion is newer than that or no?

you can oufa

the latest subversion is the latest code that you need to compile to run.  inductions are on the "Code" page of sourceforge.  if you're a new user, you might want to steer clear of using subversion code.

Your gamepad should work fine, so long as it is supposed by linux.  As long as a joystick has linux support (ls /dev/js*), 

Closing the window in fullscreen involves two sets of keys: alt-enter and alt-f4.  i don't see the big problem withhaving to leave fullscreen.


Oh, and I'd also like to update on some gfceux progress.  A working version of the input config GUI is relatively stable, it just doesn't work with joysticks right now.  Anyone using gfceux is welcome to test out the new inputcfg GUI and post feedback!

---

### Post by billc123 on 2008-12-05
I figured out what was wrong with the gamepad. It was being mapped incorrectly by GFCE UltraX 202svn. I tried mapping within the program but got the same results- up and left not working. When i opened the file .fceux/fceux.cfg both up and left were mapped to the same value of 49153.  i manually edited left and changed it to 49152 and the gamepad works correctly now.

:p

i just think its easier to be able to quit full screen with one key -escape, instead of alt enter and then alt F4 - thats all. but that just my opinion. Still trying to get the mouse cursor and sound problems working though. Thanks
ps - what is oufa?

---

### Post by punkrockguy318 on 2008-12-06
> **billc123 said:**
> I figured out what was wrong with the gamepad. It was being mapped incorrectly by GFCE UltraX 202svn. I tried mapping within the program but got the same results- up and left not working. When i opened the file .fceux/fceux.cfg both up and left were mapped to the same value of 49153.  i manually edited left and changed it to 49152 and the gamepad works correctly now.

:p

i just think its easier to be able to quit full screen with one key -escape, instead of alt enter and then alt F4 - thats all. but that just my opinion. Still trying to get the mouse cursor and sound problems working though. Thanks
ps - what is oufa?

i think your joystick issue may have been resolved in version 2.0.3, and your sound issues are probably resolved in the latest subversion.  i got rid of escape quitting because it was too easy to hit on accident

i don't know what oufa is i think i was typing something and forgot i was typing

all i can say is try 2.0.3 and wait for 2.0.4 to coem out to fix your sound issues

---

### Post by billc123 on 2008-12-07
ok cool- thanks

---

### Post by CharlieNixon on 2008-12-10
did anyone ever figure out the issue where the mouse cursor is stuck in the center of the screen during full screen mode? I am having that issue as well. Funny thing is that it worked fine when I installed it and for a few days. Later (after making NO changes) the cursor just showed up once and now it is stuck in the center of the full screen mode. 

I'm running in Intel Atom on ubuntu 8.04, btw

---

### Post by punkrockguy318 on 2008-12-12
> **CharlieNixon said:**
> did anyone ever figure out the issue where the mouse cursor is stuck in the center of the screen during full screen mode? I am having that issue as well. Funny thing is that it worked fine when I installed it and for a few days. Later (after making NO changes) the cursor just showed up once and now it is stuck in the center of the full screen mode. 

I'm running in Intel Atom on ubuntu 8.04, btw

are you running fceu .9.x or fceu 2.x?  that issue should be fixed in the latest fceux release.

---

### Post by grazzt on 2008-12-20
Edit, sigh, all sound was giving me a static, a simple reboot fixed it all, and now Im getting good sound.

---

### Post by punkrockguy318 on 2008-12-20
> **grazzt said:**
> Edit, sigh, all sound was giving me a static, a simple reboot fixed it all, and now Im getting good sound.

glad to hear that.  i'm fairly sure we got most of the sound issues out of the way in the latest svn.  it should be a fairly large improvement over 2.0.3

---

### Post by juanmoreno92 on 2008-12-26
Has anyone tried and successfully gotten it to compile on PPC? I tried but I don't know how scons works, I'm more of a makefile type of guy. Here is the output of the error:
```
src/nsf.cpp: In function 'void NSFGI(GI)':
src/nsf.cpp:128: warning: enumeration value 'GI_RESETSAVE' not handled in switch
src/nsf.cpp: In function 'void DrawNSF(uint8*)':
src/nsf.cpp:467: warning: converting to 'uint32' from 'double'
src/nsf.cpp:468: warning: converting to 'uint32' from 'double'
src/nsf.cpp:491: warning: converting to 'uint32' from 'double'
src/nsf.cpp:492: warning: converting to 'uint32' from 'double'
src/nsf.cpp:510: warning: converting to 'uint32' from 'double'
src/nsf.cpp:511: warning: converting to 'uint32' from 'double'
g++ -o src/palette.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua -I/usr/include/lua src/palette.cpp
src/palette.cpp: In function 'void SetNESDeemph(uint8, int)':
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
g++ -o src/ppu.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua -I/usr/include/lua src/ppu.cpp
src/ppu.cpp: In member function 'void PPUREGS::install_h_latches()':
src/ppu.cpp:131: warning: unused variable 'zzz'
src/ppu.cpp: In function 'void B2006(uint32, uint8)':
src/ppu.cpp:623: warning: unused variable 'zzz'
src/ppu.cpp:628: warning: unused variable 'zzz'
src/ppu.cpp: In function 'void B2007(uint32, uint8)':
src/ppu.cpp:649: warning: unused variable 'zzz'
src/ppu.cpp:652: warning: unused variable 'zzz'
g++ -o src/sound.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua -I/usr/include/lua src/sound.cpp
src/sound.cpp: In function 'void SetSoundVariables()':
src/sound.cpp:1149: warning: converting to 'uint32' from 'double'
src/sound.cpp:1155: warning: converting to 'uint32' from 'double'
g++ -o src/state.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua -I/usr/include/lua src/state.cpp
src/state.cpp: In function 'int SubWrite(std::ostream*, SFORMAT*)':
src/state.cpp:121: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:121: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
src/state.cpp:132: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:132: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
src/state.cpp: In function 'bool ReadStateChunk(std::istream*, SFORMAT*, int)':
src/state.cpp:200: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:200: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
scons: *** [src/state.o] Error 1
scons: building terminated because of errors.

```

---

### Post by punkrockguy318 on 2008-12-27
> **juanmoreno92 said:**
> Has anyone tried and successfully gotten it to compile on PPC? I tried but I don't know how scons works, I'm more of a makefile type of guy. Here is the output of the error:
```
src/nsf.cpp: In function 'void NSFGI(GI)':
src/nsf.cpp:128: warning: enumeration value 'GI_RESETSAVE' not handled in switch
src/nsf.cpp: In function 'void DrawNSF(uint8*)':
src/nsf.cpp:467: warning: converting to 'uint32' from 'double'
src/nsf.cpp:468: warning: converting to 'uint32' from 'double'
src/nsf.cpp:491: warning: converting to 'uint32' from 'double'
src/nsf.cpp:492: warning: converting to 'uint32' from 'double'
src/nsf.cpp:510: warning: converting to 'uint32' from 'double'
src/nsf.cpp:511: warning: converting to 'uint32' from 'double'
g++ -o src/palette.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua -I/usr/include/lua src/palette.cpp
src/palette.cpp: In function 'void SetNESDeemph(uint8, int)':
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:99: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:100: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
src/palette.cpp:101: warning: converting to 'uint16' from 'double'
g++ -o src/ppu.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua -I/usr/include/lua src/ppu.cpp
src/ppu.cpp: In member function 'void PPUREGS::install_h_latches()':
src/ppu.cpp:131: warning: unused variable 'zzz'
src/ppu.cpp: In function 'void B2006(uint32, uint8)':
src/ppu.cpp:623: warning: unused variable 'zzz'
src/ppu.cpp:628: warning: unused variable 'zzz'
src/ppu.cpp: In function 'void B2007(uint32, uint8)':
src/ppu.cpp:649: warning: unused variable 'zzz'
src/ppu.cpp:652: warning: unused variable 'zzz'
g++ -o src/sound.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua -I/usr/include/lua src/sound.cpp
src/sound.cpp: In function 'void SetSoundVariables()':
src/sound.cpp:1149: warning: converting to 'uint32' from 'double'
src/sound.cpp:1155: warning: converting to 'uint32' from 'double'
g++ -o src/state.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua -I/usr/include/lua src/state.cpp
src/state.cpp: In function 'int SubWrite(std::ostream*, SFORMAT*)':
src/state.cpp:121: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:121: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
src/state.cpp:132: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:132: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
src/state.cpp: In function 'bool ReadStateChunk(std::istream*, SFORMAT*, int)':
src/state.cpp:200: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:200: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
scons: *** [src/state.o] Error 1
scons: building terminated because of errors.

```

What version of fceux are you trying to compile?

What version of gcc are you using ? (output of gcc -v)



And no, I'm not aware of any recent successful compilations on the PPC architecture so I'm not sure if it will even compile (everyone coding is runnign on x86 or x64)

---

### Post by juanmoreno92 on 2008-12-27
> **punkrockguy318 said:**
> What version of fceux are you trying to compile?

What version of gcc are you using ? (output of gcc -v)



And no, I'm not aware of any recent successful compilations on the PPC architecture so I'm not sure if it will even compile (everyone coding is runnign on x86 or x64)

I am compiling the 2.0.3 version. In the changelog it states that it had issues with compiling on PPC and they have been fixed. The version of GCC I am using is 4.1.2.

---

### Post by punkrockguy318 on 2008-12-28
> **juanmoreno92 said:**
> I am compiling the 2.0.3 version. In the changelog it states that it had issues with compiling on PPC and they have been fixed. The version of GCC I am using is 4.1.2.

I have no PPC machines to test, so all I can really suggest is try compiling the latest subversion and filing a bug report if it doesn't compile

---

### Post by juanmoreno92 on 2008-12-30
Ok I was able to get fceux to compile successfully using the subversion. It showed a ton of warnings but it still compiled. I was able to confirm that it worked by launching Super Mario Brothers from the commandline. Now the problem now is that the graphical frontend won't come up. I type gfceux in the terminal and this is what I get:
```
[Juan@CELL ~]$ gfceux
Traceback (most recent call last):
  File "/usr/local/bin/gfceux", line 32, in ?
    from config_parse import FceuxConfigParser
ImportError: No module named config_parse
[Juan@CELL ~]$ Super Mario Brothers.zip

```
NOTE: I am doing the compiling on my PS3 since it's main core is based on the PPC architecture lol. It still acts as a full PPC computer though.

---

### Post by punkrockguy318 on 2008-12-30
> **juanmoreno92 said:**
> Ok I was able to get fceux to compile successfully using the subversion. It showed a ton of warnings but it still compiled. I was able to confirm that it worked by launching Super Mario Brothers from the commandline. Now the problem now is that the graphical frontend won't come up. I type gfceux in the terminal and this is what I get:
```
[Juan@CELL ~]$ gfceux
Traceback (most recent call last):
  File "/usr/local/bin/gfceux", line 32, in ?
    from config_parse import FceuxConfigParser
ImportError: No module named config_parse
[Juan@CELL ~]$ Super Mario Brothers.zip

```
NOTE: I am doing the compiling on my PS3 since it's main core is based on the PPC architecture lol. It still acts as a full PPC computer though.

yeah there are some issues with the setup.py install script right now.  try running directly out of the archive with just ./gfceux in the gfceux directory

i need to fix that, thanks for bringing that to my attention

---

### Post by juanmoreno92 on 2008-12-30
No prob. Thank you for the great emulator.

---

### Post by cyclone5uk on 2009-01-11
I followed the instructions on the first page but just get this error when i try and run gfceux:

gfceux error code 4: Could not find the fceux binary.
 Ensure that fceux is installed and in the $PATH.

---

### Post by C|Y|R|U|S on 2009-01-15
You forgot to install built-essential

type
```
 sudo apt-get install build-essential
```

and then do the steps on page 1 again.


But how can I activate **hq3x**?
adding -special 3 won't do the trick

---

### Post by punkrockguy318 on 2009-01-16
> **C|Y|R|U|S said:**
> You forgot to install built-essential

type
```
 sudo apt-get install build-essential
```

and then do the steps on page 1 again.


But how can I activate **hq3x**?
adding -special 3 won't do the trick

all of the fceux options take two dashes so try --special 3

a little change from fceu but its more consistant

---

### Post by AdventWolf on 2009-01-24
Hello, I am trying to install this on my Ubuntu mini laptop however when I am trying to launch FCEUX NES EMULATOR, I receive this error:


gfceux error code 4: Could not find the fceux binary.
Ensure that fceux is installed and in the $PATH. 


I have the latest build-essential installed already.

---

### Post by Grishka on 2009-01-24
> **AdventWolf said:**
> Hello, I am trying to install this on my Ubuntu mini laptop however when I am trying to launch FCEUX NES EMULATOR, I receive this error:


gfceux error code 4: Could not find the fceux binary.
Ensure that fceux is installed and in the $PATH. 


I have the latest build-essential installed already.

try sudo scons install, if you compiled from source. if not, you'll have to say where you got it from.

---

### Post by AdventWolf on 2009-01-24
I did a sudo scons install earlier and installed everything. I did it again and I got this:

scons: *** No SConstruct file found
File "/usr/lib/scons/SCons/Script/Main.py", line 825, in _main
$

Does that mean anything?

---

### Post by Grishka on 2009-01-24
> **AdventWolf said:**
> I did a sudo scons install earlier and installed everything. I did it again and I got this:

scons: *** No SConstruct file found
File "/usr/lib/scons/SCons/Script/Main.py", line 825, in _main
$

Does that mean anything?

you trying to install fceux or the frontend, gfceux? gfceux needs fceux installed first. I've installed gfceux with "sudo python setup.py install", and it runs fine.

---

### Post by AdventWolf on 2009-01-24
I am trying to install whatever NES Emu that will allow me to configure it. I already did the setup.py install for gfceux.

The FCEU Ultra or whatever it was that you could download from the add/remove tool allowed me to play NES games, but I couldn't figure out how to configure the settings to use a joypad.

---

### Post by punkrockguy318 on 2009-01-24
> **AdventWolf said:**
> I am trying to install whatever NES Emu that will allow me to configure it. I already did the setup.py install for gfceux.

The FCEU Ultra or whatever it was that you could download from the add/remove tool allowed me to play NES games, but I couldn't figure out how to configure the settings to use a joypad.

fceu is NOT compatible with gfceux.

if you want to use fceu (in the repos) use gfceu

if you want to use the new and improved fceux use gfceux (not in repos)

---

### Post by AdventWolf on 2009-01-24
Well since I can't get gfceux to work, I guess I'll try to get gfceu to work.

When I try to run gfceu-0.6.1 I get:

Could not find the ALSA OSS wrapper. GFCEU will not be able to share sound with other applications. On Debian based systems like Ubuntu, try the following command:
sudo apt-get install alsa-oss

I try that then I get:

Package alsa-oss is not available, but it is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package alsa-oss has no installation candidate.

---

### Post by Grishka on 2009-01-24
> **AdventWolf said:**
> Well since I can't get gfceux to work, I guess I'll try to get gfceu to work.

When I try to run gfceu-0.6.1 I get:

Could not find the ALSA OSS wrapper. GFCEU will not be able to share sound with other applications. On Debian based systems like Ubuntu, try the following command:
sudo apt-get install alsa-oss

I try that then I get:

Package alsa-oss is not available, but it is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package alsa-oss has no installation candidate.

gfceux runs fine, but you need to compile fceux from here: [http://fceux.com/web/htdocs/download.php](http://fceux.com/web/htdocs/download.php). remove fceu first. or you can try mednafen from the repos, it emulates several other systems as well.

---

### Post by AdventWolf on 2009-01-24
I've downloaded that link at least 5 times in the past 2 days. Do I need both the fceu and gfceux to play a nes rom?

I just want to start over. Ok everything nes emulator is off my computer, what do I need to download and install to play NES games and configure the menu?

Is there a way for me to uninstall all the files? they don't like to be deleted.

---

### Post by Grishka on 2009-01-24
> **AdventWolf said:**
> I've downloaded that link at least 5 times in the past 2 days. Do I need both the fceu and gfceux to play a nes rom?

you need both fceux and gfceux to have an emulator with a GUI. first install fceux with "scons" and "sudo scons install". then gfceux with "sudo python setup.py install".

---

### Post by AdventWolf on 2009-01-24
Ok, so I need to download the fceux-2.0.3 archive file with both the "fceu" and "gfceux" folders right? Then extract them to the same directory? Or do I need to merge them?

When I enter scons it says:

scons: Reading SConscript file...
platform: posix
Checking for C Library SDL... no
Did not find libSDL or SDL.lib, exiting!

What do I need to enter to install that?

---

### Post by Grishka on 2009-01-24
> **AdventWolf said:**
> Ok, so I need to download the fceux-2.0.3 archive file with both the "fceu" and "gfceux" folders right? Then extract them to the same directory? Or do I need to merge them?

When I enter scons it says:

scons: Reading SConscript file...
platform: posix
Checking for C Library SDL... no
Did not find libSDL or SDL.lib, exiting!

What do I need to enter to install that?

fceux-2.0.3.src.tar.gz is the one. don't merge the folders. run "scons" and "sudo scons install" from fceu directory, and "sudo python setup.py install" for fceux. to easily search for applications and missing libraries use Synaptic. for sdl libraries you need this: [apt://libsdl1.2-dev]("apt://libsdl1.2-dev"). you'll probably need a few more, like this one: [apt://libsdl-gfx1.2-dev]("apt://libsdl-gfx1.2-dev"). use Synaptic to find others.

---

### Post by AdventWolf on 2009-01-24
Sweet! I spent about 15 mins looking and downloading stuff I thought I needed in synaptic several hours ago but I still didn't have the right ones.

I was at the exact same spot yesterday I just didn't have the libraries. Thank you! It works perfectly.

---

### Post by punkrockguy318 on 2009-01-25
> **AdventWolf said:**
> I've downloaded that link at least 5 times in the past 2 days. Do I need both the fceu and gfceux to play a nes rom?

I just want to start over. Ok everything nes emulator is off my computer, what do I need to download and install to play NES games and configure the menu?

Is there a way for me to uninstall all the files? they don't like to be deleted.
dude just read the HOWTO it explains everything.  follow the instructions carefully and if you encounter an error report it

i know its a pain to install right now, and that's because there is no deb package for fceux and gfceux yet

---

### Post by AdventWolf on 2009-01-25
I read a few tutorials, but the problem was that I didn't have the libraries and it wasn't until late that someone helped me out by giving me the link.

---

### Post by juanmoreno92 on 2009-01-25
I have a fedora 10 src rpm of fceux. Maybe someone could use alien to turn it into a deb package?

---

### Post by khelben1979 on 2009-02-06
I'm unable to compile up fceu 2.0.3 from the source which have been provided. Need help. System: Debian Lenny on my powerbook (see my signature).

Here's the output:
```
g++ -o src/sound.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL 
-DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/l
ocal/include/lua5.1 -I/usr/include/lua5.1 src/sound.cpp
g++ -o src/state.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL 
-DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/l
ocal/include/lua5.1 -I/usr/include/lua5.1 src/state.cpp
src/state.cpp: In function 'int SubWrite(std::ostream*, SFORMAT*)':
src/state.cpp:121: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:121: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
src/state.cpp:132: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:132: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
src/state.cpp: In function 'bool ReadStateChunk(std::istream*, SFORMAT*, int)':
src/state.cpp:200: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:200: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
scons: *** [src/state.o] Error 1
scons: building terminated because of errors.
```

---

### Post by MistoffelesCat on 2009-02-22
along the same lines . . . I've successfully compiled and installed fceux and gfceux, the graphics work, the sound is fine (8.10 on a Dell Mini 9, sound fix applied).  However, the key mapping is proving problematic.  I can run the gfceux input utility, and it seems to accept the keystrokes.  However, when attempting to run a ROM, no input is accepted.

I've tried using only alpha keys, and also using the control keys.  Is there a known issue about the mini keyboard?  Or am I missing something?

Finally, I'm not sure which file would need to be edited to manually correct this issue, but if someone can point me in the right direction, I'm happy to try.

Thx!

---

### Post by cyclone5uk on 2009-03-02
I followed the instructions and it works fine, but I can't get the display to fill my widescreen monitor when I go into fullscreen mode. It stays stuck in 4:3 instead of going into 16:9

---

### Post by daring derelict on 2009-03-05
hello, I read all of the posts sofar, I tried to upgrade from fceux 2.02 to 2.03, upon running the script for gfceux i get 
> n:~/Documents/download/games/nintendo/fceux-2.03/fceultra/gfceux$ sudo python setup.py install --prefix=/usr/local
running install
running build
running build_py
package init file 'src/__init__.py' not found (or not a regular file)
package init file 'src/__init__.py' not found (or not a regular file)
running build_scripts
error: file 'gfceux' does not exist


---

### Post by punkrockguy318 on 2009-03-17
> **daring derelict said:**
> hello, I read all of the posts sofar, I tried to upgrade from fceux 2.02 to 2.03, upon running the script for gfceux i get

oops that was my bad

i moved around some of the files and forgot to commit them to subversion

its fixed in the latest subversion, so run svn update and try try agian

---

### Post by slightlystoopid on 2009-03-18
> **MistoffelesCat said:**
> along the same lines . . . I've successfully compiled and installed fceux and gfceux, the graphics work, the sound is fine (8.10 on a Dell Mini 9, sound fix applied).  However, the key mapping is proving problematic.  I can run the gfceux input utility, and it seems to accept the keystrokes.  However, when attempting to run a ROM, no input is accepted.

I've tried using only alpha keys, and also using the control keys.  Is there a known issue about the mini keyboard?  Or am I missing something?

Finally, I'm not sure which file would need to be edited to manually correct this issue, but if someone can point me in the right direction, I'm happy to try.

Thx!

I'm in the same situation, different hardware. All libraries were installed for compilation. Sound and graphics work. But fceux does not detect keystrokes within the rom. running 'fceux --inputcfg gamepad1 romname' gives me the prompt and it modifies the file ~/.fceux/fceux.cfg accurately but it has no effect within the game. it's as though fceux.cfg is not being read.

---

### Post by punkrockguy318 on 2009-03-18
> **slightlystoopid said:**
> I'm in the same situation, different hardware. All libraries were installed for compilation. Sound and graphics work. But fceux does not detect keystrokes within the rom. running 'fceux --inputcfg gamepad1 romname' gives me the prompt and it modifies the file ~/.fceux/fceux.cfg accurately but it has no effect within the game. it's as though fceux.cfg is not being read.

it's not just you and this is being looked into

can reproduce here (sometimes).

---

### Post by punkrockguy318 on 2009-03-20
Okay, for some reason input seems to work fine on Ubuntu 8.10, but its broken on jaunty (9.04).  Is the case for others?

---

### Post by CTolley on 2009-03-22
Seems that my setup has gone bad.  FCEUX was working like a champ, but I just tried to play some more and now I get this when loading a game:

> 
Starting FCEUX 2.0.3...
Loading /home/chris/Desktop/NES/1942.zip...

 PRG ROM:    2 x 16KiB
 CHR ROM:    1 x  8KiB
 ROM CRC32:  0x171251e3
 ROM MD5:  0x0b66fdf88964235c434daff62837af60
 Mapper:  0
 Mirroring: Horizontal

FCEUD_VideoChanged
Initializing video... Video Mode: 512 x 448 x 32 bpp 
ALSA lib pcm_pulse.c:625:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

E: stream.c: Assertion 's' failed at pulse/stream.c:971, function pa_stream_drain(). Aborting.
Aborted

With the GUI open, I load a game, click "execute", black screen comes up briefly, then disappears back to the GUI.

I have been trying to get a DVD Ripper to work, and that may have changed something that didn't need changed.  Any thoughts?  (I'm still retarded with Ubuntu, so please keep responses simple for my sanity)  Thanks.

*edit:  Problem fixed with reboot.  Leaving script here in case another newb has same issue.

---

### Post by slightlystoopid on 2009-03-23
> **punkrockguy318 said:**
> Okay, for some reason input seems to work fine on Ubuntu 8.10, but its broken on jaunty (9.04).  Is the case for others?

negative. I'm still using intrepid 64. also, I just tried with a new usb super nintendo controller, works like a charm. also, I don't remember if it's been said, but it only seems to affect keyboard input, which for me is a standard us keyboard (specifically a chicony internet keyboard).

---

### Post by slightlystoopid on 2009-03-23
ok, this seems strange. in full screen mode, I can only see the very bottom 1/8 or so of the image way up at the top of the screen. is there a way to pull it down?

---

### Post by MistoffelesCat on 2009-03-24
> **punkrockguy318 said:**
> Okay, for some reason input seems to work fine on Ubuntu 8.10, but its broken on jaunty (9.04).  Is the case for others?

no sir, 8,10 here.

---

### Post by khelben1979 on 2009-03-29
> **juanmoreno92 said:**
> Ok I was able to get fceux to compile successfully using the subversion. It showed a ton of warnings but it still compiled. I was able to confirm that it worked by launching Super Mario Brothers from the commandline. Now the problem now is that the graphical frontend won't come up. I type gfceux in the terminal and this is what I get:
```
[Juan@CELL ~]$ gfceux
Traceback (most recent call last):
  File "/usr/local/bin/gfceux", line 32, in ?
    from config_parse import FceuxConfigParser
ImportError: No module named config_parse
[Juan@CELL ~]$ Super Mario Brothers.zip

```
NOTE: I am doing the compiling on my PS3 since it's main core is based on the PPC architecture lol. It still acts as a full PPC computer though.

I definitely need help in compiling up this fceu emulator. I tried this before but I was unsucessful and since then I have given up. This was a few months ago.

You have written something about that you have decided to use the subversion of GFCEUX. Where can find this??

(At the present I have the old version 0.98.12 working but with no GUI and I don't know how to use frameskip without the python GUI which I'm used to, maybe I can get some help with this too?)

---

### Post by juanmoreno92 on 2009-03-29
> **khelben1979 said:**
> I definitely need help in compiling up this fceu emulator. I tried this before but I was unsucessful and since then I have given up. This was a few months ago.

You have written something about that you have decided to use the subversion of GFCEUX. Where can find this??

(At the present I have the old version 0.98.12 working but with no GUI and I don't know how to use frameskip without the python GUI which I'm used to, maybe I can get some help with this too?)

All I did was go to sourceforge where [fceux](http://sourceforge.net/projects/fceultra/) is hosted and go to SVN Browse under Code. I then clicked Download GNU tarball at the bottom and the source was downloaded. I untar'ed everything, cd'ed into fceu first, built that with scons, and then went to install gfceux using the setup.py script. Pretty easy.

Basically after downloading the source followed the instructions in the stable release to build it.

---

### Post by khelben1979 on 2009-03-29
Sounds interesting. Okay, then I will try this at a later time to see if I can manage to compile up the source from there.

---

### Post by JamonTerrell on 2009-03-31
> **punkrockguy318 said:**
> Okay, for some reason input seems to work fine on Ubuntu 8.10, but its broken on jaunty (9.04).  Is the case for others?

I'm running Ubuntu 9.04 Netbook remix and I'm having the exact same problem.  Input is detected with -input-cfg, but input doesn't work in game... any ideas?

---

### Post by khelben1979 on 2009-04-01
> **AdventWolf said:**
> I did a sudo scons install earlier and installed everything. I did it again and I got this:

scons: *** No SConstruct file found
File "/usr/lib/scons/SCons/Script/Main.py", line 825, in _main
$

Does that mean anything?

I'm trying to compile this emulator now and I receive almost the same thing as this guy. It complains about line 817 in my case.

Mmm... :confused: What exactly is I supposed to do in order to compile the fceu emulator? It seems that I have managed to compile the gui, but for fceu, I don't know. :-(

The older version of fceu have been removed from the system.

---

### Post by JamonTerrell on 2009-04-14
I stopped in to chat with the FCEUX guys in their IRC channel last night to talk about this issue and see if that had any insight.  After some discussion they were able to figure out the underlying problem is that dependency on LUA wasn't being resolved.  The deb files they release list it as a dependency, but for whatever reason, either it's not being installed, or there's some more that needs to be added as dependencies.  I'm going to spinup a new 9.04 VM tonight to figure out exactly what it is.

The quick fix if you just want it to work:
sudo apt-get install liblua5.1*

Mad props to the guys in #fceu on irc.freenode.com, they're amazingly friendly and helpful.

---

### Post by punkrockguy318 on 2009-04-14
> **JamonTerrell said:**
> I stopped in to chat with the FCEUX guys in their IRC channel last night to talk about this issue and see if that had any insight.  After some discussion they were able to figure out the underlying problem is that dependency on LUA wasn't being resolved.  The deb files they release list it as a dependency, but for whatever reason, either it's not being installed, or there's some more that needs to be added as dependencies.  I'm going to spinup a new 9.04 VM tonight to figure out exactly what it is.

The quick fix if you just want it to work:
sudo apt-get install liblua5.1*

Mad props to the guys in #fceu on irc.freenode.com, they're amazingly friendly and helpful.
Wow, thank you so much.  I went ahead and fixed the build scripts.  The problem was that liblua now NEEDs to be installed for input to work (i had no idea).  The next release of fceux will reflect this change, but until then just be sure that liblua5.1-dev is installed .  With the latest source in subversion, i changed the build scripts to exit if lua is not found.

Wow, this bug existed for FAR too long.

---

### Post by khelben1979 on 2009-04-14
> **JamonTerrell said:**
> I stopped in to chat with the FCEUX guys in their IRC channel last night to talk about this issue and see if that had any insight.  After some discussion they were able to figure out the underlying problem is that dependency on LUA wasn't being resolved.  The deb files they release list it as a dependency, but for whatever reason, either it's not being installed, or there's some more that needs to be added as dependencies.  I'm going to spinup a new 9.04 VM tonight to figure out exactly what it is.

The quick fix if you just want it to work:
sudo apt-get install liblua5.1*

Mad props to the guys in #fceu on irc.freenode.com, they're amazingly friendly and helpful.

This looks promising! Maybe I will finally be able to compile the source soon. I'll see what happens.

---

### Post by punkrockguy318 on 2009-04-15
The input issue has been resolved (even more).  Liblua is again OPTIONAL.  

For a while, there was a bug in which if lua support was not compiled into fceux, input would not work properly.  However, that bug has been fixed and lua is again optional (in the latest subversion).  We're trying to push out an SDL release soon that will incorporate this fix.

I also updated the HOWTO to include that there are now deb packages of fceux.  Installing the deb package is much easier than compiling from source, so that installation method is recommended.

If you guys have any questions or anything, stop in #fceu on irc.freenode.net

Rock on guys :guitar:

---

### Post by ghostandmachine on 2009-04-15
i'm getting this error running it from the terminal (v2.1.0a ubuntu 8.04)

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
No available audio device

---

### Post by khelben1979 on 2009-04-15
On this ppc linux system, it still won't compile without errors. Hmm... My guess would be that I'm missing more packages in my system which is required, but I don't know what at this time.

---

### Post by punkrockguy318 on 2009-04-15
> **khelben1979 said:**
> On this ppc linux system, it still won't compile without errors. Hmm... My guess would be that I'm missing more packages in my system which is required, but I don't know what at this time.

could you post your errors?

---

### Post by khelben1979 on 2009-04-16
81-224-174-203-o1123:/home/bear/FCEU/fceu# scons
scons: Reading SConscript files ...
platform:  posix
Checking for C library SDL... (cached) yes
Checking for C library z... (cached) yes
Checking for C library lua5.1... (cached) yes
Checking for C library lua... (cached) no
Checking for zenity... yes
Checking for C function asprintf()... (cached) yes
Checking for C++ library GL... (cached) yes
base CPPDEFINES: ['PSS_STYLE=1', ['_GNU_SOURCE', '1'], '_REENTRANT', '_S9XLUA_H', 'FRAMESKIP']
base CCFLAGS: -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL
$__RPATH
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/state.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/state.cpp
src/state.cpp: In function 'int SubWrite(std::ostream*, SFORMAT*)':
src/state.cpp:121: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:121: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
src/state.cpp:132: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:132: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
src/state.cpp: In function 'bool ReadStateChunk(std::istream*, SFORMAT*, int)':
src/state.cpp:200: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:200: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
scons: *** [src/state.o] Error 1
scons: building terminated because of errors.

---

### Post by Sharule on 2009-04-17
I am trying to load some of the LUA scripts for SMB, but I keep coming up with this error:
```
Lua thread bombed out: /home/dauven/fceu/output/luaScripts/SMB-Mouse.lua:19: module 'x_functions' not found:
	no field package.preload['x_functions']
	no file './x_functions.lua'
	no file '/usr/local/share/lua/5.1/x_functions.lua'
	no file '/usr/local/share/lua/5.1/x_functions/init.lua'
	no file '/usr/local/lib/lua/5.1/x_functions.lua'
	no file '/usr/local/lib/lua/5.1/x_functions/init.lua'
	no file '/usr/share/lua/5.1/x_functions.lua'
	no file '/usr/share/lua/5.1/x_functions/init.lua'
	no file './x_functions.so'
	no file '/usr/local/lib/lua/5.1/x_functions.so'
	no file '/usr/lib/lua/5.1/x_functions.so'
	no file '/usr/local/lib/lua/5.1/loadall.so'

```

---

### Post by juanmoreno92 on 2009-04-18
> **khelben1979 said:**
> 81-224-174-203-o1123:/home/bear/FCEU/fceu# scons
scons: Reading SConscript files ...
platform:  posix
Checking for C library SDL... (cached) yes
Checking for C library z... (cached) yes
Checking for C library lua5.1... (cached) yes
Checking for C library lua... (cached) no
Checking for zenity... yes
Checking for C function asprintf()... (cached) yes
Checking for C++ library GL... (cached) yes
base CPPDEFINES: ['PSS_STYLE=1', ['_GNU_SOURCE', '1'], '_REENTRANT', '_S9XLUA_H', 'FRAMESKIP']
base CCFLAGS: -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL
$__RPATH
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/state.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/state.cpp
src/state.cpp: In function 'int SubWrite(std::ostream*, SFORMAT*)':
src/state.cpp:121: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:121: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
src/state.cpp:132: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:132: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
src/state.cpp: In function 'bool ReadStateChunk(std::istream*, SFORMAT*, int)':
src/state.cpp:200: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:200: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
scons: *** [src/state.o] Error 1
scons: building terminated because of errors.

Try compiling the svn version. Worked for me and my PS3.

---

### Post by guyster on 2009-04-18
I have successfully compiled and installed fceux with gfceux on my desktop running ubuntu intrepid.  I have the enable full-screen option checked in gfceux, as well as the auto-scale and open-gl boxes.  The problem, I receive an error in every game that says unable to display video mode.  It then tells me that optimal resolution is 1280x1024.  My question is, what is the best way to achieve this?  I don't see anywhere in the video tab to select resolution directly.  As always, any help would be greatly appreciated and kudos to the devs for an awesome emulator.

Thanks,


Guy

---

### Post by khelben1979 on 2009-04-18
> **juanmoreno92 said:**
> Try compiling the svn version. Worked for me and my PS3.

Can you give me a link from where you got it from? (I checked the homepage, but felt uncertain on where I should get it anyway, hmm..)

---

### Post by guyster on 2009-04-18
I have a question concerning compiling and installing gfceux on my laptop running Ubuntu Jaunty.  When I try and launch gfceux from the command line, I get an error that says "no module named gfceux.  I looked at the output of the build command, and there are no errors.  Any suggestions as to how to get gfceux working on my laptop?  Thanks in advance for any info.

Thanks,


Guy

---

### Post by juanmoreno92 on 2009-04-18
> **khelben1979 said:**
> Can you give me a link from where you got it from? (I checked the homepage, but felt uncertain on where I should get it anyway, hmm..)

Check out:
```
svn co https://fceultra.svn.sourceforge.net/svnroot/fceultra fceultra
```
Compile fceu first:
```
cd fceultra/fceu
scons
(if all goes well)
sudo scons install
```
And then install gfceux front end:
```
cd ../gfceux
sudo python setup.py install prefix=/usr (or where ever else you want it)
```

---

### Post by khelben1979 on 2009-04-19
Okay, the program svn does not exist in Debian. where can I download it (I googled around a bit, but couldn't find anything useful on the subject).

---

### Post by DrMelon on 2009-04-19
> **Sharule said:**
> I am trying to load some of the LUA scripts for SMB, but I keep coming up with this error:
```
Lua thread bombed out: /home/dauven/fceu/output/luaScripts/SMB-Mouse.lua:19: module 'x_functions' not found:
	no field package.preload['x_functions']
	no file './x_functions.lua'
	no file '/usr/local/share/lua/5.1/x_functions.lua'
	no file '/usr/local/share/lua/5.1/x_functions/init.lua'
	no file '/usr/local/lib/lua/5.1/x_functions.lua'
	no file '/usr/local/lib/lua/5.1/x_functions/init.lua'
	no file '/usr/share/lua/5.1/x_functions.lua'
	no file '/usr/share/lua/5.1/x_functions/init.lua'
	no file './x_functions.so'
	no file '/usr/local/lib/lua/5.1/x_functions.so'
	no file '/usr/lib/lua/5.1/x_functions.so'
	no file '/usr/local/lib/lua/5.1/loadall.so'

```

I get this error too. By the look of things, it's missing the "x_functions" lua module...

---

### Post by guyster on 2009-04-19
> **khelben1979 said:**
> Okay, the program svn does not exist in Debian. where can I download it (I googled around a bit, but couldn't find anything useful on the subject).

The svn command is obtained by doing a sudo apt-get install subversion from the terminal.  Let me know if you need any other help with this.

---

### Post by khelben1979 on 2009-04-19
Now I **finally** have the new version of FCEUX compiled succesfully. :)

The gui does not work at this time. This is the output:

```
Using: /usr/local/bin/fceux
ERROR.
Traceback (most recent call last):
  File "./gfceux", line 11, in <module>
    app = main.GfceuxApp()
  File "/usr/lib/python2.5/site-packages/gfceux/main.py", line 222, in __init__
    self.load_ui()
  File "/usr/lib/python2.5/site-packages/gfceux/main.py", line 290, in load_ui
    print 'Could not find the ' + glade_file + ' file.'
UnboundLocalError: local variable 'glade_file' referenced before assignment
81-224-174-203-o1123:/fceultra/gfceux#
```
:-k

---

### Post by khelben1979 on 2009-04-19
I managed to get the emulator running this time, as I wrote (without GUI), but after this it doesn't work anymore, despite that I reboot the system.

This is how it looks like at the present:

```
bear@81-224-174-203-o1123:~/emulering/NES_ROMS$ fceux --frameskip 2 --bpp 24 ZELDA.NES

Starting FCEUX 2.1.1-interim...
Loading ZELDA.NES...

100bf30c PRG ROM:    8 x 16KiB
 CHR ROM:    0 x  8KiB
 ROM CRC32:  0x3fe272fb
 ROM MD5:  0xd9a1631d5c32d35594b9484862a26cba
 Mapper:  1
 Mirroring: Horizontal
 Battery-backed.

FCEUD_VideoChanged
Initializing video... Video Mode: 256 x 224 x 24 bpp 
fceux: symbol lookup error: /usr/lib/libSDL-1.2.so.0: undefined symbol: SDL_Quit
```

---

### Post by juanmoreno92 on 2009-04-19
> **khelben1979 said:**
> I managed to get the emulator running this time, as I wrote (without GUI), but after this it doesn't work anymore, despite that I reboot the system.

This is how it looks like at the present:

```
bear@81-224-174-203-o1123:~/emulering/NES_ROMS$ fceux --frameskip 2 --bpp 24 ZELDA.NES

Starting FCEUX 2.1.1-interim...
Loading ZELDA.NES...

100bf30c PRG ROM:    8 x 16KiB
 CHR ROM:    0 x  8KiB
 ROM CRC32:  0x3fe272fb
 ROM MD5:  0xd9a1631d5c32d35594b9484862a26cba
 Mapper:  1
 Mirroring: Horizontal
 Battery-backed.

FCEUD_VideoChanged
Initializing video... Video Mode: 256 x 224 x 24 bpp 
fceux: symbol lookup error: /usr/lib/libSDL-1.2.so.0: undefined symbol: SDL_Quit
```
I have no clue on this one. I managed to run the rip off version of Super Mario Brothers (the one that leads you underwater to peach that runs away) many times without error.

---

### Post by billc123 on 2009-04-29
Squashed looking graphics- how to fix

This is just some general info in case someone else has the same problem I had.  When I went into full screen mode it looked like the graphics were squashed (specifically in super mario bros 3)- it was fixed by setting the following command under the advanced tab, extra parameters  

 --xres 640 --yres 480

took me a little while to figure out what was wrong so I just figured i would post that.

i just upgraded to GFCEUX v2.1 and it fixed the vast majority of my issues. Thanks to the coders ! :P

also - just curious- is it possible to make the cursor not visible in full screeen mode?

---

### Post by nortexoid on 2009-04-30
I just installed in Jaunty using the .deb, and while fceux works, the graphical interface gfeux doesn't. This is the error I get:

```
Traceback (most recent call last):
  File "/usr/bin/gfceux", line 9, in <module>
    from gfceux import main
ImportError: No module named gfceux
```

Any ideas?

---

### Post by Grishka on 2009-04-30
> **nortexoid said:**
> I just installed in Jaunty using the .deb, and while fceux works, the graphical interface gfeux doesn't. This is the error I get:

```
Traceback (most recent call last):
  File "/usr/bin/gfceux", line 9, in <module>
    from gfceux import main
ImportError: No module named gfceux
```

Any ideas?

installing from svn should work.

---

### Post by nortexoid on 2009-04-30
Thanks.

On another note. Why is the performance so slow on my 1.06ghz Intel Core Solo ULV with 945GM graphics, when roms run blazing in Windows emulators on the same hardware (e.g. in Jnes) and with less cpu utilization!?

---

### Post by nortexoid on 2009-04-30
> **nortexoid said:**
> Thanks.

On another note. Why is the performance so slow on my 1.06ghz Intel Core Solo ULV with 945GM graphics, when roms run blazing in Windows emulators on the same hardware (e.g. in Jnes) and with less cpu utilization!?

Nevermind. It runs quite well, performance-wise. I noticed after watching a Flash video just now that it was super choppy. For some reason (I guess after resuming from suspend) that write-combining for my video was disabled, as revealed by a cat /proc/mtrr. Stupid linux!

---

### Post by Clydtsdk-Rivendare on 2009-05-01
I know this post was inevitable, but how legal is this? Need something to do while I get WOW fixed.

---

### Post by Nazty_Nayt on 2009-05-04
Hey when is get to

```
sudo scons install
```

I get nothing but errors, such as

```
5.1 src/input/shadow.cpp
sh: o: not found
o src/input/suborkb.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/input/suborkb.cpp
sh: o: not found
o src/input/toprider.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/input/toprider.cpp
sh: o: not found
o src/input/zapper.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/input/zapper.cpp
sh: o: not found
o src/utils/crc32.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/utils/crc32.cpp
sh: o: not found
o src/utils/endian.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/utils/endian.cpp
sh: o: not found
o src/utils/general.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/utils/general.cpp
sh: o: not found
o src/utils/guid.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/utils/guid.cpp
sh: o: not found
o src/utils/md5.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/utils/md5.cpp
sh: o: not found
o src/utils/memory.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/utils/memory.cpp
sh: o: not found
o src/utils/unzip.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/utils/unzip.cpp
sh: o: not found
o src/utils/xstring.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/utils/xstring.cpp
sh: o: not found
o src/mappers/151.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/151.cpp
sh: o: not found
o src/mappers/16.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/16.cpp
sh: o: not found
o src/mappers/17.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/17.cpp
sh: o: not found
o src/mappers/18.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/18.cpp
sh: o: not found
o src/mappers/193.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/193.cpp
sh: o: not found
o src/mappers/201.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/201.cpp
sh: o: not found
o src/mappers/202.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/202.cpp
sh: o: not found
o src/mappers/203.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/203.cpp
sh: o: not found
o src/mappers/204.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/204.cpp
sh: o: not found
o src/mappers/212.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/212.cpp
sh: o: not found
o src/mappers/213.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/213.cpp
sh: o: not found
o src/mappers/214.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/214.cpp
sh: o: not found
o src/mappers/215.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/215.cpp
sh: o: not found
o src/mappers/217.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/217.cpp
sh: o: not found
o src/mappers/21.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/21.cpp
sh: o: not found
o src/mappers/225.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/225.cpp
sh: o: not found
o src/mappers/227.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/227.cpp
sh: o: not found
o src/mappers/228.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/228.cpp
sh: o: not found
o src/mappers/229.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/229.cpp
sh: o: not found
o src/mappers/22.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/22.cpp
sh: o: not found
o src/mappers/230.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/230.cpp
sh: o: not found
o src/mappers/231.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/231.cpp
sh: o: not found
o src/mappers/232.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/232.cpp
sh: o: not found
o src/mappers/234.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/234.cpp
sh: o: not found
o src/mappers/241.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/241.cpp
sh: o: not found
o src/mappers/242.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/242.cpp
sh: o: not found
o src/mappers/244.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/244.cpp
sh: o: not found
o src/mappers/246.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/246.cpp
sh: o: not found
o src/mappers/24and26.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/24and26.cpp
sh: o: not found
o src/mappers/255.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/255.cpp
sh: o: not found
o src/mappers/25.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/25.cpp
sh: o: not found
o src/mappers/27.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/27.cpp
sh: o: not found
o src/mappers/32.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/32.cpp
sh: o: not found
o src/mappers/33.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/33.cpp
sh: o: not found
o src/mappers/40.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/40.cpp
sh: o: not found
o src/mappers/41.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/41.cpp
sh: o: not found
o src/mappers/42.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/42.cpp
sh: o: not found
o src/mappers/46.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/46.cpp
sh: o: not found
o src/mappers/50.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/50.cpp
sh: o: not found
o src/mappers/51.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/51.cpp
sh: o: not found
o src/mappers/59.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/59.cpp
sh: o: not found
o src/mappers/60.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/60.cpp
sh: o: not found
o src/mappers/61.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/61.cpp
sh: o: not found
o src/mappers/62.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/62.cpp
sh: o: not found
o src/mappers/65.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/65.cpp
sh: o: not found
o src/mappers/67.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/67.cpp
sh: o: not found
o src/mappers/69.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/69.cpp
sh: o: not found
o src/mappers/6.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/6.cpp
sh: o: not found
o src/mappers/71.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/71.cpp
sh: o: not found
o src/mappers/72.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/72.cpp
sh: o: not found
o src/mappers/73.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/73.cpp
sh: o: not found
o src/mappers/75.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/75.cpp
sh: o: not found
o src/mappers/76.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/76.cpp
sh: o: not found
o src/mappers/77.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/77.cpp
sh: o: not found
o src/mappers/79.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/79.cpp
sh: o: not found
o src/mappers/80.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/80.cpp
sh: o: not found
o src/mappers/82.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/82.cpp
sh: o: not found
o src/mappers/83.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/83.cpp
sh: o: not found
o src/mappers/85.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/85.cpp
sh: o: not found
o src/mappers/86.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/86.cpp
sh: o: not found
o src/mappers/89.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/89.cpp
sh: o: not found
o src/mappers/8.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/8.cpp
sh: o: not found
o src/mappers/91.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/91.cpp
sh: o: not found
o src/mappers/92.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/92.cpp
sh: o: not found
o src/mappers/97.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/97.cpp
sh: o: not found
o src/mappers/99.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/99.cpp
sh: o: not found
o src/mappers/mmc2and4.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/mmc2and4.cpp
sh: o: not found
o src/mappers/simple.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/mappers/simple.cpp
sh: o: not found
o src/drivers/sdl/input.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/drivers/sdl/input.cpp
sh: o: not found
o src/drivers/sdl/config.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/drivers/sdl/config.cpp
sh: o: not found
o src/drivers/sdl/sdl.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/drivers/sdl/sdl.cpp
sh: o: not found
o src/drivers/sdl/sdl-joystick.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/drivers/sdl/sdl-joystick.cpp
sh: o: not found
o src/drivers/sdl/sdl-sound.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/drivers/sdl/sdl-sound.cpp
sh: o: not found
o src/drivers/sdl/sdl-throttle.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/drivers/sdl/sdl-throttle.cpp
sh: o: not found
o src/drivers/sdl/sdl-video.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/drivers/sdl/sdl-video.cpp
sh: o: not found
o src/drivers/sdl/unix-netplay.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/drivers/sdl/unix-netplay.cpp
sh: o: not found
o src/drivers/sdl/sdl-opengl.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr/include/lua5.1 src/drivers/sdl/sdl-opengl.cpp
sh: o: not found
o src/fceux src/asm.o src/cart.o src/cheat.o src/conddebug.o src/config.o src/debug.o src/drawing.o src/fceu.o src/fds.o src/file.o src/filter.o src/ines.o src/input.o src/netplay.o src/nsf.o src/oldmovie.o src/palette.o src/ppu.o src/sound.o src/state.o src/unif.o src/video.o src/vsuni.o src/wave.o src/x6502.o src/movie.o src/lua-engine.o src/boards/01-222.o src/boards/103.o src/boards/106.o src/boards/108.o src/boards/112.o src/boards/117.o src/boards/120.o src/boards/121.o src/boards/15.o src/boards/164.o src/boards/175.o src/boards/176.o src/boards/177.o src/boards/178.o src/boards/179.o src/boards/183.o src/boards/185.o src/boards/186.o src/boards/187.o src/boards/189.o src/boards/199.o src/boards/208.o src/boards/222.o src/boards/23.o src/boards/235.o src/boards/3d-block.o src/boards/411120-c.o src/boards/43.o src/boards/57.o src/boards/603-5052.o src/boards/68.o src/boards/8157.o src/boards/8237.o src/boards/830118C.o src/boards/88.o src/boards/90.o src/boards/95.o src/boards/a9711.o src/boards/a9746.o src/boards/addrlatch.o src/boards/ax5705.o src/boards/bandai.o src/boards/bmc13in1jy110.o src/boards/bmc42in1r.o src/boards/bmc64in1nr.o src/boards/bmc70in1.o src/boards/bonza.o src/boards/bs-5.o src/boards/copyfami_mmc3.o src/boards/dance.o src/boards/datalatch.o src/boards/deirom.o src/boards/dream.o src/boards/__dummy_mapper.o src/boards/edu2000.o src/boards/fk23c.o src/boards/ghostbusters63in1.o src/boards/gs-2004.o src/boards/gs-2013.o src/boards/h2288.o src/boards/karaoke.o src/boards/kof97.o src/boards/konami-qtai.o src/boards/ks7032.o src/boards/malee.o src/boards/mmc1.o src/boards/mmc3.o src/boards/mmc5.o src/boards/n-c22m.o src/boards/n106.o src/boards/n625092.o src/boards/novel.o src/boards/sachen.o src/boards/sc-127.o src/boards/sheroes.o src/boards/sl1632.o src/boards/smb2j.o src/boards/subor.o src/boards/super24.o src/boards/supervision.o src/boards/t-227-1.o src/boards/t-262.o src/boards/tengen.o src/boards/tf-1201.o src/drivers/common/args.o src/drivers/common/cheat.o src/drivers/common/config.o src/drivers/common/hq2x.o src/drivers/common/hq3x.o src/drivers/common/scale2x.o src/drivers/common/scale3x.o src/drivers/common/scalebit.o src/drivers/common/vidblit.o src/drivers/common/configSys.o src/input/arkanoid.o src/input/bworld.o src/input/cursor.o src/input/fkb.o src/input/ftrainer.o src/input/hypershot.o src/input/mahjong.o src/input/mouse.o src/input/oekakids.o src/input/powerpad.o src/input/quiz.o src/input/shadow.o src/input/suborkb.o src/input/toprider.o src/input/zapper.o src/utils/ConvertUTF.o src/utils/crc32.o src/utils/endian.o src/utils/general.o src/utils/guid.o src/utils/md5.o src/utils/memory.o src/utils/unzip.o src/utils/xstring.o src/mappers/151.o src/mappers/16.o src/mappers/17.o src/mappers/18.o src/mappers/193.o src/mappers/201.o src/mappers/202.o src/mappers/203.o src/mappers/204.o src/mappers/212.o src/mappers/213.o src/mappers/214.o src/mappers/215.o src/mappers/217.o src/mappers/21.o src/mappers/225.o src/mappers/227.o src/mappers/228.o src/mappers/229.o src/mappers/22.o src/mappers/230.o src/mappers/231.o src/mappers/232.o src/mappers/234.o src/mappers/241.o src/mappers/242.o src/mappers/244.o src/mappers/246.o src/mappers/24and26.o src/mappers/255.o src/mappers/25.o src/mappers/27.o src/mappers/32.o src/mappers/33.o src/mappers/40.o src/mappers/41.o src/mappers/42.o src/mappers/46.o src/mappers/50.o src/mappers/51.o src/mappers/59.o src/mappers/60.o src/mappers/61.o src/mappers/62.o src/mappers/65.o src/mappers/67.o src/mappers/69.o src/mappers/6.o src/mappers/71.o src/mappers/72.o src/mappers/73.o src/mappers/75.o src/mappers/76.o src/mappers/77.o src/mappers/79.o src/mappers/80.o src/mappers/82.o src/mappers/83.o src/mappers/85.o src/mappers/86.o src/mappers/89.o src/mappers/8.o src/mappers/91.o src/mappers/92.o src/mappers/97.o src/mappers/99.o src/mappers/emu2413.o src/mappers/mmc2and4.o src/mappers/simple.o src/drivers/sdl/input.o src/drivers/sdl/config.o src/drivers/sdl/sdl.o src/drivers/sdl/sdl-joystick.o src/drivers/sdl/sdl-sound.o src/drivers/sdl/sdl-throttle.o src/drivers/sdl/sdl-video.o src/drivers/sdl/unix-netplay.o src/drivers/sdl/sdl-opengl.o -L/usr/lib -lz -llua5.1 -lGL -lSDL
sh: o: not found
Copy("bin/fceux", "src/fceux")
scons: *** [bin/fceux] src/fceux: No such file or directory
scons: building terminated because of errors.

```

Can anyone help with this?

---

### Post by lariosa42 on 2009-05-04
Any tips on doing this for us svn-virgins?

---

### Post by Grishka on 2009-05-04
> **lariosa42 said:**
> Any tips on doing this for us svn-virgins?

install [subversion]("apt://subversion"). then do ```
svn co https://fceultra.svn.sourceforge.net/svnroot/fceultra/fceu/
svn co https://fceultra.svn.sourceforge.net/svnroot/fceultra/gfceux
```
and proceed with the installation as normal. or get a gui for subversion, like [this one]("apt://subcommander").

---

### Post by reloweb on 2009-05-24
I've installed fceu and gfceux both from svn and source but when I launch gfceux it return me this:
```
Traceback (most recent call last):
  File "/usr/bin/gfceux", line 9, in <module>
    from gfceux import main
ImportError: No module named gfceux
```

EDIT: I've solved
One thing, when i'm in game, the sound result a bit not synchronized. How I resolve it?

---

### Post by f16 on 2009-05-25
Hello, gfce hangs after sometime.:confused:
[FONT="Arial Black"][SIZE="5"]Why?[/SIZE][/FONT][CENTER][/CENTER]

---

### Post by droazen on 2009-05-28
For those who are sick of having to compile fceux from source, there is an experimental "official" ubuntu package built on 2009-05-09 available in this PPA:

[https://edge.launchpad.net/~fabricesp/+archive/experimental]("https://edge.launchpad.net/~fabricesp/+archive/experimental")

The packager needs people to test it on their systems and report the results in a comment to this bug report:

[https://bugs.launchpad.net/ubuntu/+source/fceu/+bug/254352]("https://bugs.launchpad.net/ubuntu/+source/fceu/+bug/254352")

If it works for people, it will be submitted for inclusion in a future version of ubuntu (finally!)

---

### Post by oleoleole on 2009-05-29
> **reloweb said:**
> I've installed fceu and gfceux both from svn and source but when I launch gfceux it return me this:
```
Traceback (most recent call last):
  File "/usr/bin/gfceux", line 9, in <module>
    from gfceux import main
ImportError: No module named gfceux
```

EDIT: I've solved
One thing, when i'm in game, the sound result a bit not synchronized. How I resolve it?

And how did you solve it?

---

### Post by James79 on 2009-05-30
Hi. Firstly - thanks to those who've picked up and extended the FCEU project. I love this emulator.

2 things -

1. I recently upgraded my TV to a plasma 1920x1080. Games now seem a little jerky. In fceu it's tolerable but still noticeable; in fceux it's downright unplayable and slow. I've tried turning everything down, and using OpenGL. The best settings seem to be to render to a smaller resolution like 640x480 and have it stretch to fit the screen, but it's still not perfect. It's frustrating because I don't appear to be cpu limited - the emu takes roughly 20% according to top (amd X2 1.8ghz). Any ideas?

2. I truly don't understand why all these emus don't let you map important things like save/load state, and EXIT to *controller buttons*. Surely I'm not the only person who plays this with a MythTv frontend, on a keyboardless computer? Currently I'm using qjoypad to work around this situation but it feels like a dirty hack and not entirely reliable. 

Thanks!

---

### Post by reloweb on 2009-06-01
> **oleoleole said:**
> And how did you solve it?

I've compiled it with --prefix=/usr/local/ both fceux and gfceux

---

### Post by slightlystoopid on 2009-06-06
I'm trying to reinstall FCEUX on Jaunty. Everything appears to install fine, except when I try to run it I get```
Starting FCEUX 2.1.0a...
Could not initialize SDL: No available video device.

```I tried compiling from source as well as downloading the .deb off launchpad. Apparently I'm missing something related to SDL, but I don't know what. ```
dpkg -l *sdl* | grep ii
ii  libsdl-gfx1.2-4                            2.0.13-4                                                 drawing and graphical effects extension for 
ii  libsdl-gfx1.2-dev                          2.0.13-4                                                 development files for SDL_gfx
ii  libsdl-image1.2                            1.2.6-3                                                  image loading library for Simple DirectMedia
ii  libsdl-image1.2-dev                        1.2.6-3                                                  development files for SDL 1.2 image loading 
ii  libsdl-mixer1.2                            1.2.8-5                                                  mixer library for Simple DirectMedia Layer 1
ii  libsdl-mixer1.2-dev                        1.2.8-5                                                  development files for SDL1.2 mixer library
ii  libsdl-sound1.2                            1.0.3-3                                                  Decoder of several sound file formats for SD
ii  libsdl-sound1.2-dev                        1.0.3-3                                                  Development files for SDL_sound
ii  libsdl-ttf2.0-0                            2.0.9-1                                                  ttf library for Simple DirectMedia Layer wit
ii  libsdl-ttf2.0-dev                          2.0.9-1                                                  development files for SDL ttf library (versi
ii  libsdl1.2-dev                              1.2.13-4ubuntu3                                          Simple DirectMedia Layer development files
ii  libsdl1.2debian                            1.2.13-4ubuntu3                                          Simple DirectMedia Layer
ii  libsdl1.2debian-all                        1.2.13-4ubuntu3                                          Simple DirectMedia Layer (with all available

```

---

### Post by slightlystoopid on 2009-06-07
ugh, the SDL FAQs have this... > Q:	I get the error: "no video devices available"
A:	SDL doesn't use the X11 video driver if it can't open the X display, and if no other drivers are available, it will report this error.
To fix this, set your display environment variable appropriately:
sh: DISPLAY=:0 ; export DISPLAY
csh: setenv DISPLAY :0
If you still have problems, try running xhost + localhost
Finally, if all those didn't work, and you built SDL from source, make sure that you have the X11 development libraries installed, otherwise you'll get a version of SDL that doesn't include X11 display support. After you install the X development libraries, you need to "make clean" and then rerun the configure and build process.
of course, the DISPLAY variable is set properly, and xhost +localhost doesn't do anything. all X11 dev librarys are insalled. man, a complete SDL removal and reinstall would require removing soooo much stuff. and it's probably not gonna work anyway. *sigh*

---

### Post by ArCeSiNo on 2009-06-09
> **nortexoid said:**
> I just installed in Jaunty using the .deb, and while fceux works, the graphical interface gfeux doesn't. This is the error I get:

```
Traceback (most recent call last):
  File "/usr/bin/gfceux", line 9, in <module>
    from gfceux import main
ImportError: No module named gfceux
```

Any ideas?

I have the same problem. I solved it running the script at **/usr/bin/gfceux** with **python2.5**. Remember that the version installed by default on jaunty is 2.6... so just run in a terminal

***python2.5 /usr/bin/gfceux***

---

### Post by Loranga on 2009-06-11
Any ideas about "native" Game Genie support? (i mean, that GG codes can be entered directly on the command line / GUI without using a GG rom). Like in FCEU for Windows.

---

### Post by Teclas5 on 2009-06-13
I installed it and have it up and running. I'm still trying to figure out how to use the Game Genie emulation. Any help or tutorials would be most appreciated.  :D

---

### Post by sticmann on 2009-06-23
Hello all,
Fantastic piece of work here. This may be a bit out, but I'm trying to use a PSX controller that I modded to fit into the parallel port. All the buttons work, but the directional pad doesn't. It is recognized by other js calibration tools, but fceux just doesn't pick it up. Any ideas? Can I edit the config file manually to get it to recognize these?

Thanks.

---

### Post by punkrockguy318 on 2009-06-23
> **sticmann said:**
> Hello all,
Fantastic piece of work here. This may be a bit out, but I'm trying to use a PSX controller that I modded to fit into the parallel port. All the buttons work, but the directional pad doesn't. It is recognized by other js calibration tools, but fceux just doesn't pick it up. Any ideas? Can I edit the config file manually to get it to recognize these?

Thanks.

I have the same problem with my 360 controller.  Fceux has trouble recognizing any part of the controller that the OS treats as a "hat" right now

---

### Post by punkrockguy318 on 2009-06-23
As for the person that was complaining about low framerate, try turning openGL off and turning compiz off if it is on.

---

### Post by sticmann on 2009-06-23
> **punkrockguy318 said:**
> I have the same problem with my 360 controller.  Fceux has trouble recognizing any part of the controller that the OS treats as a "hat" right now

Thank you for the quick reply. Do you know if this is something that is being worked on? Is this a common issue or an outside case?

---

### Post by khelben1979 on 2009-07-14
I just wanted to mention that I have been able to run FCEUX 2.1.1 (during this summer) successfully on the ppc linux platform and as of today 2.1.0 have been tested and working with no problems on my pc linux system as of today.

Is this the best nes emulator available for Linux today? (when thinking about cpu efficency and stability)

It has been the only NES emulator which I have successfully used on a ppc linux system, ever.

---

### Post by carlosalvatore on 2009-07-26
> **ArCeSiNo said:**
> I have the same problem. I solved it running the script at **/usr/bin/gfceux** with **python2.5**. Remember that the version installed by default on jaunty is 2.6... so just run in a terminal

***python2.5 /usr/bin/gfceux***

# python2.5 setup.py install --prefix=/usr/local

solves the problem, at install stage

greetings

---

### Post by mister_playboy on 2009-07-27
EDIT:Never mind... post above me solved it.

---

### Post by Redmage913 on 2009-08-04
Greetings,

I just tried installing from the source file, and I came across a huge problem in doing so.

I copy-pasted the long sudo apt-get install command and installed the necessary packages.  I also extracted the fceu and gfceux folders to the home directory.

When I ran the sudo scons install command, the entire process failed.  I was getting not found errors for every file it tried to work with.

I would include an entire terminal entry, but it ran way longer than the terminal length before it starts cropping the oldest lines.

Any ideas?

Thanks much,
Redmage913

PS Running Xubuntu 9.04 on a Dell Mini 9.

---

### Post by holamyburrito on 2009-08-18
I just installed the latest version of FCEUX from source and I'm having the same input problem described a few pages back. I have liblua5.1-dev installed, and I even tried running sudo apt-get install liblua5.1* and with all the packages it still doesn't accept input after config.

Can anyone help?

---

### Post by holamyburrito on 2009-08-21
Anyone at all?

---

### Post by s0up on 2009-10-23
> **Redmage913 said:**
> Greetings,

I just tried installing from the source file, and I came across a huge problem in doing so.

I copy-pasted the long sudo apt-get install command and installed the necessary packages.  I also extracted the fceu and gfceux folders to the home directory.

When I ran the sudo scons install command, the entire process failed.  I was getting not found errors for every file it tried to work with.

I would include an entire terminal entry, but it ran way longer than the terminal length before it starts cropping the oldest lines.

Any ideas?

Thanks much,
Redmage913

PS Running Xubuntu 9.04 on a Dell Mini 9.

I had this problem as well.  You need to install g++:
```
sudo aptitude install g++
```

---

### Post by hellocatfood on 2009-11-07
I've installed to Ubuntu 9.10 using the instructions on your website and I get choppy sound. Is there any way to fix this? I tried changing the Buffer size and Sample rate but it had little effect

---

### Post by sou_agua on 2009-11-09
Trying to get FCEUX working on my gf's old laptop (running ubuntu 8.04).  Here is the error I get when I try to run sudo scons install:

```
scons: Reading SConscript files ...
NameError: name 'Variables' is not defined:
  File "/home/nikki/fceux-2.1.2.src/fceu/SConstruct", line 5:
    opts = Variables()

```

The laptop is a Compaq with AMD64 processor.  I've read through this thread and the FAQ on the fceu website.  I haven't played with any Linux stuff in a long time.  Is the fix on this something easy that I'm forgetting?  I installed all the dependencies from the beginning of this HOWTO, and tried svn, and installed gtk++.  No dice yet.

Thanks,
~S

---

### Post by Stuart P. Bentley on 2009-11-13
I'm not getting a window when I go Applications->Games->FCEUX NES Emulator.

> stuart@stuback:~$ gfceux
Traceback (most recent call last):
  File "/usr/bin/gfceux", line 9, in <module>
    from gfceux import main
ImportError: No module named gfceux


Also, what's the progress on replacing the GFCEU and FCEU entries in the Ubuntu Software Center?

---

### Post by kissg1988 on 2009-11-18
To eliminate the "ImportError: No module named gfceux" error message, just open the file "/usr/bin/gfceux" with a text editor and append the numbers "2.5" to the very first line, so it reads:

```
#!/usr/bin/python2.5
```

This solved the problem for me on Jaunty, it certainly has to do the trick on Karmic, too.

They switched to Python 2.6 in Jaunty, but fortunately the old version is still available.

---

### Post by punkrockguy318 on 2009-12-30
Hey all,
I know I'm sort of bringing this thread back from the dead, but I wanted to announce that I'm starting work on an integrated GTK GUI for FceuX.  This will eliminate the need for a launcher program since options will changeable during run-time.

I've currently just begun work on this, and there are only a few basic features but if you want to check it out, compile the subversion source with the GTK flag checked (ie:  scons GTK=1 install)

If anyone is interested in working on this with me shoot me a PM.

---

### Post by quequotion on 2010-01-07
In order to get gfceux to work (after compiling without a prefix) I tried to cut out everything to do with the network setup. (there's a *colorful* comment in main.py justifying this action as well...)

take a look at this main.py (from /usr/local/lib/python2.6/dist-packages/gfceux/) in which I've commented out everything that i thought might be relevant.. I am not familiar with the code however so it's pretty likely I did something wrong. I did make one small deletion, where "network" was requested whenever you hit a button on the gui.

The good news is, fceux works fine anyway, and now I can even use gfceux to configure the controllers, screen, sound, and load games. (haven't tried any lua scripts yet.)

Also, there's another bug in uninstall.py for gfceux, where it looks for files in the wrong directory (after installing with a prefix). I've attached my revision to this as well...

ps - I'd very much like to work with the svn directly but the checkout link on the homepage doesn't seem to be working... is it just me or is the repository down?

---

### Post by punkrockguy318 on 2010-01-07
> **quequotion said:**
> In order to get gfceux to work (after compiling without a prefix) I tried to cut out everything to do with the network setup. (there's a *colorful* comment in main.py justifying this action as well...)

take a look at this main.py (from /usr/local/lib/python2.6/dist-packages/gfceux/) in which I've commented out everything that i thought might be relevant.. I am not familiar with the code however so it's pretty likely I did something wrong. I did make one small deletion, where "network" was requested whenever you hit a button on the gui.

The good news is, fceux works fine anyway, and now I can even use gfceux to configure the controllers, screen, sound, and load games. (haven't tried any lua scripts yet.)

Also, there's another bug in uninstall.py for gfceux, where it looks for files in the wrong directory (after installing with a prefix). I've attached my revision to this as well...

ps - I'd very much like to work with the svn directly but the checkout link on the homepage doesn't seem to be working... is it just me or is the repository down?

Hey, thanks a lot for reporting that.  I actually screwed that up a little while ago and didn't know it got committed broken as all hell.

I also just fixed the uninstall script in svn; i changed the default install a while ago to /usr/local and I guess i forgot to change that. .  python doesn't really have a good install/uninstall mechanism (well I guess autotools don't either)

gfceux will probably not get any more features from me, as I'm putting my time into the GTK GUI for fceux right now.  The GUI currently runs in a seperate window due to technical limitations right now, but if/when SDL 1.3 gets released, this will be a lot better to integrate.  With the seperate window you will be able to change options and controls on the fly, and will be much more integrated with the emu itself

expect some good things when I have some spare time

---

### Post by MatthewJohn on 2010-01-09
im having trouble getting sound working with fceux, and im pretty sure its a SDL issue. i have a ion 330 motherboard and im using hdmi for audio, its working for everything else but sdl applications. i did however get mednafen to work but only after changing settings that are not available in fceux, i used -sounddriver alsa and -sounddevice sexyal-literal-default

if anyone knows how to fix this or force sdl to use a different sound device for every application that should fix it.

---

### Post by Shaggin Shea on 2010-01-12
> **MatthewJohn said:**
> im having trouble getting sound working with fceux, and im pretty sure its a SDL issue. i have a ion 330 motherboard and im using hdmi for audio, its working for everything else but sdl applications. i did however get mednafen to work but only after changing settings that are not available in fceux, i used -sounddriver alsa and -sounddevice sexyal-literal-default

if anyone knows how to fix this or force sdl to use a different sound device for every application that should fix it.
I am having this or a similar problem as well, I did find this [http://sourceforge.net/tracker/index.php?func=detail&aid=2919837&group_id=13536&atid=113536](http://sourceforge.net/tracker/index.php?func=detail&aid=2919837&group_id=13536&atid=113536) which mentions updating libSDL-1.2.14 from version 1.2.13 which is apparently in the Lucid suppositoy. I am using ubuntu 9.10 (I don't even know what libSDL version I am using) could somebody let me know how to check/update this? I will post the results. Hope this helps you matthewjohn

******UPDATE******
I was able, it seems, to solve my sound jitter and emulator crashing as follows
1. I already had followed the howto and was getting crashes/choppy sound
1.a. I downloaded and intalled [libsdl1.2_1.2.14.orig.tar.gz]("http://archive.ubuntu.com/ubuntu/pool/main/libs/libsdl1.2/libsdl1.2_1.2.14.orig.tar.gz") found here [http://packages.ubuntu.com/source/lucid/libsdl1.2](http://packages.ubuntu.com/source/lucid/libsdl1.2)
Please note I am using ubuntu Karmic 9.10 and had to go to the ubuntu lucid(10.x) packages to do the update. Apparently as far as I could tell from other forum threads the sdl libraries even though it's a minor update number 1.2.13 ->1.2.14 it fixed a not so minor bug. But the update is not in karmic repositories.
2. Followed the rest of the howto even the gefcux part (maybe unnecessary)
Tada! My sound emulation came out much better, perfect maybe.
Hope this helps someone else!

---

### Post by Shaggin Shea on 2010-01-15
Now I have a separate problem.
When I am trying to set the controls for my xbox controller terminal gives me a segmentation fault. It has something to do with the directional pad. When I push the joystick, both the left analogue and the left directional pad.

Left Directional pad is the worst

Starting FCEUX 2.0.3...
GamePad #1: A (1)
GamePad #1: A (2)
GamePad #1: B (1)
GamePad #1: B (2)
GamePad #1: SELECT (1)
GamePad #1: SELECT (2)
GamePad #1: START (1)
GamePad #1: START (2)
GamePad #1: UP (1)
Segmentation fault


I get through sometimes with the analogue but it's not pretty, for some reason it shoots forward in the setup of the controls (for example it says push up I do, then it asks me to push turbo b) here is a sample analouge controller fceux.cfg for controller 0 (player 1)

SDL.Input.GamePad.0A = 49152
SDL.Input.GamePad.0B = 32768
SDL.Input.GamePad.0DeviceNum = 0
SDL.Input.GamePad.0Down = 32768
SDL.Input.GamePad.0Left = 32768
SDL.Input.GamePad.0Right = 32768
SDL.Input.GamePad.0Select = 32768
SDL.Input.GamePad.0Start = 32768
SDL.Input.GamePad.0TurboA = 32768
SDL.Input.GamePad.0TurboB = 32768
SDL.Input.GamePad.0Up = 32768

---

### Post by revmns on 2010-01-21
I installed gfceux in karmic using the scons command but now I am having trouble removing it. I was wanting to use sixaxis as a usb controler but didnt get anywhere so i figured that I would just remove gfceux. Any help would be appreciated.

thanks.

---

### Post by NewWorld on 2010-01-23
> **sou_agua said:**
> Trying to get FCEUX working on my gf's old laptop (running ubuntu 8.04).  Here is the error I get when I try to run sudo scons install:

```
scons: Reading SConscript files ...
NameError: name 'Variables' is not defined:
  File "/home/nikki/fceux-2.1.2.src/fceu/SConstruct", line 5:
    opts = Variables()

```

The laptop is a Compaq with AMD64 processor.  I've read through this thread and the FAQ on the fceu website.  I haven't played with any Linux stuff in a long time.  Is the fix on this something easy that I'm forgetting?  I installed all the dependencies from the beginning of this HOWTO, and tried svn, and installed gtk++.  No dice yet.

Thanks,
~S

I worked around that by replacing 'Variables' in lines 5-6 with 'Options'. And replacing 'Variable' in lines 7-14 with 'Option'. That's how I found the code to look like in an older version of the program. :)

---

### Post by bgiannes on 2010-01-28
sudo apt-get install fceu gfceu

works for me in 9.10, but how do i do keyboard and gamepad maping?

i tryed:

"gfcue gamepad mapper" but the dialog box just flys through the "wrong" keys??  my "gamepad1" is a usb gen joy-pad

ps i'm running it from mythgames with this command, so i don't really need gfceu as mythtv is my fecu gui

fceu -fs 1 -sound 1 -input 1 -xres 1024 -yres 768 -soundvol 25 %s


UPDATE:

got it fixed, edit the fceu.cfg file and make all the gamespad values 0, then re-run the gfceu gamespad setup.

---

### Post by rifter on 2010-02-09
> **hellocatfood said:**
> I've installed to Ubuntu 9.10 using the instructions on your website and I get choppy sound. Is there any way to fix this? I tried changing the Buffer size and Sample rate but it had little effect

I actually installed this because the ubuntu-included fceu and gfceu had choppy sound, which I determined was caused somehow by pulseaudio (on 9.10) even when I used the commands that force things to pulseaudio.  Having gotten some success in wine by directing things to esd, I tried to get esddsp to work but that gave no joy.

I found that if I launched gfceux as

esddsp gfceux

the sound was perfect.

What's funny about this is that on 9.10 the esd apparently has a wrapper to pulseaudio.  nevertheless this works, so you should try it.

---

### Post by rifter on 2010-02-09
By the way, in 9.10 with 2.1.2 of gfceux I still have the mouse cursor bug.  It is not stuck in the middle of the screen; I can move it, but it does not get hidden :P.

Still, so far this is the only emulator I have gotten to work right, so props! :D

---

### Post by Redmage913 on 2010-02-18
Hey there,

I have a weird experience opening the program - unless I open up the gfceux python script from thunar (I'm running xubuntu 9.04), I can't open it up. I can't open it from applications->games->FCEUX NES Emulator or using the alt+f2 run program tool.

The program runs fine for me, just the way I'm forced to open it is a little strange in my mind.  Any ideas?

EDIT: it will open up the terminal if i type in 'python gfceux' (minus quotes).

---

### Post by punkrockguy318 on 2010-02-18
Hey all, fceuX-sdl dev here.  I see you guys have brought up a lot of new issues so I'm going to try to address all of them.

* Fullscreen cursor not being hidden - FIXED in r1651

* Audio issues - First, try running fceuX through esddsp.  If you're using pulseaudio and not alsa, this should eliminate all poor audio performance.  Secondly, as mentioned earlier, update to SDL 1.2.14.  There are some audio-related bug fixes in that update that are relevant to fceuX.  I'm not sure if there's a package yet, but it will be default in Ubuntu+1 and it's simple to install via source.  TBH, i'm not sure why SDL 1.2.14 isn't in the update repository yet.  THANKS SHAGGIN SHEA FOR THE ESDDSP TIP!  I was hacking the SDL sound code for weeks, and it wans't even an issue in my code. :mad:

* Input configuration issues - Let me start off by saying that the "--inputcfg" system used in fceuX is extremely outdated and has a lot of problems right now.  I'm working on it.  For now, use a third party utility to map joystick buttons to KEYS.  I know there are apps that do this but I can't think of the names off hand, search the apt repos.

* Scons bombing out - You're using a pretty damn old version of scons.  Either update to the latest scons, or replace each instance of variables with options like Shaggin Shea mentioned earlier.

* GFceux issues - Gfceux is getting depreciated.  FceuX is getting a GTK GUI that will remove the need for a launcher.  If you'd like to try it out, enable the GTK option in the SConstruct (line 15).  Just change the 0 to 1 and you're good to go.

This thread seems to be the most active discussion of the SDL version of fceuX.  I encourage you all to participate in the fceuX community ([http://fceux.com](http://fceux.com)).  I reply to the mailing list ASAP, and check the tracker fairly often.  We're also fairly active on IRC (#fceu @ irc.freenode.net) so come check us out there.

Furthermore, you can contact me directly at < LTsmooth42 _at_ gmail _dot_ com > .  I'm not bothered by questions / feedback / issues related to fceuX because I want to see fceuX be as good as it can be.

So, now that that's settled, you guys can kick back and play some f*****g nintendo while I code away :popcorn::popcorn::popcorn:

Enjoy!

-Lukas

---

### Post by punkrockguy318 on 2010-02-18
Hey all;
I've been doing a lot of work on the GTK GUI.  I just added a lot of menu options.  The GTK UI desperately needs some testing outside of my box. 

If you'd like to test it, enable GTK in the SConstruct and rebuild fceuX

Make sure you get the latest svn if you want to test (i've been making a lot of changes, so make sure you svn up often)

Please, stress test this in every single way.  I'd like to get all the bugs cleared out of this so I can start adding all the features I'd like to add to the GUI.

I'm also idling on IRC if anyone wants to chat and help test this.

Thanks!

---

### Post by litemirrors on 2010-02-18
I would use this but then why? I downloaded Mednafen then found this front end [http://ubuntuforums.org/showthread.php?t=813785](http://ubuntuforums.org/showthread.php?t=813785) programmed that still works. It supports more than just NES too!

---

### Post by punkrockguy318 on 2010-02-18
> **litemirrors said:**
> I would use this but then why? I downloaded Mednafen then found this front end [http://ubuntuforums.org/showthread.php?t=813785](http://ubuntuforums.org/showthread.php?t=813785) programmed that still works. It supports more than just NES too!

not forcing you to use anything; madnafen is a cool emu as well

fceuX just has a lot more features than what madnafen's nes emulator has.  i don't really feel like getting into details right now, but fceu is a lot more flexible for TAS, rom hacking, and other power-user features

the GUI for mednafen is a lot more fleshed out than the GUI for fceuX currently.  i'm the only person working on the GUI currently, and I also have a real job and a lot of other things to do.  However, I plan on devoting a lot of time in the near future for getting the GTK GUI up to speed with the win32 version and depreciating gfceux

use whatever you want.  i obviously have a biased opinion since I spend so much time coding fceuX, but I feel that I can say objectively that fceuX is much more powerful than mednafen, but it's obvious that mednafen has a much better GUI

Working to improve the GUI as we speak; I just committed a dialog to replace --inputcfg.  it's not finished, but it will save a lot of headaches once it is.

---

### Post by punkrockguy318 on 2010-02-19
I recommend this software for people who would like to use gamepads for hotkeys, or if they are having trouble getting their joysticks working with fceuX

[http://code.google.com/p/jkeys/](http://code.google.com/p/jkeys/)

---

### Post by punkrockguy318 on 2010-02-24
I've been doing a lot of work on the GTK GUI.  It's almost completely fleshed out.

Testing would be key here!  I have built an amd64 package for anyone that would like to give it a shot.

I've been working hard on the GTK GUI.  Almost everything in fceux.cfg is configurable via the GUI.  Here's a list of some stuff I added:
* inputcfg - no hotkeys yet, but there's a GUI for gamepad config
* video dialog 
* sound dialog - all options and mixers for each sound channel
* palette dialog - also includes color/tint/hue

movie loading, lua script loading, rom loading, and some other command are also available via menus

there's more to come and it will be polished more in the near future, but any feedback would be great!

here's a deb package for 64bit.  it was built on ubuntu 9.10 with SDL 1.2.14.  as with all linux binaries, YMMV, but if all else fails just compile the source in subversion.

[http://megaupload.com/=dFCMDASUI](http://megaupload.com/=dFCMDASUI)

---

### Post by punkrockguy318 on 2010-02-25
bump for update

---

### Post by quequotion on 2010-02-26
> **rifter said:**
> I actually installed this because the ubuntu-included fceu and gfceu had choppy sound, which I determined was caused somehow by pulseaudio (on 9.10) even when I used the commands that force things to pulseaudio.  Having gotten some success in wine by directing things to esd, I tried to get esddsp to work but that gave no joy.

I found that if I launched gfceux as

esddsp gfceux

the sound was perfect.

What's funny about this is that on 9.10 the esd apparently has a wrapper to pulseaudio.  nevertheless this works, so you should try it.

this is interesting, and possibly very important. [9.10 has serious problems with SDL audio]("http://ubuntuforums.org/showthread.php?t=1368141&page=14") I haven't seen using esddsp proposed yet, although a lot of similar half-workarounds have been tried, and no solution has been found so far...

---

### Post by Genecks on 2010-03-10
I'm on a Debian Lenny system. And I'm not getting sound. I used the first post's instructions in this thread. Maybe things have changed?

Either way, I'd really like sound.
Yes, sound on my box works (not with the FCEU, though).
I believe I'm using an ALSA setup at the moment.

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

---

### Post by Groucho Marxist on 2010-03-10
> **punkrockguy318 said:**
> I've been doing a lot of work on the GTK GUI.  It's almost completely fleshed out.

Testing would be key here!  I have built an amd64 package for anyone that would like to give it a shot.

I've been working hard on the GTK GUI.  Almost everything in fceux.cfg is configurable via the GUI.  Here's a list of some stuff I added:
* inputcfg - no hotkeys yet, but there's a GUI for gamepad config
* video dialog 
* sound dialog - all options and mixers for each sound channel
* palette dialog - also includes color/tint/hue

movie loading, lua script loading, rom loading, and some other command are also available via menus

there's more to come and it will be polished more in the near future, but any feedback would be great!

here's a deb package for 64bit.  it was built on ubuntu 9.10 with SDL 1.2.14.  as with all linux binaries, YMMV, but if all else fails just compile the source in subversion.

[http://megaupload.com/=dFCMDASUI](http://megaupload.com/=dFCMDASUI)

The link appears to be broken; would you be so kind as to re upload the 64bit package?

---

### Post by rifter on 2010-03-13
> **Genecks said:**
> I'm on a Debian Lenny system. And I'm not getting sound. I used the first post's instructions in this thread. Maybe things have changed?

Either way, I'd really like sound.
Yes, sound on my box works (not with the FCEU, though).
I believe I'm using an ALSA setup at the moment.

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

What kind of sound mixer are you using? (pulseaudio, esd, etc)?
If you don't know chances are the man pages will give a hint (did for me) try 
apropos esd
apropos pulseaudio
 
and see what you get.  You can force an application to use your mixer in those two cases with the 

esddsp

and

padsp

commands, respectively.  Just put either one before the program you are launching like:

esddsp gfceux

note that if you have pulseaudio it has a wrapper for esd. For some reason on my system even though I have pulseaudio some programs will not work with the padsp command but will with the esddsp command (which is a wrapper to pulseaudio that takes esd style input).  Your mileage may vary.

---

### Post by mocha on 2010-03-20
```
esddsp fceux /home/mocha/ROMS/NES/Recca.nes

Starting FCEUX 2.1.3 debug...
Loading /home/mocha/ROMS/NES/Recca.nes...

08120020 PRG ROM:    8 x 16KiB
 CHR ROM:   16 x  8KiB
 ROM CRC32:  0xf31dcc15
 ROM MD5:  0x86e917c37515ace20d3b50dca4551f3b
 Mapper #:  4
 Mapper name: MMC3
 Mirroring: Horizontal

Initializing video...Initializing with OpenGL (Disable with '-opengl 0').
 Video Mode: 256 x 224 x 32 bpp 
Paletted texture extension not found.  Using slower texture format...
Loading SDL sound with esd driver...
Quit
```

I just checked out version 1753.  Sound doesn't work very well.  Tried with padsp wrapper as well.  My system doesn't have pulseaudio problems in general.

Also, can't get any of the OpenGL scaling modes to work.  It's probably related to the OpenGL bug 2740043 on Sourceforge.  If I enable any of the scaling modes I just get a seg fault like this:

```
esddsp fceux /home/mocha/ROMS/NES/Recca.nes

Starting FCEUX 2.1.3 debug...
Loading /home/mocha/ROMS/NES/Recca.nes...

08120020 PRG ROM:    8 x 16KiB
 CHR ROM:   16 x  8KiB
 ROM CRC32:  0xf31dcc15
 ROM MD5:  0x86e917c37515ace20d3b50dca4551f3b
 Mapper #:  4
 Mapper name: MMC3
 Mirroring: Horizontal

Initializing video...Initializing with OpenGL (Disable with '-opengl 0').
 Video Mode: 768 x 672 x 32 bpp 
Paletted texture extension not found.  Using slower texture format...
Loading SDL sound with esd driver...
Segmentation fault
```

---

### Post by Braveheart1980 on 2010-03-20
I was wondering , how can I **remove** fceux , if installed with the method mentioned in the first post?

---

### Post by derrick81787 on 2010-03-22
Has anyone here ever gotten fceu to work with an XBox controller?  I have almost gotten it, but just can't quite get there.  I have everything working except for the d-pad, which fceu just won't recognize.  It's weird because SuperTux will recognize it, and fceu actually works with the joystick.  It's just that playing NES games with a joystick is awkward.

If anyone can offer any advice at all, I'd appreciate it.

- Derrick

---

### Post by cecilkorik on 2010-03-27
Like the dev said earlier, it seems the input configuration in FCEUX isn't up to par yet.

In the meantime you should use a joystick->keyboard mapper to make your joystick create keypresses instead of button presses. Personally I use [QJoyPad]("http://qjoypad.sourceforge.net/") which has profiles, can map axises as well as buttons, and has a very user friendly dialog to set everything up. You can even set up one of your analog sticks to act as a mouse, if you like!

Other alternatives that I've heard of but not tried include xjoypad and rejoystick (which I've heard good things about).

Unfortunately I don't think any of them come with a ubuntu package at this time. QJoypad wasn't difficult to compile. All I did was download the source and make sure that I had the needed libraries before running "./configure" then "make". 

If configure complains about missing libraries, try running the following apt-get:

```
sudo apt-get install build-essential libqt4-dev qt4-qmake libqtgui4 libqtcore4 libxtst6 libxtst-dev
```

That should get more or less everything you need to compile programs, including this one specifically.

---

### Post by derrick81787 on 2010-03-27
Thanks for that post.  I'll give it a try.  I tried jkeys once, but it didn't seem to map axis, just buttons, and for some reason the d-pad on the Xbox controller is an axis, not 4 buttons.

I'll try out some of those and post here about how it worked out.

Thanks,
Derrick

---

### Post by grnorris on 2010-03-27
I followed the method mostly but I had already downloaded the current version so I just followed the method from my download folder.  If I'm not mistaken I'm supposed to just move the folder elsewhere right?  If so what folder would you suggest (Single User-Ubuntu 9.1)

---

### Post by derrick81787 on 2010-03-28
> **derrick81787 said:**
> Thanks for that post.  I'll give it a try.  I tried jkeys once, but it didn't seem to map axis, just buttons, and for some reason the d-pad on the Xbox controller is an axis, not 4 buttons.

I'll try out some of those and post here about how it worked out.

Thanks,
Derrick

QJoyPad works great.  I'm running GNOME and so I tried the others first (since QJoyPad uses QT) but they weren't anywhere near as good as QJoyPad.  I tried Jojsticken, which is the newer rewrite of Rejoystick, but it just didn't recognise the d-pad.  Then I tried xjoypad, but it just wasn't very user friendly to set up.  QJoyPad ended up working great, and it was easy to compile and install.

- Derrick

---

### Post by Nisal on 2010-03-29
OK Going to try this ? what about system requirement ?

---

### Post by derrick81787 on 2010-03-29
> **Nisal said:**
> OK Going to try this ? what about system requirement ?

I didn't install FCEUX, but I installed the older version, FCEU, that is in the repositories.  I have a little, underpowered netbook, and it works fine, so I'd say the system requirements are pretty low.

The only problem I encountered was that the graphics were a little choppy on my cheap integrated video card.  Disabling OpenGL fixed that though.  I think the option I had to specify was **-opengl 0**.  After that, and after using QJoyPad to set up the controller, it works great for me.

- Derrick

---

### Post by punkrockguy318 on 2010-03-29
Hello all,

I really can't diagnose people's sound issues this way.

Sound is a mess in 9.10.

Please post the following info:
OS version
SDL_AUDIODRIVER (this is a big issue; it's buggy in < 10.4.
FceuX version

Fceu has such a different codebase from fceux at this point that I'm going to really offer support for anyone with troubles with fceu except this point of advice:  upgrade to fceux

I'd love to help people out here

I had sound working w/ fceux (svn) in 9.10 with export SDL_AUDIODRIVER=esd (while using pulseaudio) 

Sound works out of the box in 10.04; which I recommend everyone to upgrade to when it is released.

Just reiterating that the issues here are NOT with fceuX code; mostly issues with the SDLAUDIODRIVERs

---

### Post by punkrockguy318 on 2010-03-29
> **Braveheart1980 said:**
> I was wondering , how can I **remove** fceux , if installed with the method mentioned in the first post?

rm /usr/bin/fceux

or /usr/local/bin/fceux

everyone is tripping over being able to remove fceux

it's on binary file; you don't even really need to install it

---

### Post by bb93 on 2010-04-02
Hi guys!

My system is Ubuntu 9.10 64 bits, and it work's perfectly.

I did following steps:

1. Download Fceux tar.bz2 from [[COLOR="Navy"]here[/COLOR]]("http://sourceforge.net/projects/fceultra/files/")

2.  Install necessary dependencies. 

```

sudo apt-get install scons libsdl1.2-dev libsdl1.2debian-esd subversion libgtk2.0-dev

```

3.  Open a terminal (Applications... Accessories... Terminal) and obtain source from subversion.
```

svn co https://fceultra.svn.sourceforge.net/svnroot/fceultra fceultra 

```

4. Change directory into the fceu folder.

```
cd fceultra/fceu
```

5.  Build and install fceux.

```
sudo scons GTK=1 install
```

6. Type: **fceux**

Thanks punkrockguy318.

---

### Post by rifter on 2010-04-13
I recently had to do this again, for my 64 bit machine.
I noted that you install libsdl1.2debian-esd and that was going to uninstall (on my machine) libsdl1.2debian-alsa.  I noticed that there is a libsdl1.2debian-all that allows for all of the options.  I installed that instead and the only difference I have to make now is to specify esd before starting gfceux by setting the environment variable
```

export SDL_AUDIODRIVER=esd

```
I have that in my .profile now, but I have also tested using the following in the launch for gfceux that I created in the menu
```

env  "SDL_AUDIODRIVER=esd" /usr/local/bin/fceux

```

Hope this helps if someone wanted to make sure their SDL library had support for other sound options.  ESD is still the only one that works right for me for gfceux.

---

### Post by Redmage913 on 2010-04-18
I compiled FCEUX using the instructions in the first post, and I'm VERY happy to say it compiles just fine under Lucid Ubuntu.  I'm running the 32-bit beta/release candidate (according to the roadmap we're in-between them with a freeze on just about everything, so I'm guessing it's about the release candidate at this point)

It's a little choppy, but at the same time, I'm running a bit of an underpowered machine (Dell Mini 9: 1024 MB RAM, 1.6 Intel Atom, Intel GMA 950).

By the way, what would you say the minimum specs are nowadays for this program?

Thanks,

--Red

EDIT: P.S. I found that the emulator runs as smooth as can be without sound enabled (even at 400% speed), which for me is fine because I normally tend to play Final Fantasy when I'm in class, when I sit in waiting rooms, etc.

---

### Post by bb93 on 2010-05-08
It works in Ubuntu 10.04 x64 too :p

---

### Post by dbbolton on 2010-05-08
Well, sound was working for me in 2.1.2, but after installing 2.1.3, it doesn't (running Debian squeeze)

```
echo $DISPLAY
:0

echo $SDL_AUDIODRIVER
esd
```

I ran
```
esddsp fceux file.rom
```

and got this:
```
Loading SDL sound with  &#65533;&#65533;  driver...
No available audio device
```

Notice the Unicode junk as the name of the driver. It is different every time. Some others that have appeared:
```
@&#65533;&#65533;
&#65533;&#65533;&#65533;
`&#65533;D
`&#65533;

```

---

### Post by bb93 on 2010-05-09
Anybody can play via network on Fceux? Or it's not possible??

---

### Post by PerfectReign on 2010-06-10
Many thanks to the OP - this worked great. I'm now up on FCEUX 2.0.  

[IMG]http://www.perfectreign.com/stuff/2010/fceux_mario.png[/IMG]


I can't seem to get full screen going, but that is a minor issue. (I'm set at 1680x1050 on a laptop.)

This is a very nice implementation. By comparison, the out of the box 9.1 fceu was choking at 100% utilizaiton. I think I had fceu working on 10.04, but there were so many issues with that I had to reinstall at 9.1.

---

### Post by hanciong on 2010-06-12
hai. I have one problem. I have done all 4 steps to install [B](G)FCEUX 2.0 NES emulator. Now, how to run it?? thanx a lot

got it. turns out I must type fceux in terminal and press enter. sorry guys, i am a newbie in ubuntu
[/B]

---

### Post by punkrockguy318 on 2010-06-26
> **hanciong said:**
> hai. I have one problem. I have done all 4 steps to install [B](G)FCEUX 2.0 NES emulator. Now, how to run it?? thanx a lot

got it. turns out I must type fceux in terminal and press enter. sorry guys, i am a newbie in ubuntu
[/B]

after running scons, fceux in built in ./src/fceux

you can run it via ./src/fceux in your fceux folder

or if you installed it; you can just run "fceux" or "/usr/local/bin/fceux"

are people still having sound issues?

---

### Post by Super Jamie on 2010-07-28
Just wanted to say thankyou so much for all your efforts with this emulator. The interface is way better than fumbling around with the old gfceu and the video options are perfect.

---

### Post by Shaggin Shea on 2010-08-18
> **punkrockguy318 said:**
> after running scons, fceux in built in ./src/fceux

you can run it via ./src/fceux in your fceux folder

or if you installed it; you can just run "fceux" or "/usr/local/bin/fceux"

are people still having sound issues?
I just did a fresh install of ubuntu 10.04 I tried fceu through the ubuntu software center and fceux gfceu. They worked well, sound was good on both (I had troubles in the past which you can find in earlier posts to this thread), fceux couldn't open the controller input.Than I installed using  punkrockguy's howto with scons. Again no sound issues. I want to say good job on how far you have come with fceux. Is there a way to save the controller config or is that something that is coming?

Update
This came up in the terminal:
Initializing video... Video Mode: 512 x 448 x 32 bpp full screen
Loading SDL sound with &#65533;&#65533;&#65533;&#65533; driver...
No available audio device

Update2
The controller config issue seems to have resolved itself on it's own. I haven't been able to reproduce the sound issue so that too has seemed to resolve itself.

---

### Post by mister_playboy on 2010-09-16
> **dbbolton said:**
> Well, sound was working for me in 2.1.2, but after installing 2.1.3, it doesn't (running Debian squeeze)

```
echo $DISPLAY
:0

echo $SDL_AUDIODRIVER
esd
```

I ran
```
esddsp fceux file.rom
```

and got this:
```
Loading SDL sound with  &#65533;&#65533;  driver...
No available audio device
```

Notice the Unicode junk as the name of the driver. It is different every time. Some others that have appeared:
```
@&#65533;&#65533;
&#65533;&#65533;&#65533;
`&#65533;D
`&#65533;

```

I'm having the same problem with 2.1.4a on Kubuntu 10.04. :-k  EDIT: Changing the sound from "esd" to "alsa" fixed the problem. :D

---

### Post by mister_playboy on 2010-09-17
Is there no way to set directory paths with the new GUI?  Having to click through folders for every load/save operation gets old fast.

---

### Post by btncix on 2010-09-23
Sound does not work for me.


I installed only fceux (no gfceu) by following the instructions explained in the first post. My system is 32 bit Ubuntu 10.04. Most of what I tested appear to work great except for sound.

I know that my sound works when I go to youtube.com, but I haven't done anything else to test it. Also, I don't know my system or Linux well enough to know if I should be using some other value for SDL_AUDIODRIVER. I place the export SDL_AUDIODRIVER=esd in my .bashrc file.


Here's my output:
> 
~$ echo $SDL_AUDIODRIVER
esd
~$ fceux --sound 1

Starting FCEUX 2.1.5 debug...
Loading /home/hh/nes/Final Fantasy.nes...

08121b60 PRG ROM:   16 x 16KiB
 CHR ROM:    0 x  8KiB
 ROM CRC32:  0xcebd2a31
 ROM MD5:  0x24ae5edf8375162f91a6846d3202e3d6
 Mapper #:  1
 Mapper name: MMC1
 Mirroring: Horizontal
 Battery-backed: Yes
 Trained: No

Initializing video... Video Mode: 256 x 224 x 32 bpp 
Loading SDL sound with &#65533;&#65533;&#65533;~&#65533;&#65533; driver...
No available audio device

(fceux:2796): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
~$ 
~$ 
~$ uname -a
Linux spock 2.6.32-24-generic-pae #42-Ubuntu SMP Fri Aug 20 15:37:22 UTC 2010 i686 GNU/Linux
~$ 




FYI - I got game genie to work with gg.rom. If I have a couple of questions regarding the cheat code features, can I ask them here or should I create a new thread?

punkrockguy318,
    Thanks for all your work so far with fceux.

---

### Post by btncix on 2010-09-23
UPDATE:

I had another Ubuntu install on another hard drive, so I repeated the install on the second system. Sound worked!

Difference between my two Ubuntu systems: 
**the first Ubuntu system** (sound did NOT work) - this was a bare minimum install with LXDE. I had to install the sound files myself such as alsa-base and alsa-utils
**the second Ubuntu system** (sound WORKED) - this was an Ubuntu Desktop install. I'm guessing that I didn't have something installed or configured in my first system.


I would appreciate any suggestions on how I might be able to figure out what the sound setup differences are between my two systems - is there an apt or dpkg or any other command to see which packages might be missing in my first system compared to my working system. Thanks.

---

### Post by Redmage913 on 2010-10-10
Hello again,

Has the list of required programs changed with the release of Maverick?

Thanks,
--Red

---

### Post by xQB12 on 2010-11-20
your info helped me out alot!!!! Im new to Ubuntu and it can be overwhelming at times, but its cool to find help just clicks away...Thanks again

---

### Post by Zas32x on 2010-12-06
I was unable to build it:
```
g++ -o src/drivers/sdl/sdl.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -Isrc/lua/src -DLUA_USE_LINUX -DHAVE_ASPRINTF -g -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -D_DEBUG -I/usr/include/SDL src/drivers/sdl/sdl.cpp
src/drivers/sdl/sdl.cpp:789: error: expected constructor, destructor, or type conversion before ';' token
src/drivers/sdl/sdl.cpp:792: error: expected constructor, destructor, or type conversion before ';' token
src/drivers/sdl/sdl.cpp:793: error: expected constructor, destructor, or type conversion before ';' token
src/drivers/sdl/sdl.cpp:794: error: expected unqualified-id before 'return'
src/drivers/sdl/sdl.cpp:795: error: expected declaration before '}' token
src/drivers/sdl/config.h:26: warning: 'HotkeyStrings' defined but not used
src/drivers/sdl/sdl-video.h:6: warning: 's_screen' defined but not used
scons: *** [src/drivers/sdl/sdl.o] Error 1
scons: building terminated because of errors.

```

---

### Post by punkrockguy318 on 2011-01-25
> **Zas32x said:**
> I was unable to build it:
```
g++ -o src/drivers/sdl/sdl.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -Isrc/lua/src -DLUA_USE_LINUX -DHAVE_ASPRINTF -g -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DLSB_FIRST -DFRAMESKIP -D_DEBUG -I/usr/include/SDL src/drivers/sdl/sdl.cpp
src/drivers/sdl/sdl.cpp:789: error: expected constructor, destructor, or type conversion before ';' token
src/drivers/sdl/sdl.cpp:792: error: expected constructor, destructor, or type conversion before ';' token
src/drivers/sdl/sdl.cpp:793: error: expected constructor, destructor, or type conversion before ';' token
src/drivers/sdl/sdl.cpp:794: error: expected unqualified-id before 'return'
src/drivers/sdl/sdl.cpp:795: error: expected declaration before '}' token
src/drivers/sdl/config.h:26: warning: 'HotkeyStrings' defined but not used
src/drivers/sdl/sdl-video.h:6: warning: 's_screen' defined but not used
scons: *** [src/drivers/sdl/sdl.o] Error 1
scons: building terminated because of errors.

```

try compiling the most recent svn, it should compile fine now

UPDATE:  Game window is embedded in GUI window!  Grab the latest SVN for testing!

To answer some questions...

Yes, the build deps should be the same for maverick

For those of you with no sound, make sure that libsdl1.2debian-* is installed, where * is the sound system on your system (try pulse, esd, alsa, etc... use whichever works the best on your system!

And any game genie questions can surely be asked in here.  Check the docs as well, as they might be outdated (I may need to update them)

Any feedback on the new GUI would be greatly appreciated !

---

### Post by VortexCortex on 2011-01-26
> **punkrockguy318 said:**
> try compiling the most recent svn, it should compile fine now
...
Any feedback on the new GUI would be greatly appreciated !

First time using FCEUX (long time FCEU user).  Just compiled this on a few x86 Maverick systems (svn rev 2096, Tue, 25 Jan 2011).  Glad to see that sound is working, even on low end specs (1.8ghz, 640mb RAM -- w/ reduced sound Hz).

Love the new GUI, much improved from the GFCE front-end I used previously.  Integrated menu and emulator window is very nice.

I like that the load ROM file dialog remembers the last folder (perhaps "save state as dialog" should remember its last location too? For now I just execute with saves folder as the working dir).

At first I thought it was freezing up when I pressed "select", but then I realized that my chosen select key "\" is mapped to SDL.Hotkeys.FrameAdvance...  No prob, edited the .cfg as mentioned (hint: use "showkey -a" in a virtual terminal (Ctrl+Alt+F1) to get ASCII codes (not scancodes). Use the decimal code -- first number output).

Aside from changing the "open" dialog to a "save" for the "Save State As" file dialog, the only UI I'm missing is a shortcut editor -- resolving double key mapping conflicts manually is a bit tedious.

Great work!  Looking forward to compiling on x64 Maverick when my laptop arrives in a week or so.

---

### Post by jmrank on 2011-01-27
Okay, experts... I was able to get fceux built and installed, and it's working.  Here's my issue: I'd like to be able to script it so I can run it via the command line and go straight to the game, which isn't working.

I don't have gdm running, and would ideally like to be able to run it directly from a terminal.  I'm trying this:

[FONT=Courier New]xinit /usr/local/bin/fceux /roms/nes/<romname>[/FONT]

...which kind of works (this is how I run daphne from tty, with xinit).  It starts X, loads the game, and is reading the config file (fullscreen turned on, custom key assignments are working).  Except... the "empty" fceux window (with the menu options) shows up in front of the game, so you can't see about 1/4 of the screen!  Also, when the game is quit, you still have to "close" the fceux window before it returns to the terminal.

Is it possible to basically have the fceux window never come up?  Load straight into the game and go right back to tty when you quit?  My other option is to use fceu, but then I don't have the config file to custom-map all the keys...

---

### Post by punkrockguy318 on 2011-01-28
> 
Aside from changing the "open" dialog to a "save" for the "Save State As" file dialog, the only UI I'm missing is a shortcut editor -- resolving double key mapping conflicts manually is a bit tedious.

Great work!  Looking forward to compiling on x64 Maverick when my laptop arrives in a week or so.

Just commited 2098.  Does that clean up the dialog issue for you?

And about the shortcut editor.. If there's not already one there, add a bug under the wishlist folder and hopefully me or someone else will eventually get to it.  This would be nice to have.

Thanks for your feedback!  Enjoy fceux :popcorn:

edit: i somehow lost half of my reply here when posting... too late to repost but basically i implemented the dialog remembering folders feature in r2097 check out the latest svn and test :D

---

### Post by punkrockguy318 on 2011-01-28
> **jmrank said:**
> Okay, experts... I was able to get fceux built and installed, and it's working.  Here's my issue: I'd like to be able to script it so I can run it via the command line and go straight to the game, which isn't working.

I don't have gdm running, and would ideally like to be able to run it directly from a terminal.  I'm trying this:

[FONT=Courier New]xinit /usr/local/bin/fceux /roms/nes/<romname>[/FONT]

...which kind of works (this is how I run daphne from tty, with xinit).  It starts X, loads the game, and is reading the config file (fullscreen turned on, custom key assignments are working).  Except... the "empty" fceux window (with the menu options) shows up in front of the game, so you can't see about 1/4 of the screen!  Also, when the game is quit, you still have to "close" the fceux window before it returns to the terminal.

Is it possible to basically have the fceux window never come up?  Load straight into the game and go right back to tty when you quit?  My other option is to use fceu, but then I don't have the config file to custom-map all the keys...
try  r2099

i think i might have solved your issue

if it doesn't; file a bug :D

---

### Post by inukaze on 2011-03-31
Hi there , well , the solution for mi , its very simple
I just "Change the emulator"

I had uninstall , emulators : Meka , Fceu , Nestra , Gens , Fusion , VisualBoyAdvance , VisualBoyAdvance-M , and anothers for this

"Mednafen" , in the repo , we can find a STABLE version , its very INCREDIBLE Multi-Emulator

N.e.s , S.m.s , GameBoys (Original , Pocket & Advance) , PC-Engine , etc

But i Prefer the "WIP" Version

"[Mednafen WIP 0.9.17-WIP]("http://forum.fobby.net/index.php?t=msg&th=630&start=0&")"

This version Support

1 - Nintendo Entertainment System (N.e.s)
2 - SuperNes
3 - Sega Master System
4 - Sega MasterDriver / Genesis
5 - WonderSwan / Color
6 - GameBoy / Original / Pocket / Color / Advance
7 - NeoGeo Pocket , etc ...

And i use too : "[Gelide]("http://gelide.sourceforge.net/")" this program , let me select , emulator , and games i wanna play with simple clicks :=)

well if you wanna use "Filters" or something like that , you should , edit the "mednafen" emulator line , inside the "gelide" , and add something like this "nes.special 2xsai" (to load rom with 2xsai Filter).

Well And the Anothers Emulators & VirtualMachines i use are "Dolphin-Emu" , "Pcsx-r" , "Pcsx2" , "Yabause" . 

ScummVM , DosBox (With this i use "GR-Lida")

Few Softwares to play much Games :=) , now Search , Install & Enjoy your Playing Game :=)

---

### Post by punkrockguy318 on 2011-03-31
> **inukaze said:**
> Hi there , well , the solution for mi , its very simple
I just "Change the emulator"

I had uninstall , emulators : Meka , Fceu , Nestra , Gens , Fusion , VisualBoyAdvance , VisualBoyAdvance-M , and anothers for this

"Mednafen" , in the repo , we can find a STABLE version , its very INCREDIBLE Multi-Emulator

N.e.s , S.m.s , GameBoys (Original , Pocket & Advance) , PC-Engine , etc

But i Prefer the "WIP" Version

"[Mednafen WIP 0.9.17-WIP]("http://forum.fobby.net/index.php?t=msg&th=630&start=0&")"

This version Support

1 - Nintendo Entertainment System (N.e.s)
2 - SuperNes
3 - Sega Master System
4 - Sega MasterDriver / Genesis
5 - WonderSwan / Color
6 - GameBoy / Original / Pocket / Color / Advance
7 - NeoGeo Pocket , etc ...

And i use too : "[Gelide]("http://gelide.sourceforge.net/")" this program , let me select , emulator , and games i wanna play with simple clicks :=)

well if you wanna use "Filters" or something like that , you should , edit the "mednafen" emulator line , inside the "gelide" , and add something like this "nes.special 2xsai" (to load rom with 2xsai Filter).

Well And the Anothers Emulators & VirtualMachines i use are "Dolphin-Emu" , "Pcsx-r" , "Pcsx2" , "Yabause" . 

ScummVM , DosBox (With this i use "GR-Lida")

Few Softwares to play much Games :=) , now Search , Install & Enjoy your Playing Game :=)

Sort of off topic here.  For those who don't know mednefen is a multi-platform emulator.  It uses the (slightly older) core of fceuX for its NES emulation.

Anyway... 2.1.5 is going to be released soon and supports a ton of new features!  A complete GUI overhoul and a ton of bug fixes!  2.1.5 should be out sometime in April, but you can get it now through subversion and enjoy all the new features.

The old steps for compiling svn should still apply.

Enjoy!:popcorn:

---

### Post by iLLNiSS on 2011-04-18
> **punkrockguy318 said:**
> Sort of off topic here.  For those who don't know mednefen is a multi-platform emulator.  It uses the (slightly older) core of fceuX for its NES emulation.

Anyway... 2.1.5 is going to be released soon and supports a ton of new features!  A complete GUI overhoul and a ton of bug fixes!  2.1.5 should be out sometime in April, but you can get it now through subversion and enjoy all the new features.

The old steps for compiling svn should still apply.

Enjoy!:popcorn:

yeah i just checked out 2.1.5 on svn. it runs WAYYY better then mednafen. i get absolutely no screen tears anything for xbmc-live unlike mednafen.

mapping controls was an issue for me. i had to run fceux as root and map my controls. i was then able to run as a regular user and the controls worked fine. there are some bugs i see right off the hop but nothing that cant be worked around except one thing.

when using the --no-gui option in fceux, the gui still shows up after you kill the fceux process. not sure why but its definately broken in my situation.

also, anyone whos having sound issues, apt-get install libsdl1.2debian-alsa (will remove esd).

---

### Post by punkrockguy318 on 2011-04-18
> **iLLNiSS said:**
> yeah i just checked out 2.1.5 on svn. it runs WAYYY better then mednafen. i get absolutely no screen tears anything for xbmc-live unlike mednafen.

mapping controls was an issue for me. i had to run fceux as root and map my controls. i was then able to run as a regular user and the controls worked fine. there are some bugs i see right off the hop but nothing that cant be worked around except one thing.

when using the --no-gui option in fceux, the gui still shows up after you kill the fceux process. not sure why but its definately broken in my situation.

also, anyone whos having sound issues, apt-get install libsdl1.2debian-alsa (will remove esd).

Hello,

Try removing your ~/.fceux/fceux.cfg file as user and see if you can remap your controls ( are you using the GUI on CLI here?) (regarding gamepad options not sticking

The "no-gui" option actually should be "--nogui".  that's a bug and it's been fixed.  Use "--nogui" and it will work fine.

Command-line input parses is broken.  Thanks for discovering this before we released a broken fceux!

thanks for your feedback

---

### Post by iLLNiSS on 2011-04-18
> **punkrockguy318 said:**
> Hello,

Try removing your ~/.fceux/fceux.cfg file as user and see if you can remap your controls ( are you using the GUI on CLI here?) (regarding gamepad options not sticking

The "no-gui" option actually should be "--nogui".  that's a bug and it's been fixed.  Use "--nogui" and it will work fine.

Command-line input parses is broken.  Thanks for discovering this before we released a broken fceux!

thanks for your feedback

yeah i deleted the .fceux folder all together before as i was upgrading from 2.1.2. originally, the .fceux folder was completely locked out from my user (not sure why as it was installed with that user). i couldn't cd into the folder but i could chown it fine. thats unrelated though.

i did try mapping as regular user to begin with from a completely fresh install. 

thanks for the --nogui tip though ill check that out. i really wish the documentation was better with fceux as i've had nothing but issues setting it up relying on the internet and the usually vague/outdated flags specified in the app itself.

---

### Post by amano on 2011-06-25
Is there a precompiled version of FCEUX 2.1.5 for Natty? The one from the oneiric repos doesn't work...

---

### Post by rokrep69 on 2011-06-26
Hi,
I am setting up some emulators in mythgame on mythbuntu 11.04 64 bit. I installed it via synaptic.

FCEUX does work with sound but I am looking for the proper command line to enter into mythgame, for fullscreen and no gui etc.

I messed around and with the --nogui it would lock up, and another time yres and xres switches seemed not work either. Any help is appreciated. And great job dev on the emulator. 

Thanks,
Dan

---

### Post by guyster on 2011-08-09
I am trying to install fceux 2.1.5 on Ubuntu Natty.  I have all the dependencies installed, but am getting a message that build terminated because of errors.  I scrolled the screen up and the error I saw was that asprintf(...) was declared extern and later static.  Is there something I'm doing wrong?  If someone could please help, I would greatly appreciate it, or point me in the direction of a precompiled package.

Thanks for any suggestions,


Guy

---

### Post by punkrockguy318 on 2011-08-09
> **guyster said:**
> I am trying to install fceux 2.1.5 on Ubuntu Natty.  I have all the dependencies installed, but am getting a message that build terminated because of errors.  I scrolled the screen up and the error I saw was that asprintf(...) was declared extern and later static.  Is there something I'm doing wrong?  If someone could please help, I would greatly appreciate it, or point me in the direction of a precompiled package.

Thanks for any suggestions,


Guy

Can you provide the exact error?  I sort of remember that issue cropping up in the past, but I thoguht it was resolved.


> **rokrep69 said:**
> Hi,
I am setting up some emulators in mythgame on mythbuntu 11.04 64 bit. I installed it via synaptic.

FCEUX does work with sound but I am looking for the proper command line to enter into mythgame, for fullscreen and no gui etc.

I messed around and with the --nogui it would lock up, and another time yres and xres switches seemed not work either. Any help is appreciated. And great job dev on the emulator. 

Thanks,
Dan

fceux --nogui 1 --fullscreen 1 doesn't work properly for you?

> Is there a precompiled version of FCEUX 2.1.5 for Natty? The one from the oneiric repos doesn't work...


Not that I know of.  I'm not a Debian/Ubuntu user, so I'm not really sure.  It would be really great if someone wanted to package one. 

Also, if any of you guys need assistance hop in #fceu on Freenode.  Don't expect an immediate response, but someone will get around to assisting you (probably me)

---

### Post by Geraba on 2011-09-10
Hello, I'm trying to compile FCEUX 2.1.5 in Ubuntu 10.10, but there's this error I don't know how to fix...

```
scons: Reading SConscript files ...
platform:  posix
Checking for inflate in C library z... (cached) yes
Checking for C library SDL... (cached) yes
Checking for C library gd... (cached) no
Did not find libgd, you won't be able to create a logo screen for your avis.
Checking for C function asprintf()... (cached) no
Checking for C++ library GL... (cached) yes
base CPPDEFINES: ['PUBLIC_RELEASE', '_GTK2', '_S9XLUA_H', 'PSS_STYLE=1', ['_GNU_SOURCE', '1'], '_REENTRANT', 'LSB_FIRST', 'FRAMESKIP']
base CCFLAGS: ['-Wall', '-Wno-write-strings', '-Wno-sign-compare', '-O2', '-Isrc/lua/src', '-pthread', '-D_GTK', '-DLUA_USE_LINUX', '-DOPENGL']
['$__RPATH', '-pthread']
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/file.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -Isrc/lua/src -pthread -D_GTK -DLUA_USE_LINUX -DOPENGL -DPUBLIC_RELEASE -D_GTK2 -D_S9XLUA_H -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -DLSB_FIRST -DFRAMESKIP -DCREATE_AVI -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/SDL src/file.cpp
src/file.cpp: In function 'void ApplyIPS(FILE*, FCEUFILE*)':
src/file.cpp:134: warning: ignoring return value of 'size_t fread(void*, size_t, size_t, FILE*)', declared with attribute warn_unused_result
src/file.cpp: In function 'int asprintf(char**, const char*, ...)':
src/file.cpp:464: error: 'int asprintf(char**, const char*, ...)' was declared 'extern' and later 'static'
/usr/include/bits/stdio2.h:156: error: previous declaration of 'int asprintf(char**, const char*, ...)'
scons: *** [src/file.o] Error 1
scons: building terminated because of errors.

```It seems some kind of programming error, but as I can't program... How can I fix this? :confused:


EDIT: I just tried to compile version 2.1.4a, and it seemed to work! Looks really like a programming error in 2.1.5...

---

### Post by punkrockguy318 on 2011-09-10
> **Geraba said:**
> Hello, I'm trying to compile FCEUX 2.1.5 in Ubuntu 10.10, but there's this error I don't know how to fix...

```
scons: Reading SConscript files ...
platform:  posix
Checking for inflate in C library z... (cached) yes
Checking for C library SDL... (cached) yes
Checking for C library gd... (cached) no
Did not find libgd, you won't be able to create a logo screen for your avis.
Checking for C function asprintf()... (cached) no
Checking for C++ library GL... (cached) yes
base CPPDEFINES: ['PUBLIC_RELEASE', '_GTK2', '_S9XLUA_H', 'PSS_STYLE=1', ['_GNU_SOURCE', '1'], '_REENTRANT', 'LSB_FIRST', 'FRAMESKIP']
base CCFLAGS: ['-Wall', '-Wno-write-strings', '-Wno-sign-compare', '-O2', '-Isrc/lua/src', '-pthread', '-D_GTK', '-DLUA_USE_LINUX', '-DOPENGL']
['$__RPATH', '-pthread']
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/file.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -Isrc/lua/src -pthread -D_GTK -DLUA_USE_LINUX -DOPENGL -DPUBLIC_RELEASE -D_GTK2 -D_S9XLUA_H -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -DLSB_FIRST -DFRAMESKIP -DCREATE_AVI -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/SDL src/file.cpp
src/file.cpp: In function 'void ApplyIPS(FILE*, FCEUFILE*)':
src/file.cpp:134: warning: ignoring return value of 'size_t fread(void*, size_t, size_t, FILE*)', declared with attribute warn_unused_result
src/file.cpp: In function 'int asprintf(char**, const char*, ...)':
src/file.cpp:464: error: 'int asprintf(char**, const char*, ...)' was declared 'extern' and later 'static'
/usr/include/bits/stdio2.h:156: error: previous declaration of 'int asprintf(char**, const char*, ...)'
scons: *** [src/file.o] Error 1
scons: building terminated because of errors.

```It seems some kind of programming error, but as I can't program... How can I fix this? :confused:


EDIT: I just tried to compile version 2.1.4a, and it seemed to work! Looks really like a programming error in 2.1.5...

can't reproduce with glibc 2.14 and gcc 4.6.1 .  the older versions of glibc and gcc in Ubuntu 10.10 might not be compatible with the latest code; although I'm pretty sure I remember 2.1.5 compiling without issues on 10.10

you might want to try get newer versions of gcc/glibc from -backports

are you able to compile the source from the latest svn?

---

### Post by Eck on 2011-09-15
I got the same errors on Debian Squeeze.  That print thing is provided by gettext so I tried installing more of that, bringing in php5 stuff, as well as trying more libgd stuff.  No go.  And if there's a backport I have it installed, excepting the thing that removes portmap.  I've got 2.6.39, the latest X, etc.

I too just built and installed the previous fceux instead.

---

### Post by punkrockguy318 on 2011-09-15
> **Eck said:**
> I got the same errors on Debian Squeeze.  That print thing is provided by gettext so I tried installing more of that, bringing in php5 stuff, as well as trying more libgd stuff.  No go.  And if there's a backport I have it installed, excepting the thing that removes portmap.  I've got 2.6.39, the latest X, etc.

I too just built and installed the previous fceux instead.

you shouldn't need libgd or php5; i'll see if i can reproduce and fix this on a debian6 box

---

### Post by Eck on 2011-09-15
Yes, and I purged the additional items when seeing they didn't help.  They were the two items mentioned in the errors. Gettext provides that asprint thing so I tried installing more parts of gettext, which brought in php5, and then there was the mention of not finding libgd which I had, but the mini version without X related support.

Got rid of the extras and the just previous fceux built and ran fine.  No mention of either of those items during the build either.

Thanks so much for checking into this.  I don't know if it relates, but for some time now whenever I build wine the configure builds without gettext support because, it says, it is either not installed or too old a version.  That hasn't stopped wine from working just fine though.

---

### Post by punkrockguy318 on 2011-09-15
> **Eck said:**
> Yes, and I purged the additional items when seeing they didn't help.  They were the two items mentioned in the errors. Gettext provides that asprint thing so I tried installing more parts of gettext, which brought in php5, and then there was the mention of not finding libgd which I had, but the mini version without X related support.

Got rid of the extras and the just previous fceux built and ran fine.  No mention of either of those items during the build either.

Thanks so much for checking into this.  I don't know if it relates, but for some time now whenever I build wine the configure builds without gettext support because, it says, it is either not installed or too old a version.  That hasn't stopped wine from working just fine though.

can you try compiling the latest svn source please?

svn co [https://fceultra.svn.sourceforge.net/svnroot/fceultra/fceu](https://fceultra.svn.sourceforge.net/svnroot/fceultra/fceu) fceultra

---

### Post by Eck on 2011-09-16
I just built the latest svn build and although the same reference to not finding libgd was shown, and many more warnings appeared than do in the last release version, it succeeded in building.  

I removed the old /usr/local/bin/fceux and the ~./fceux directory, and then just installed the updated fceux using the command in your readme and install.sh (without the sudo, just as root as this is debian.)  I had installed the previous version using scons install. Is there anything else placed anywhere by scons install besides the binary?  I'd just like to know whether there's old stuff floating about.

I just haven't run it to test as I have dvdshrink encoding now and don't want to chance a processor overload. :)

Was something changed to make the subversion build succeed?  Whatever it is, it builds now so that's good!

Perhaps the release version should be updated shortly?

---

### Post by Eck on 2011-09-16
Well I ran it.  The gamepad config opens up a black screen box and if I hit change in the configurator it blanks out the default option but doesn't replace it.  And the usual "press A press A(twice)" stuff doesn't print out in the black window.  I need to close the emulator to get that button mapping black window to go away.

Um, I think I like the older version better so far eh?  I think I'll delete the executable again and scons install the older one.  Something's amiss on this system with the latest (not building) and the subversion (not working.)

Yep, 2.1.4a works fine.

---

### Post by punkrockguy318 on 2011-09-17
> **Eck said:**
> Well I ran it.  The gamepad config opens up a black screen box and if I hit change in the configurator it blanks out the default option but doesn't replace it.  And the usual "press A press A(twice)" stuff doesn't print out in the black window.  I need to close the emulator to get that button mapping black window to go away.

Um, I think I like the older version better so far eh?  I think I'll delete the executable again and scons install the older one.  Something's amiss on this system with the latest (not building) and the subversion (not working.)

Yep, 2.1.4a works fine.

That extra black window is opening in error in the current SVN, thank you for pointing that out.  However, you should only need to press the key once to set the key.  The black box will not be visible in a commit in the near future, so just ignore it and you can bind your keys.  But yes, subversion is the working codebase so there are kinks here and there especially when maintaining ports for windows, mac osx, and unix.

Add these three lines to the top of the "src/drivers/sdl/SConcript" file in 2.1.5 to see if this resolves the compilation issue for you (I would test myself but I do not have a Debian/Ubuntu box handy):

```

Import('env')
env.ParseConfig('pkg-config --cflags --libs x11')
Export('env')

```

If I recall correctly, that should resolve this issue.  If you could let me know that would be greatly appreciated.  Thanks.

---

### Post by Eck on 2011-09-18
Cool.  I'll build in the morning.  I just pulled a 17 hour workday so I'm just here tonight until I conk out.

The problem I saw in the controller config was not just the black box, but also the different configuration window.  Instead of a press button there is a change button, and hitting that and then a gamepad key just blanked out the listed button instead of changing it as if it knew I pressed something (blanks it) but can't read what I pressed (so no new pad key replaces the blanked out default keypad listed.)

I'll check out building and running 2.1.5 tomorrow, well, later today here.

---

### Post by Eck on 2011-09-19
I tried adding those lines suggested and building.

The same errors regarding that print thing show up as the build fails so that solution had no effect here.

---

### Post by punkrockguy318 on 2011-09-19
> **Eck said:**
> I tried adding those lines suggested and building.

The same errors regarding that print thing show up as the build fails so that solution had no effect here.

can you try with a clean build environment?

as in run "scons -c" before the build to remove any object files

---

### Post by Eck on 2011-09-22
That was a clean build with a freshly extracted source.

---

### Post by punkrockguy318 on 2011-09-22
> **Eck said:**
> That was a clean build with a freshly extracted source.

ill check it out on ubuntu in a vm when i get the chance

---

### Post by punkrockguy318 on 2011-09-25
> **Eck said:**
> I tried adding those lines suggested and building.

The same errors regarding that print thing show up as the build fails so that solution had no effect here.

made some changes to svn; run svn update on your source tree

compiles just fine and works for me on debian6

make sure you have the following packages installed

build-essential libgtk2.0-dev libsdl1.2-dev scons

---

### Post by punkrockguy318 on 2011-10-18
As or revision 2278, fceux now optionally compiles with GTK3.  If you want to compile your binary with GTK3 support, simply adjust the GTK3 option in the SConstruct to "1".  Any feedback and testing would be greatly appreciated!

Report bugs here: [https://sourceforge.net/tracker/?group_id=13536](https://sourceforge.net/tracker/?group_id=13536)

FceuX 2.1.6 coming soon with increased stability, some new features, working netplay, gtk3, and more.

---

### Post by ERamseth on 2011-10-26
Trying to compile latest svn from source. Build-essentials and all stated dependencies are installed. Compile fails as follows:

 
```

 scons: Reading SConscript files ...platform:  posix
Checking for inflate in C library z... (cached) yes
Checking for C library SDL... (cached) yes
Checking for C library gtk-x11-2.0... (cached) yes
Checking for C library lua... (cached) no
Checking for C function asprintf()... (cached) yes
Checking for C++ library GL... (cached) yes
base CPPDEFINES: ['_GTK2', '_S9XLUA_H', 'PSS_STYLE=1', ['_GNU_SOURCE', '1'], '_REENTRANT', 'LSB_FIRS
T', 'FRAMESKIP']
base CCFLAGS: ['-Wall', '-Wno-write-strings', '-Wno-sign-compare', '-Isrc/lua/src', '-pthread', '-D_
GTK', '-DLUA_USE_LINUX', '-DHAVE_ASPRINTF', '-DOPENGL']
['$__RPATH', '-pthread']
scons: done reading SConscript files.
scons: Building targets ...
Copy("bin/auxlib.lua", "src/auxlib.lua")
g++ -o src/asm.o -c -Wall -Wno-write-strings -Wno-sign-compare -Isrc/lua/src -pthread -D_GTK -DLUA_U
SE_LINUX -DHAVE_ASPRINTF -DOPENGL O2 -D_GTK2 -D_S9XLUA_H -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT
-DLSB_FIRST -DFRAMESKIP -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/
usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0 -I/usr/include/glib-2.0 -I/us
r/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/u
sr/include/libpng12 -I/usr/include/SDL src/asm.cpp
g++: O2: No such file or directory
scons: *** [src/asm.o] Error 1
scons: building terminated because of errors. 

``` 

This is on ubuntu 10.04

---

### Post by punkrockguy318 on 2011-10-26
> **ERamseth said:**
> Trying to compile latest svn from source. Build-essentials and all stated dependencies are installed. Compile fails as follows:

 
```

 scons: Reading SConscript files ...platform:  posix
Checking for inflate in C library z... (cached) yes
Checking for C library SDL... (cached) yes
Checking for C library gtk-x11-2.0... (cached) yes
Checking for C library lua... (cached) no
Checking for C function asprintf()... (cached) yes
Checking for C++ library GL... (cached) yes
base CPPDEFINES: ['_GTK2', '_S9XLUA_H', 'PSS_STYLE=1', ['_GNU_SOURCE', '1'], '_REENTRANT', 'LSB_FIRS
T', 'FRAMESKIP']
base CCFLAGS: ['-Wall', '-Wno-write-strings', '-Wno-sign-compare', '-Isrc/lua/src', '-pthread', '-D_
GTK', '-DLUA_USE_LINUX', '-DHAVE_ASPRINTF', '-DOPENGL']
['$__RPATH', '-pthread']
scons: done reading SConscript files.
scons: Building targets ...
Copy("bin/auxlib.lua", "src/auxlib.lua")
g++ -o src/asm.o -c -Wall -Wno-write-strings -Wno-sign-compare -Isrc/lua/src -pthread -D_GTK -DLUA_U
SE_LINUX -DHAVE_ASPRINTF -DOPENGL O2 -D_GTK2 -D_S9XLUA_H -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT
-DLSB_FIRST -DFRAMESKIP -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/
usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0 -I/usr/include/glib-2.0 -I/us
r/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/u
sr/include/libpng12 -I/usr/include/SDL src/asm.cpp
g++: O2: No such file or directory
scons: *** [src/asm.o] Error 1
scons: building terminated because of errors. 

``` 

This is on ubuntu 10.04

Thanks for your report!  This has been fixed in revision2329 so you can svn up and run "scons" again to build.

---

### Post by ERamseth on 2011-10-26
> **punkrockguy318 said:**
> Thanks for your report!  This has been fixed in revision2329 so you can svn up and run "scons" again to build.

thanks.

Also, this isn't fceux specific, but its the only time I've used scons... What's the easiest way to make a deb package? Is there anything like checkinstall?

---

### Post by garybrlow on 2012-05-20
Fcfeux 2.1.5 and 2.1.6 (SVN) gets a Segmentation Fault Error on Ubuntu Precise.  Terminal Output: --------------------------------------------------------- Starting FCEUX 2.1.6 debug... Loading /home/mycomputer/Desktop/Earthbound Zero (Demiforce Hack) (U).nes...   PRG ROM:   16 x 16KiB  CHR ROM:   32 x  8KiB  ROM CRC32:  0x00f0fbbc  ROM MD5:  0xb6d937fe6b101afbfc84bc4084c6f9b9  Mapper #:  4  Mapper name: MMC3  Mirroring: Vertical  Battery-backed: Yes  Trained: No  Power on Initializing video... Video Mode: 512 x 448 x 32 bpp  Loading SDL sound with pulse driver... Segmentation fault (core dumped) ---------------------------------------------------------  Xubuntu 12.04 AM Turion64  Dual Core GeForce FX 7000M   Anyone getting the same error?

---

### Post by BigSilly on 2012-05-20
This isn't helpful in this thread at all, but if you pop over to Ubuntu's PPA page on Launchpad, some lovely soul has packaged and uploaded Nestopia for your delectation and delight. It's a better emu imho, and could be worth a look for you.

---

### Post by punkrockguy318 on 2012-05-20
> **garybrlow said:**
> Fcfeux 2.1.5 and 2.1.6 (SVN) gets a Segmentation Fault Error on Ubuntu Precise.  Terminal Output: --------------------------------------------------------- Starting FCEUX 2.1.6 debug... Loading /home/mycomputer/Desktop/Earthbound Zero (Demiforce Hack) (U).nes...   PRG ROM:   16 x 16KiB  CHR ROM:   32 x  8KiB  ROM CRC32:  0x00f0fbbc  ROM MD5:  0xb6d937fe6b101afbfc84bc4084c6f9b9  Mapper #:  4  Mapper name: MMC3  Mirroring: Vertical  Battery-backed: Yes  Trained: No  Power on Initializing video... Video Mode: 512 x 448 x 32 bpp  Loading SDL sound with pulse driver... Segmentation fault (core dumped) ---------------------------------------------------------  Xubuntu 12.04 AM Turion64  Dual Core GeForce FX 7000M   Anyone getting the same error?

Could you please post an strace and preferably a gdb backtrace of the issue?

You can follow these instructions on how to acquire an strace and gdb backtrace:
[http://wiki.mandriva.com/en/Development/Howto/Software_Crash](http://wiki.mandriva.com/en/Development/Howto/Software_Crash)

the instructions are for another distribution but you should be able to install gdb and strace with "apt-get install strace gdb" and follow the instructions as per usual.

Thank you in advance.

---

### Post by garybrlow on 2012-05-21
gdb output: ------------------------- gdb /usr/local/bin/fceux GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2) 7.4-2012.04 Copyright (C) 2012 Free Software Foundation, Inc. License GPLv3+: GNU GPL version 3 or later  This is free software: you are free to change and redistribute it. There is NO WARRANTY, to the extent permitted by law.  Type "show copying" and "show warranty" for details. This GDB was configured as "i686-linux-gnu". For bug reporting instructions, please see: ... Reading symbols from /usr/local/bin/fceux...done. (gdb) run Starting program: /usr/local/bin/fceux  [Thread debugging using libthread_db enabled] Using host libthread_db library "/lib/i386-linux-gnu/libthread_db.so.1". Starting FCEUX 2.1.6 debug... [New Thread 0xb4cdcb40 (LWP 4174)] [New Thread 0xb44dbb40 (LWP 4175)] [New Thread 0xb3affb40 (LWP 4176)] [New Thread 0xb30ffb40 (LWP 4177)] [Thread 0xb44dbb40 (LWP 4175) exited] Loading /home/mycomputer/Desktop/Earthbound Zero (Demiforce Hack) (U).nes.zip...   PRG ROM:   16 x 16KiB  CHR ROM:   32 x  8KiB  ROM CRC32:  0x00f0fbbc  ROM MD5:  0xb6d937fe6b101afbfc84bc4084c6f9b9  Mapper #:  4  Mapper name: MMC3  Mirroring: Vertical  Battery-backed: Yes  Trained: No  Power on Initializing video... Video Mode: 512 x 448 x 32 bpp  [New Thread 0xb44dbb40 (LWP 4178)] Loading SDL sound with pulse driver... [Thread 0xb44dbb40 (LWP 4178) exited] [New Thread 0xb44dbb40 (LWP 4179)] [Thread 0xb4cdcb40 (LWP 4174) exited] [New Thread 0xb4cdcb40 (LWP 4204)] [New Thread 0xae6feb40 (LWP 4205)] [New Thread 0xadefdb40 (LWP 4206)] [Thread 0xb4cdcb40 (LWP 4204) exited] [Thread 0xae6feb40 (LWP 4205) exited] [New Thread 0xae6feb40 (LWP 4207)] [Thread 0xadefdb40 (LWP 4206) exited] [New Thread 0xadefdb40 (LWP 4208)] [New Thread 0xb4cdcb40 (LWP 4209)] [New Thread 0xad64cb40 (LWP 4210)] [New Thread 0xace4bb40 (LWP 4211)] [Thread 0xb4cdcb40 (LWP 4209) exited] [Thread 0xad64cb40 (LWP 4210) exited] [Thread 0xace4bb40 (LWP 4211) exited] [Thread 0xae6feb40 (LWP 4207) exited] [New Thread 0xae6feb40 (LWP 4212)] [Thread 0xadefdb40 (LWP 4208) exited] [New Thread 0xadefdb40 (LWP 4213)] [Thread 0xadefdb40 (LWP 4213) exited] [Thread 0xae6feb40 (LWP 4212) exited] [New Thread 0xae6feb40 (LWP 4214)] [Thread 0xae6feb40 (LWP 4214) exited] [New Thread 0xae6feb40 (LWP 4216)] [New Thread 0xadefdb40 (LWP 4217)] [New Thread 0xace4bb40 (LWP 4218)] [New Thread 0xad64cb40 (LWP 4219)] [New Thread 0xb4cdcb40 (LWP 4220)] [Thread 0xae6feb40 (LWP 4216) exited] [Thread 0xadefdb40 (LWP 4217) exited] [Thread 0xb4cdcb40 (LWP 4220) exited] [Thread 0xad64cb40 (LWP 4219) exited] [New Thread 0xad64cb40 (LWP 4221)] [Thread 0xace4bb40 (LWP 4218) exited] [New Thread 0xace4bb40 (LWP 4222)] [New Thread 0xb4cdcb40 (LWP 4223)] [Thread 0xb4cdcb40 (LWP 4223) exited] [Thread 0xad64cb40 (LWP 4221) exited] [New Thread 0xad64cb40 (LWP 4224)] [New Thread 0xb4cdcb40 (LWP 4225)] [New Thread 0xadefdb40 (LWP 4226)] [New Thread 0xae6feb40 (LWP 4227)] [Thread 0xad64cb40 (LWP 4224) exited] [Thread 0xb4cdcb40 (LWP 4225) exited] [Thread 0xadefdb40 (LWP 4226) exited] [Thread 0xace4bb40 (LWP 4222) exited] [Thread 0xb44dbb40 (LWP 4179) exited] [Thread 0xae6feb40 (LWP 4227) exited] [Thread 0xb30ffb40 (LWP 4177) exited] [Thread 0xb3affb40 (LWP 4176) exited] [Inferior 1 (process 4171) exited normally] -------------------------  It's bizzare actually, fceux runs without problems within gdb. The normal run of fceux causes a segmentation error after a few seconds.

---

### Post by punkrockguy318 on 2012-05-21
> **garybrlow said:**
> gdb output: ------------------------- gdb /usr/local/bin/fceux GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2) 7.4-2012.04 Copyright (C) 2012 Free Software Foundation, Inc. License GPLv3+: GNU GPL version 3 or later  This is free software: you are free to change and redistribute it. There is NO WARRANTY, to the extent permitted by law.  Type "show copying" and "show warranty" for details. This GDB was configured as "i686-linux-gnu". For bug reporting instructions, please see: ... Reading symbols from /usr/local/bin/fceux...done. (gdb) run Starting program: /usr/local/bin/fceux  [Thread debugging using libthread_db enabled] Using host libthread_db library "/lib/i386-linux-gnu/libthread_db.so.1". Starting FCEUX 2.1.6 debug... [New Thread 0xb4cdcb40 (LWP 4174)] [New Thread 0xb44dbb40 (LWP 4175)] [New Thread 0xb3affb40 (LWP 4176)] [New Thread 0xb30ffb40 (LWP 4177)] [Thread 0xb44dbb40 (LWP 4175) exited] Loading /home/mycomputer/Desktop/Earthbound Zero (Demiforce Hack) (U).nes.zip...   PRG ROM:   16 x 16KiB  CHR ROM:   32 x  8KiB  ROM CRC32:  0x00f0fbbc  ROM MD5:  0xb6d937fe6b101afbfc84bc4084c6f9b9  Mapper #:  4  Mapper name: MMC3  Mirroring: Vertical  Battery-backed: Yes  Trained: No  Power on Initializing video... Video Mode: 512 x 448 x 32 bpp  [New Thread 0xb44dbb40 (LWP 4178)] Loading SDL sound with pulse driver... [Thread 0xb44dbb40 (LWP 4178) exited] [New Thread 0xb44dbb40 (LWP 4179)] [Thread 0xb4cdcb40 (LWP 4174) exited] [New Thread 0xb4cdcb40 (LWP 4204)] [New Thread 0xae6feb40 (LWP 4205)] [New Thread 0xadefdb40 (LWP 4206)] [Thread 0xb4cdcb40 (LWP 4204) exited] [Thread 0xae6feb40 (LWP 4205) exited] [New Thread 0xae6feb40 (LWP 4207)] [Thread 0xadefdb40 (LWP 4206) exited] [New Thread 0xadefdb40 (LWP 4208)] [New Thread 0xb4cdcb40 (LWP 4209)] [New Thread 0xad64cb40 (LWP 4210)] [New Thread 0xace4bb40 (LWP 4211)] [Thread 0xb4cdcb40 (LWP 4209) exited] [Thread 0xad64cb40 (LWP 4210) exited] [Thread 0xace4bb40 (LWP 4211) exited] [Thread 0xae6feb40 (LWP 4207) exited] [New Thread 0xae6feb40 (LWP 4212)] [Thread 0xadefdb40 (LWP 4208) exited] [New Thread 0xadefdb40 (LWP 4213)] [Thread 0xadefdb40 (LWP 4213) exited] [Thread 0xae6feb40 (LWP 4212) exited] [New Thread 0xae6feb40 (LWP 4214)] [Thread 0xae6feb40 (LWP 4214) exited] [New Thread 0xae6feb40 (LWP 4216)] [New Thread 0xadefdb40 (LWP 4217)] [New Thread 0xace4bb40 (LWP 4218)] [New Thread 0xad64cb40 (LWP 4219)] [New Thread 0xb4cdcb40 (LWP 4220)] [Thread 0xae6feb40 (LWP 4216) exited] [Thread 0xadefdb40 (LWP 4217) exited] [Thread 0xb4cdcb40 (LWP 4220) exited] [Thread 0xad64cb40 (LWP 4219) exited] [New Thread 0xad64cb40 (LWP 4221)] [Thread 0xace4bb40 (LWP 4218) exited] [New Thread 0xace4bb40 (LWP 4222)] [New Thread 0xb4cdcb40 (LWP 4223)] [Thread 0xb4cdcb40 (LWP 4223) exited] [Thread 0xad64cb40 (LWP 4221) exited] [New Thread 0xad64cb40 (LWP 4224)] [New Thread 0xb4cdcb40 (LWP 4225)] [New Thread 0xadefdb40 (LWP 4226)] [New Thread 0xae6feb40 (LWP 4227)] [Thread 0xad64cb40 (LWP 4224) exited] [Thread 0xb4cdcb40 (LWP 4225) exited] [Thread 0xadefdb40 (LWP 4226) exited] [Thread 0xace4bb40 (LWP 4222) exited] [Thread 0xb44dbb40 (LWP 4179) exited] [Thread 0xae6feb40 (LWP 4227) exited] [Thread 0xb30ffb40 (LWP 4177) exited] [Thread 0xb3affb40 (LWP 4176) exited] [Inferior 1 (process 4171) exited normally] -------------------------  It's bizzare actually, fceux runs without problems within gdb. The normal run of fceux causes a segmentation error after a few seconds.

Thank you for your report.  I have received a similar bug report of this nature (fceux segfaulting in 12.04, but not within gdb).  I will spin up 12.04 on one of my boxen and see if I can reproduce.

Thank you for your feedback!

---

### Post by punkrockguy318 on 2012-05-26
> **punkrockguy318 said:**
> Thank you for your report.  I have received a similar bug report of this nature (fceux segfaulting in 12.04, but not within gdb).  I will spin up 12.04 on one of my boxen and see if I can reproduce.

Thank you for your feedback!

What video card/driver are you using when you get a crash on 12.04?  I'm unable to reproduce the crash on my system in VirtualBox.  Is OpenGL enabled?

---

### Post by garybrlow on 2012-05-27
GeForce FX 7000M

---

### Post by garybrlow on 2012-05-27
Am actually running the windows version of fceux using wine. It works fine though not as perfect as the native version.

---

### Post by punkrockguy318 on 2012-05-27
> **garybrlow said:**
> GeForce FX 7000M

what driver are you using?

---

### Post by garybrlow on 2012-05-27
295.40 w/ official ubuntu patches  for the regression issues with old cards all from repo.

---

### Post by punkrockguy318 on 2012-05-29
> **garybrlow said:**
> 295.40 w/ official ubuntu patches  for the regression issues with old cards all from repo.

can you reproduce with and without openGL?

---

### Post by punkrockguy318 on 2012-05-30
> **garybrlow said:**
> 295.40 w/ official ubuntu patches  for the regression issues with old cards all from repo.

i couldn't reproduce on ubuntu 12.04 on virtualbox or on intel drivers.  in regards to nvidia -- i can not reproduce on 295.53, 295.40 or 302.11 with arch linux.  the issue sounds like a driver related issue and not a fceux related issue and without a backtrace and without being able to reproduce the issue i'm not really able to diagnose the issue.  i would say try running with and without opengl to see if you can work around the probable driver issue

---

### Post by garybrlow on 2012-06-01
There is no error/segmentation fault if the driver is turned off/removed.

---

### Post by punkrockguy318 on 2012-06-02
> **garybrlow said:**
> There is no error/segmentation fault if the driver is turned off/removed.

I would suggest disabling openGL when using the nvidia drivers in Ubuntu 12.04.  I'm unable to reproduce this with Ubuntu on intel drivers or in Virtualbox nor with the latest nvidia drivers on Arch Linux

---

### Post by punkrockguy318 on 2012-06-19
the subversion url is: svn checkout [http://svn.code.sf.net/p/fceultra/code/fceu](http://svn.code.sf.net/p/fceultra/code/fceu) fceultra-code

this can be seen from the "code" section of the fceultra project page: [http://sourceforge.net/p/fceultra/code/](http://sourceforge.net/p/fceultra/code/)

i wanted to post this and confirm this because the url has changed -- sourceforge has upgraded their software stack and the fceux svn url has changed in the process.  you WILL need to recheck out fceux with the new URL to get the latest code.

---

### Post by someotheruser on 2012-06-24
Just built FCEUX '2.1.6 debug' (i386) from the link above.  Seems to work better than my previous install (2.1.0).  Only problem I seem to have is when I click on something under Options, it crashes and I get the following error:
```

./fceux: symbol lookup error: ./fceux: undefined symbol: gtk_combo_box_text_new

```

---

### Post by punkrockguy318 on 2012-06-24
> **someotheruser said:**
> Just built FCEUX '2.1.6 debug' (i386) from the link above.  Seems to work better than my previous install (2.1.0).  Only problem I seem to have is when I click on something under Options, it crashes and I get the following error:
```

./fceux: symbol lookup error: ./fceux: undefined symbol: gtk_combo_box_text_new

```

That dialog in 2.1.6 requires GTK 2.24.  Sounds like you are using Ubuntu 10.04, correct?  Ubuntu 10.04 includes GTK 2.20.  The reasoning for this so that the codebase could be compiled with either GTK2 or GTK3.  As a workaround, you can use "--inputcfg" from the command line:

    fceux --inputcfg gamepad1

That dialog should work without issues on any more recent versions of Ubuntu (at least natty).  I've just now added some code in subversion (r2542) that hides the "gamepad config" option on older versions of GTK, preventing a frustrating crash in the middle of a (unsaved) emulation session.

Let me know how you make out with the most recent revision.  FYI the subversion repo has officially changed, please use the repo as described on the sourceforge page:

[https://sourceforge.net/p/fceultra/code/](https://sourceforge.net/p/fceultra/code/)

If you run into further issues let me know; I'm trying to get as many bugs ironed out before the 2.1.6 release as possible

---

### Post by someotheruser on 2012-06-24
Actually I'm using Debian unstable.

These are my GTK2 related packages
```

$ dpkg-query --list | grep 'gtk2'
ii  gtk2-engines-oxygen:amd64                    1.2.4-1                            Oxygen widget theme for GTK+-based applications
ii  gtk2-engines-pixbuf:amd64                    2.24.10-1                          pixbuf-based theme for GTK+ 2.x
ii  gtk2-engines-qtcurve                         1.8.15-1                           This is a set of widget styles for Gtk2 based apps
ii  gtk2-ex-formfactory-perl                     0.67-0.0                           Makes building complex GUI's easy
ii  libgtk2-gladexml-perl                        1.007-1+b2                         Perl interface to use user interfaces created with glade-2
ii  libgtk2-perl                                 2:1.244-1                          Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0:amd64                            2.24.10-1                          GTK+ graphical user interface library
ii  libgtk2.0-bin                                2.24.10-1                          programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                                2.12.10-4                          CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                             2.24.10-1                          common files for the GTK+ graphical user interface library
ii  libwxgtk2.6-0                                2.6.3.2.2-6                        wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
ii  libwxgtk2.8-0:amd64                          2.8.12.1-11                        wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
ii  python-gtk2                                  2.24.0-3                           Python bindings for the GTK+ widget set
ii  python-wxgtk2.8                              2.8.12.1-11                        wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)
ii  ruby-gtk2                                    1.1.3-2                            GTK+ bindings for the Ruby language

```

---

### Post by punkrockguy318 on 2012-06-24
> **garybrlow said:**
> There is no error/segmentation fault if the driver is turned off/removed.

this issue has been resolved in revision2539.  thank you for your report!

---

### Post by punkrockguy318 on 2012-06-24
> **someotheruser said:**
> Actually I'm using Debian unstable.

These are my GTK2 related packages
```

$ dpkg-query --list | grep 'gtk2'
ii  gtk2-engines-oxygen:amd64                    1.2.4-1                            Oxygen widget theme for GTK+-based applications
ii  gtk2-engines-pixbuf:amd64                    2.24.10-1                          pixbuf-based theme for GTK+ 2.x
ii  gtk2-engines-qtcurve                         1.8.15-1                           This is a set of widget styles for Gtk2 based apps
ii  gtk2-ex-formfactory-perl                     0.67-0.0                           Makes building complex GUI's easy
ii  libgtk2-gladexml-perl                        1.007-1+b2                         Perl interface to use user interfaces created with glade-2
ii  libgtk2-perl                                 2:1.244-1                          Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0:amd64                            2.24.10-1                          GTK+ graphical user interface library
ii  libgtk2.0-bin                                2.24.10-1                          programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                                2.12.10-4                          CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                             2.24.10-1                          common files for the GTK+ graphical user interface library
ii  libwxgtk2.6-0                                2.6.3.2.2-6                        wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
ii  libwxgtk2.8-0:amd64                          2.8.12.1-11                        wxWidgets Cross-platform C++ GUI toolkit (GTK+ runtime)
ii  python-gtk2                                  2.24.0-3                           Python bindings for the GTK+ widget set
ii  python-wxgtk2.8                              2.8.12.1-11                        wxWidgets Cross-platform C++ GUI toolkit (wxPython binding)
ii  ruby-gtk2                                    1.1.3-2                            GTK+ bindings for the Ruby language

```
Interesting... That shouldn't happen.  I'll installing sid in a VM and see if I'm able to reproduce.

---

### Post by VonSpyder on 2012-10-29
Options menu has NO options at all, how the heck do i configure input?

---

### Post by punkrockguy318 on 2012-11-01
> **VonSpyder said:**
> Options menu has NO options at all, how the heck do i configure input?

Strange.  What version of fceux and Ubuntu?

---

### Post by outrosdiasvirao on 2012-11-20
I needed also (before proceed with the install) to install dependencies for lua:

```

apt-get install liblua5.1-0-dev liblua50-dev liblualib50-dev

```I needed to remove my previous fceultra directory, and get a new copy from svn.

Thanks.


> **punkrockguy318 said:**
> These steps should work to install the latest version of the FCE UltraX (FCEUX) NES/Famicom emulator in Ubuntu.

1.  Install necessary dependencies. 

```

sudo apt-get install scons libsdl1.2-dev subversion libgtk2.0-dev

```2.  Open a terminal (Applications... Accessories... Terminal) and obtain source from subversion.
```

svn checkout http://svn.code.sf.net/p/fceultra/code/fceu fceultra

```3. Change directory into the fceultra folder.

```
cd fceultra/
```4.  Build and install fceux.

```
sudo scons install
```And that's it!  You can also grab an older version of fceux from the Ubuntu repositories, but the latest and greatest can be obtained and compiled from subversion.

If you would like to contribute, or run into any issues, feel free to join us in #fceu on irc.freenode.com.  You can also file bugs to our tracker ([http://sourceforge.net/p/fceultra/bugs/](http://sourceforge.net/p/fceultra/bugs/)).  Please note that you may not receive an immediate response in IRC -- idling is key.

Enjoy!

---

### Post by TheUniversalRemonster on 2012-12-26
Hey, sorry to gum up this thread with more troubleshooting, but I've scoured the internet to the best of my abilities and can't get anywhere.  I'm new to both fceux and linux (running Raspbian on a Raspberry Pi). I have compiled and installed FCEUX 2.2.  If I try to run from command line I get a GTK warning.  When I run in GUI, the program launches a black screen. I File>Open> choose my rom, and nothing happens.

In order to verify, on my Windows PC I installed FCEUX 2.2 and ran then exact same rom and it worked.  I am at a loss as to what I'm doing wrong. Any and all guidance would be appreciated! Thanks!

---

### Post by punkrockguy318 on 2012-12-26
> **TheUniversalRemonster said:**
> Hey, sorry to gum up this thread with more troubleshooting, but I've scoured the internet to the best of my abilities and can't get anywhere.  I'm new to both fceux and linux (running Raspbian on a Raspberry Pi). I have compiled and installed FCEUX 2.2.  If I try to run from command line I get a GTK warning.  When I run in GUI, the program launches a black screen. I File>Open> choose my rom, and nothing happens.

In order to verify, on my Windows PC I installed FCEUX 2.2 and ran then exact same rom and it worked.  I am at a loss as to what I'm doing wrong. Any and all guidance would be appreciated! Thanks!

If you are running on the RaspPI, you may want to try disabling OpenGL.  Can you be a little more specific about the error messages you are receiving?

---

### Post by TheUniversalRemonster on 2012-12-26
> **punkrockguy318 said:**
> If you are running on the RaspPI, you may want to try disabling OpenGL.  Can you be a little more specific about the error messages you are receiving?

When trying to run from Command Line I get:

(Fceux:12980): Gtk-WARNING **: cannot open display:

I tried searching that error but the responses didn't seem to have anything to do with Fceux. Thanks for your help.

EDIT: I checked, open GL is disabled in fceux options.

---

### Post by punkrockguy318 on 2012-12-26
> **TheUniversalRemonster said:**
> When trying to run from Command Line I get:

(Fceux:12980): Gtk-WARNING **: cannot open display:

I tried searching that error but the responses didn't seem to have anything to do with Fceux. Thanks for your help.

That message would indicate that the tty session that you are invoking fceux from is not able to access the X11 server.  Are you running this as root or from within a screen/tmux session?  You will likely be unable to run any other X11 applications from that tty session.  Try running it from the X session directly and let me know what error message you are receiving -- the above error message is not an issue with fceux itself

---

### Post by TheUniversalRemonster on 2012-12-26
> **punkrockguy318 said:**
> That message would indicate that the tty session that you are invoking fceux from is not able to access the X11 server.  Are you running this as root or from within a screen/tmux session?  You will likely be unable to run any other X11 applications from that tty session.  Try running it from the X session directly and let me know what error message you are receiving -- the above error message is not an issue with fceux itself

Ok, I need to emphasize again that I am new at this, so some of those terms are lost on me. When I say I'm running from Command Line, I guess technically I mean I'm running from shell (no graphical interface at all, just the prompt). I am running the program as user. I just tried running it again as root and it gave me the same warning but with a different number (13097).

If I try to run FCEUX from the desktop (is that what you mean by screen session?), as in, double click the FCEUX icon, the program opens, but roms will not load.

Thanks for the clarification, I'll do some more research on that X11 server business.

---

### Post by punkrockguy318 on 2012-12-26
> **TheUniversalRemonster said:**
> Ok, I need to emphasize again that I am new at this, so some of those terms are lost on me. When I say I'm running from Command Line, I guess technically I mean I'm running from shell (no graphical interface at all, just the prompt). I am running the program as user. I just tried running it again as root and it gave me the same warning but with a different number (13097).

If I try to run FCEUX from the desktop (is that what you mean by screen session?), as in, double click the FCEUX icon, the program opens, but roms will not load.

Thanks for the clarification, I'll do some more research on that X11 server business.

What's the error message you get when attempting to load a ROM from the GUI?

---

### Post by TheUniversalRemonster on 2012-12-26
> **punkrockguy318 said:**
> What's the error message you get when attempting to load a ROM from the GUI?

That's the frustrating part, there is no error message. Unless there's some kind of log that I'm not seeing. The fceux window just remains blank. That's why I tested the rom on my PC to make sure that wasn't the problem.

---

### Post by petran79 on 2013-02-17
hallo, I get the following error when trying to compile from svn (2526) using scons.
I have all necessary libraries installed on Ubuntu 12.04 64-bit

scons: Reading SConscript files ...
platform:  posix
Checking for inflate in C library z... (cached) yes
Checking for C library SDL... (cached) yes
Checking for C library gtk-x11-2.0... (cached) yes
Checking for C library lua... (cached) no
Checking for C library gd... (cached) no
Did not find libgd, you won't be able to create a logo screen for your avis.
Checking for C function asprintf()... (cached) yes
Checking for C++ library GL... (cached) yes
base CPPDEFINES: ['_GTK2', '_S9XLUA_H', 'PSS_STYLE=1', ['_GNU_SOURCE', '1'], '_REENTRANT', 'LSB_FIRST', 'FRAMESKIP']
base CCFLAGS: ['-Wall', '-Wno-write-strings', '-Wno-sign-compare', '-Isrc/lua/src', '-pthread', '-D_GTK', '-DLUA_USE_LINUX', '-DHAVE_ASPRINTF', '-DOPENGL']
['-pthread']
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/drivers/sdl/input.o -c -Wall -Wno-write-strings -Wno-sign-compare -Isrc/lua/src -pthread -D_GTK -DLUA_USE_LINUX -DHAVE_ASPRINTF -DOPENGL -g -D_GTK2 -D_S9XLUA_H -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -DLSB_FIRST -DFRAMESKIP -D_DEBUG -DCREATE_AVI -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/SDL src/drivers/sdl/input.cpp
src/drivers/sdl/input.cpp: In function 'void KeyboardCommands()':
src/drivers/sdl/input.cpp:562:9: error: 'string' does not name a type
src/drivers/sdl/input.cpp:563:49: error: 'movie_fname' was not declared in this scope
src/drivers/sdl/input.cpp: In function 'void GetMouseData(uint32 (&)[3])':
src/drivers/sdl/input.cpp:879:13: warning: unused variable 'event' [-Wunused-variable]
src/drivers/sdl/input.cpp: In function 'void ButtonConfigEnd()':
src/drivers/sdl/input.cpp:1033:18: warning: unused variable 'GameInfo' [-Wunused-variable]
src/drivers/sdl/sdl-video.h: At global scope:
src/drivers/sdl/sdl-video.h:6:21: warning: 's_screen' defined but not used [-Wunused-variable]
src/drivers/sdl/sdl.h:9:13: warning: 'void DoFun(int)' declared 'static' but never defined [-Wunused-function]
src/drivers/sdl/sdl.h:10:12: warning: 'isloaded' defined but not used [-Wunused-variable]
scons: *** [src/drivers/sdl/input.o] Error 1
scons: building terminated because of errors.

---

### Post by punkrockguy318 on 2013-02-17
> **petran79 said:**
> hallo, I get the following error when trying to compile from svn (2526) using scons.
I have all necessary libraries installed on Ubuntu 12.04 64-bit

scons: Reading SConscript files ...
platform:  posix
Checking for inflate in C library z... (cached) yes
Checking for C library SDL... (cached) yes
Checking for C library gtk-x11-2.0... (cached) yes
Checking for C library lua... (cached) no
Checking for C library gd... (cached) no
Did not find libgd, you won't be able to create a logo screen for your avis.
Checking for C function asprintf()... (cached) yes
Checking for C++ library GL... (cached) yes
base CPPDEFINES: ['_GTK2', '_S9XLUA_H', 'PSS_STYLE=1', ['_GNU_SOURCE', '1'], '_REENTRANT', 'LSB_FIRST', 'FRAMESKIP']
base CCFLAGS: ['-Wall', '-Wno-write-strings', '-Wno-sign-compare', '-Isrc/lua/src', '-pthread', '-D_GTK', '-DLUA_USE_LINUX', '-DHAVE_ASPRINTF', '-DOPENGL']
['-pthread']
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/drivers/sdl/input.o -c -Wall -Wno-write-strings -Wno-sign-compare -Isrc/lua/src -pthread -D_GTK -DLUA_USE_LINUX -DHAVE_ASPRINTF -DOPENGL -g -D_GTK2 -D_S9XLUA_H -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -DLSB_FIRST -DFRAMESKIP -D_DEBUG -DCREATE_AVI -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/SDL src/drivers/sdl/input.cpp
src/drivers/sdl/input.cpp: In function 'void KeyboardCommands()':
src/drivers/sdl/input.cpp:562:9: error: 'string' does not name a type
src/drivers/sdl/input.cpp:563:49: error: 'movie_fname' was not declared in this scope
src/drivers/sdl/input.cpp: In function 'void GetMouseData(uint32 (&)[3])':
src/drivers/sdl/input.cpp:879:13: warning: unused variable 'event' [-Wunused-variable]
src/drivers/sdl/input.cpp: In function 'void ButtonConfigEnd()':
src/drivers/sdl/input.cpp:1033:18: warning: unused variable 'GameInfo' [-Wunused-variable]
src/drivers/sdl/sdl-video.h: At global scope:
src/drivers/sdl/sdl-video.h:6:21: warning: 's_screen' defined but not used [-Wunused-variable]
src/drivers/sdl/sdl.h:9:13: warning: 'void DoFun(int)' declared 'static' but never defined [-Wunused-function]
src/drivers/sdl/sdl.h:10:12: warning: 'isloaded' defined but not used [-Wunused-variable]
scons: *** [src/drivers/sdl/input.o] Error 1
scons: building terminated because of errors.

You'll want to ensure that you are building with the latest subversion code.  I am unable to reproduce this issue with the latest source on 64 bit linux.  At the time of posting, the latest revision is revision 2834, so you will want to "svn update" to the latest version.

---

### Post by petran79 on 2013-02-22
ok I updated to the latest revision (2835), but while building got the following error:

g++ -o src/drivers/sdl/sdl-opengl.o -c -Wall -Wno-write-strings -Wno-sign-compare -Isrc/lua/src -DHAVE_ASPRINTF -pthread -D_GTK -DLUA_USE_LINUX -DOPENGL -g -D_GTK2 -D_S9XLUA_H -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -DLSB_FIRST -DFRAMESKIP -D_DEBUG -DCREATE_AVI -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/SDL src/drivers/sdl/sdl-opengl.cpp
src/drivers/sdl/sdl.h:9:13: warning: 'void DoFun(int)' declared 'static' but never defined [-Wunused-function]
src/drivers/sdl/sdl.h:10:12: warning: 'isloaded' defined but not used [-Wunused-variable]
scons: *** [src/fceux] Implicit dependency `/usr/lib/x86_64-linux-gnu/libGL.so' not found, needed by target `src/fceux'.
scons: building terminated because of errors.


this libgl error was also in previous versions. 
probably due to this. problem is I need those drivers because closed source Nvidia solves some issues with video playback.
[http://sourceforge.net/mailarchive/message.php?msg_id=29448314](http://sourceforge.net/mailarchive/message.php?msg_id=29448314)

---

### Post by punkrockguy318 on 2013-02-22
> **petran79 said:**
> ok I updated to the latest revision (2835), but while building got the following error:

g++ -o src/drivers/sdl/sdl-opengl.o -c -Wall -Wno-write-strings -Wno-sign-compare -Isrc/lua/src -DHAVE_ASPRINTF -pthread -D_GTK -DLUA_USE_LINUX -DOPENGL -g -D_GTK2 -D_S9XLUA_H -DPSS_STYLE=1 -D_GNU_SOURCE=1 -D_REENTRANT -DLSB_FIRST -DFRAMESKIP -D_DEBUG -DCREATE_AVI -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/SDL src/drivers/sdl/sdl-opengl.cpp
src/drivers/sdl/sdl.h:9:13: warning: 'void DoFun(int)' declared 'static' but never defined [-Wunused-function]
src/drivers/sdl/sdl.h:10:12: warning: 'isloaded' defined but not used [-Wunused-variable]
scons: *** [src/fceux] Implicit dependency `/usr/lib/x86_64-linux-gnu/libGL.so' not found, needed by target `src/fceux'.
scons: building terminated because of errors.


this libgl error was also in previous versions. 
probably due to this. problem is I need those drivers because closed source Nvidia solves some issues with video playback.
[http://sourceforge.net/mailarchive/message.php?msg_id=29448314](http://sourceforge.net/mailarchive/message.php?msg_id=29448314)

You need to have libGL on your system.  If you have installed the nvidia proprietary drivers, you should already have this on your system.  If not, you may need to install mesa to supply libGL

The issue that you have linked has already been resolved and is not relevant to the issue you are experiencing.

---

### Post by petran79 on 2013-02-23
> **punkrockguy318 said:**
> You need to have libGL on your system.  If you have installed the nvidia proprietary drivers, you should already have this on your system.  If not, you may need to install mesa to supply libGL

The issue that you have linked has already been resolved and is not relevant to the issue you are experiencing.

since I already have both the latest version of Nvidia and mesa, yet still get this error, it hasnt been resolved yet,

---

### Post by punkrockguy318 on 2013-02-23
> **petran79 said:**
> since I already have both the latest version of Nvidia and mesa, yet still get this error, it hasnt been resolved yet,


the error you are receiving is a completely different error than what you referenced from the mailing list.  you need to have libgl on your system. ive compiled and run latest svn across multiple versions of ubuntu with nvidia drivers. make sure you have all the proper dependencies (apt-get build-dep fceux might help)

---

### Post by petran79 on 2013-02-24
> **punkrockguy318 said:**
> the error you are receiving is a completely different error than what you referenced from the mailing list.  you need to have libgl on your system. ive compiled and run latest svn across multiple versions of ubuntu with nvidia drivers. make sure you have all the proper dependencies (apt-get build-dep fceux might help)

does it matter whether they are open or closed source drivers? I have the closed source ones and perhaps this might be the problem, as seen in the article I linked. 

because other OpenGL applications and emulators work without issues.

---

### Post by punkrockguy318 on 2013-02-24
> **petran79 said:**
> does it matter whether they are open or closed source drivers? I have the closed source ones and perhaps this might be the problem, as seen in the article I linked. 

because other OpenGL applications and emulators work without issues.

The problem noted in the article (mailing list) that you linked has since been resolved if you are using the latest version of fceux.  what version of ubuntu are you running?  you need to make sure that you have all the dependencies as well as the "-dev" package of the dependencies installed on your system

---

### Post by petran79 on 2013-03-02
> **punkrockguy318 said:**
> The problem noted in the article (mailing list) that you linked has since been resolved if you are using the latest version of fceux.  what version of ubuntu are you running?  you need to make sure that you have all the dependencies as well as the "-dev" package of the dependencies installed on your system

problem solved finally!

after upgrading to the latest kernel (Ubuntu 12.04 3.2.0.39), suddenly Compiz effects werent working.

had to install Nvidia drivers again this time from terminal in recovery mode. After that both Compiz effects worked and fceux compiled normally
strange because in the previous kernel while there were Compiz effects and Opengl worked, fceux wouldnt compile due to libgl.so

now problem has been fixed, mainly due to the new kernel. in the previous kernel even if I reinstalled Nvidia drivers, libgl.so would appear.

---

### Post by punkrockguy318 on 2013-03-10
2.2.1 released with some bug fixes and new features: [https://sourceforge.net/projects/fceultra/files/](https://sourceforge.net/projects/fceultra/files/)

enjoy!

---

### Post by punkrockguy318 on 2013-03-15
I'm not sure why I can't edit the OP anymore, but the new svn repo URL is:

svn checkout [http://svn.code.sf.net/p/fceultra/code/fceu/trunk](http://svn.code.sf.net/p/fceultra/code/fceu/trunk) fceultra

Cheers!

---

### Post by dannyboy79 on 2013-05-19
I had to 
```
sudo aptitude install liblua5.1-0-dev
```
and then everything worked out. Thanks for these instructions because the 1 provided in the repo's for 12.04 would seg fault after only 15 seconds and I found it because I run the Nvidia binary driver for my 8400 GS

---

