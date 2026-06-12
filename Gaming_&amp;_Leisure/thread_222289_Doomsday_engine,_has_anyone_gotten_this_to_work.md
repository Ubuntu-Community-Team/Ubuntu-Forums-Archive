---
title: "Doomsday engine, has anyone gotten this to work?"
date: 2006-07-24
forum: Gaming &amp; Leisure
---

### Post by ravalox on 2006-07-24
Hey, I'm trying to install the doomsday engine so that I can play the revamped Doom and it resists any and all efforts to install it.  Following the compilation instructions I get: 
```

In file included from ../../../Src/dsSDLMixer/driver_sdlmixer.c:24:
../../../Src/dsSDLMixer/driver.h:37:25: error: SDL_mixer.h: No such file or directory
../../../Src/dsSDLMixer/driver_sdlmixer.c: In function 'DS_Init':
../../../Src/dsSDLMixer/driver_sdlmixer.c:117: error: 'MIX_DEFAULT_FREQUENCY' undeclared (first use in this function)
../../../Src/dsSDLMixer/driver_sdlmixer.c:117: error: (Each undeclared identifier is reported only once
../../../Src/dsSDLMixer/driver_sdlmixer.c:117: error: for each function it appears in.)
../../../Src/dsSDLMixer/driver_sdlmixer.c:117: error: 'MIX_DEFAULT_FORMAT' undeclared (first use in this function)
../../../Src/dsSDLMixer/driver_sdlmixer.c:124: error: 'MIX_CHANNELS' undeclared (first use in this function)
../../../Src/dsSDLMixer/driver_sdlmixer.c: In function 'DS_CreateBuffer':
../../../Src/dsSDLMixer/driver_sdlmixer.c:168: error: 'MIX_CHANNELS' undeclared (first use in this function)
../../../Src/dsSDLMixer/driver_sdlmixer.c: In function 'DS_Load':
../../../Src/dsSDLMixer/driver_sdlmixer.c:256: warning: assignment makes pointer from integer without a cast
../../../Src/dsSDLMixer/driver_sdlmixer.c: In function 'DS_Set':
../../../Src/dsSDLMixer/driver_sdlmixer.c:381: error: 'MIX_MAX_VOLUME' undeclared (first use in this function)
make[3]: *** [libdssdlmixer_la-driver_sdlmixer.lo] Error 1
make[3]: Leaving directory `/home/tate/games/deng-1.9.0-beta4/Build/Src/dsSDLMixer'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tate/games/deng-1.9.0-beta4/Build/Src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tate/games/deng-1.9.0-beta4/Build'
make: *** [all] Error 2

```

Then I tried to install it via the debian repository ([http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu)and](http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu)and) it took forever and didn't seem to install the binaries.  So my question is, has anyone been able to sneak up on Ubuntu and gotten this to work?

---

### Post by Yagisan on 2006-07-25
> **ravalox said:**
> Hey, I'm trying to install the doomsday engine so that I can play the revamped Doom and it resists any and all efforts to install it.  Following the compilation instructions I get: 
```

In file included from ../../../Src/dsSDLMixer/driver_sdlmixer.c:24:
../../../Src/dsSDLMixer/driver.h:37:25: error: SDL_mixer.h: No such file or directory
../../../Src/dsSDLMixer/driver_sdlmixer.c: In function 'DS_Init':
../../../Src/dsSDLMixer/driver_sdlmixer.c:117: error: 'MIX_DEFAULT_FREQUENCY' undeclared (first use in this function)
../../../Src/dsSDLMixer/driver_sdlmixer.c:117: error: (Each undeclared identifier is reported only once
../../../Src/dsSDLMixer/driver_sdlmixer.c:117: error: for each function it appears in.)
../../../Src/dsSDLMixer/driver_sdlmixer.c:117: error: 'MIX_DEFAULT_FORMAT' undeclared (first use in this function)
../../../Src/dsSDLMixer/driver_sdlmixer.c:124: error: 'MIX_CHANNELS' undeclared (first use in this function)
../../../Src/dsSDLMixer/driver_sdlmixer.c: In function 'DS_CreateBuffer':
../../../Src/dsSDLMixer/driver_sdlmixer.c:168: error: 'MIX_CHANNELS' undeclared (first use in this function)
../../../Src/dsSDLMixer/driver_sdlmixer.c: In function 'DS_Load':
../../../Src/dsSDLMixer/driver_sdlmixer.c:256: warning: assignment makes pointer from integer without a cast
../../../Src/dsSDLMixer/driver_sdlmixer.c: In function 'DS_Set':
../../../Src/dsSDLMixer/driver_sdlmixer.c:381: error: 'MIX_MAX_VOLUME' undeclared (first use in this function)
make[3]: *** [libdssdlmixer_la-driver_sdlmixer.lo] Error 1
make[3]: Leaving directory `/home/tate/games/deng-1.9.0-beta4/Build/Src/dsSDLMixer'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tate/games/deng-1.9.0-beta4/Build/Src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tate/games/deng-1.9.0-beta4/Build'
make: *** [all] Error 2

```
You are missing sdl mixer - which is in the compilation instructions.

> **ravalox said:**
> Then I tried to install it via the debian repository ([http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu](http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu)) and it took forever and didn't seem to install the binaries.  So my question is, has anyone been able to sneak up on Ubuntu and gotten this to work? It does install binaries, Right where it says on that page, and you even get a nice menu in Applications -> Games.

Please state what version of Ubuntu you use so I can direct you to the most approriate files.

You are aware I have a faster mirror right ?

---

### Post by rogeriovinhal on 2006-07-25
Hi, I've added the fast repository to my sources.list, but apt-get update doesn't seem to update it, because it keeps trying on the server, and after some time it gives up with connection expired.

Anyway, does doomslegacy work on Ubuntu dapper AMD64?
It was not clear on that page. And do I have to install all packages?

EDIT:
I managed to install it, but it is not working.
```

DD_InitDGL: Loading of libdropengl failed.
  libGL.so.1: cannot open shared object file: No such file or directory.

```

I have an ATI card, with 3d acceleration enabled with the fglrx driver.
libGL.so.1 is where it should be, and even in the lib32 folders.

Is that a problem with AMD64? How do I get over it?

---

### Post by Yagisan on 2006-07-26
> **rogeriovinhal said:**
> Hi, I've added the fast repository to my sources.list, but apt-get update doesn't seem to update it, because it keeps trying on the server, and after some time it gives up with connection expired.I've just been told that the fast server went offline yesterday :(

> **rogeriovinhal said:**
> Anyway, does doomslegacy work on Ubuntu dapper AMD64?
No idea

> **rogeriovinhal said:**
> It was not clear on that page. And do I have to install all packages?
You need at a minimum, deng, one of the iwad installers, and if amd64 - all of the ia32-libs packages it wants to install.

> **rogeriovinhal said:**
> EDIT:
I managed to install it, but it is not working.
```

DD_InitDGL: Loading of libdropengl failed.
  libGL.so.1: cannot open shared object file: No such file or directory.

```

I have an ATI card, with 3d acceleration enabled with the fglrx driver.
libGL.so.1 is where it should be, and even in the lib32 folders.

Is that a problem with AMD64? How do I get over it?
What is your output from ?
```
ldd /usr/lib/deng/libdropengl.so.0.0.0
```
On my amd64 system (nvidia) it looks like this
```
ldd /usr/lib/deng/libdropengl.so.0.0.0
        linux-gate.so.1 =>  (0xffffe000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0x55571000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0x555f9000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0x5560b000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0x55690000)
        libc.so.6 => /lib32/libc.so.6 (0x55706000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0x55836000)
        libm.so.6 => /lib32/libm.so.6 (0x558f2000)
        libdl.so.2 => /lib32/libdl.so.2 (0x55914000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x55917000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x559fd000)
        /lib/ld-linux.so.2 (0x56555000)
        libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0x55a0a000)
        libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0x561cd000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0x561cf000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x562af000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x562ba000)
```

---

### Post by rogeriovinhal on 2006-07-26
They were pointing to "not found", but as I saw there I realized that the program searches for libGL in /lib32, not /usr/lib32. So I made 2 symlinks for them and it was fine.

But now my problem is sound.
It has no sound at all, and when I load doomsday the following warning is shown:
```

Sfx_Init: Initializing SDL_mixer...
DS_Load: Loading of libdssdlmixer failed.
Sfx_Init: Driver init failed. Sfx is disabled.
S_Init: Errors during initialization..

```

So I tried to see the others libraries just as you told me to do with video and this is it:

```

ldd /usr/lib/deng/libdsopenal.so.0.0.0
        linux-gate.so.1 =>  (0xffffe000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7f4c000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7f3a000)
        libopenal.so.0 => not found
        libc.so.6 => /lib32/libc.so.6 (0xf7e0b000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7d4f000)
        libm.so.6 => /lib32/libm.so.6 (0xf7d2c000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7d29000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7c43000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7c36000)
        /lib/ld-linux.so.2 (0x56555000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7c33000)

```

```

ldd /usr/lib/deng/libdssdlmixer.so.0.0.0
        linux-gate.so.1 =>  (0xffffe000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7e31000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7e1f000)
        libSDL_mixer-1.2.so.0 => /usr/lib32/libSDL_mixer-1.2.so.0 (0xf7db1000)
        libc.so.6 => /lib32/libc.so.6 (0xf7c82000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7bc6000)
        libm.so.6 => /lib32/libm.so.6 (0xf7ba3000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7ba0000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7aba000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf7aad000)
        /lib/ld-linux.so.2 (0x56555000)
        libvorbisfile.so.3 => not found
        libvorbis.so.0 => not found
        libogg.so.0 => not found
        libsmpeg-0.4.so.0 => not found
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf7aa9000)

```

Anyway, the game loaded properly, but it looked like the normal doom with higher resolutions, but how can I make it look like this:
[http://www.doomsdayhq.com/screenshots/doom_001.jpg](http://www.doomsdayhq.com/screenshots/doom_001.jpg)

Another thing, is that it only runs on fullscreen. Is there any way to make it work on a window?

And have you any plans to make doomsday work also with Final Doom?

---

### Post by HAARP on 2006-07-26
Doomsday works with Final Doom. Use
**deng-iwad-plutonia-installer** and **deng-iwad-tnt-installer**

Use the Resource Packs to get new models. They were on the DHQ page, at least before the redesign. Now I can't seem to find the Downloads section :s
Well, you'll find them somewhere. They make it look more 3D-ish, like in the screenshot.
There also are Packs for textures, patches and just about anything. But I can't find those either.

---

### Post by rogeriovinhal on 2006-07-26
Doomsday is hard-freezing my computer... :( 

After some time, like 5 to 10 minutes, doomsday simply freezes, and nothing else works. No Ctrl+alt+Fx, no Ctrl+alt+backspace, no shutdown button...
Everything locks and requires a hard reset. (Even then I can see that Azureus is working because of the network traffic).

Is there any log or something I can look at to find this error?

---

### Post by DoktorSeven on 2006-07-26
I've experienced the same with the latest versions (1.9.0) of Doomsday so I've had to go back to 1.8.6, though I still get the occasional freeze.  It's basically segfaulting, but not going back to the desktop.

However, I am able to unstick it by going to a console (C-A-F2) and killing (SIGKILL) it.

---

### Post by Yagisan on 2006-07-27
> **rogeriovinhal said:**
> They were pointing to "not found", but as I saw there I realized that the program searches for libGL in /lib32, not /usr/lib32. So I made 2 symlinks for them and it was fine.
That is odd
> **rogeriovinhalBut now my problem is sound.
It has no sound at all, and when I load doomsday the following warning is shown:
```

Sfx_Init: Initializing SDL_mixer...
DS_Load: Loading of libdssdlmixer failed.
Sfx_Init: Driver init failed. Sfx is disabled.
S_Init: Errors during initialization..

```[/quote]
You are missing the ia32-libs-universe package. (same repo as doomsday)
[QUOTE=rogeriovinhal said:**
> Another thing, is that it only runs on fullscreen. Is there any way to make it work on a window? add -wnd to the command line

---

### Post by Yagisan on 2006-07-27
> **HAARP said:**
> Doomsday works with Final Doom. Use
**deng-iwad-plutonia-installer** and **deng-iwad-tnt-installer**

Use the Resource Packs to get new models. They were on the DHQ page, at least before the redesign. Now I can't seem to find the Downloads section :s
Well, you'll find them somewhere. They make it look more 3D-ish, like in the screenshot.
There also are Packs for textures, patches and just about anything. But I can't find those either.
You'll find them in the **breezy** repo. When deng is more stable on dapper I'll update them to dapper.

---

### Post by Yagisan on 2006-07-27
> **rogeriovinhal said:**
> Is there any log or something I can look at to find this error?
~/.deng/Doomsday.out

---

### Post by Yagisan on 2006-07-27
> **DoktorSeven said:**
> I've experienced the same with the latest versions (1.9.0) of Doomsday so I've had to go back to 1.8.6, though I still get the occasional freeze.  It's basically segfaulting, but not going back to the desktop.

However, I am able to unstick it by going to a console (C-A-F2) and killing (SIGKILL) it.
I belive I have fixed many of these in what will be beta5. I intend to packages a svn version soon and release that for dapper. It however is not network compatible with older versions dues to security fixes.

---

### Post by rogeriovinhal on 2006-07-27
What about sound? I still can't get it... :( 

The log Doomsday.out show nothing strange, just game messages...

I just put the breezy repos, and the version in them is the same as dappers. Are there 1.8.6 packages?

---

### Post by HAARP on 2006-07-27
> **Yagisan said:**
> You'll find them in the **breezy** repo. When deng is more stable on dapper I'll update them to dapper.

Strange, because I got them from your Dapper repo and they worked :confused:

edit: ah, you meant the Resource Packs? I don't have those.
Can you make an estimation when deng will be stable? I just can't wait to kill some high-quality demons :cool:

---

### Post by Yagisan on 2006-07-27
> **rogeriovinhal said:**
> What about sound? I still can't get it... :( Please make sure you install the recommends and suggests files from deng, such as timdity and freepats. Did you install deng via synaptic or aptitude (if you did dpkg -i you will have problems as you would miss all support files)

> **rogeriovinhal said:**
> I just put the breezy repos, and the version in them is the same as dappers. Are there 1.8.6 packages?Actually dapper is beta4, breezy is beta3. 1.8.6 packages are no longer available as we dicovered the 1.9.0betas are a) more stable on more machines, and b) The is a public remote security exploit in every version less then 1.9.0beta4, so we strongly recommand you use that.

---

### Post by Yagisan on 2006-07-27
> **HAARP said:**
> Strange, because I got them from your Dapper repo and they worked :confused:

edit: ah, you meant the Resource Packs? I don't have those.
Yes that's what I meant.

> **HAARP said:**
> Can you make an estimation when deng will be stable? I just can't wait to kill some high-quality demons :cool: I expect to do more work on it this weekend, but I'm rather ill at the moment, so I can't gaurantee it.

---

### Post by rogeriovinhal on 2006-07-27
> **Yagisan said:**
> Please make sure you install the recommends and suggests files from deng, such as timdity and freepats. Did you install deng via synaptic or aptitude (if you did dpkg -i you will have problems as you would miss all support files)

Actually dapper is beta4, breezy is beta3. 1.8.6 packages are no longer available as we dicovered the 1.9.0betas are a) more stable on more machines, and b) The is a public remote security exploit in every version less then 1.9.0beta4, so we strongly recommand you use that.

Timidity and freepats are installed, but the libdssdlmixer.so.0.0.0 is missing some files, like this:

```

        libvorbisfile.so.3 => not found
        libvorbis.so.0 => not found
        libogg.so.0 => not found
        libsmpeg-0.4.so.0 => not found

```

Although I do have them in /usr/lib. What symlinks should I do to make it see them? I Tried to make symlinks in /lib32, /usr/lib32, /lib, and anywhere I thought It might see it.

And actually, I have installed deng from the dapper repos, and now it says that the version installed is beta 4, and the version to install is also beta4 (now from the breezy packages).

---

### Post by HAARP on 2006-07-28
Whoo, new version!
But there's something strange. As I was playing D2, there was a strange flare  on MAP09. It didn't dissapear, even when I walked into another room. Looked like it was inside a wall. Can't reproduce it.
Also, music on MAP08 seemed a bit strange to me, with some instruments being "echo-y"

I've got 2 questions:
Is Jumping by default allowed in Doom2?
Is it possible to use the Resource Packs from your Breezy repository for the Dapper version of deng?

---

### Post by rogeriovinhal on 2006-07-28
I just updated today to the beta4-ubuntu2, and now the sound works.

But the repository is far too slow (about 1 KB/s). I tried the other mirror, and it doesn't work. Is there anywhere else I can get at least the sound package (272 MB)?

---

### Post by Yagisan on 2006-07-29
> **rogeriovinhal said:**
> I just updated today to the beta4-ubuntu2, and now the sound works.

But the repository is far too slow (about 1 KB/s). I tried the other mirror, and it doesn't work. Is there anywhere else I can get at least the sound package (272 MB)?
It's called every man and his dog leaching at once. That is the only working repo (and the primary repo all others used to sync to it). I requested a speed upgrade some time ago. I'm still waiting for it.

Queue it up overnight, Send donations for a fatter pipe, or buy something so I can pay for bigger pipes.

---

### Post by Yagisan on 2006-07-29
> **HAARP said:**
> But there's something strange. As I was playing D2, there was a strange flare  on MAP09. It didn't dissapear, even when I walked into another room. Looked like it was inside a wall. Can't reproduce it.odd stuff

> **HAARP said:**
> Also, music on MAP08 seemed a bit strange to me, with some instruments being "echo-y"SDL_Mixer is procesing the music at the moment. As the packs arrive for dapper you'll get music packs that sound better.

> **HAARP said:**
> I've got 2 questions:
Is Jumping by default allowed in Doom2?Need to turn it on in the options.
> **HAARP said:**
> Is it possible to use the Resource Packs from your Breezy repository for the Dapper version of deng?for now yes, but new versions are comming (heretic already done for dapper)

---

### Post by HAARP on 2006-07-29
> **Yagisan said:**
> odd stuff
Got a Screenshot. It was much brighter ingame.
[[IMG]http://img132.imageshack.us/img132/4305/doom2flareep3.th.jpg[/IMG]](http://img132.imageshack.us/my.php?image=doom2flareep3.jpg)

> SDL_Mixer is procesing the music at the moment. As the packs arrive for dapper you'll get music packs that sound better.
Sycraft's stuff? Hell yeah :cool: 
I've got a recording somewhere if you want it.

> Need to turn it on in the options.
Agh, so I was playing the whole time with "semi-cheats" :s

> for now yes, but new versions are comming (heretic already done for dapper)
What's the difference between the versions?


Also, may I tell you that your /usr/share/pixmaps/deng.png is corrupted with 0 bytes? ;-)

---

### Post by Yagisan on 2006-07-29
> **HAARP said:**
> Got a Screenshot. It was much brighter ingame.
[[IMG]http://img132.imageshack.us/img132/4305/doom2flareep3.th.jpg[/IMG]](http://img132.imageshack.us/my.php?image=doom2flareep3.jpg)
Do yoy have a map location for that ? I couldn't see it myself.

> **HAARP said:**
> Sycraft's stuff? Hell yeah :cool: 
I've got a recording somewhere if you want it. Sycrafts music is already part of the pack.

> **HAARP said:**
> Agh, so I was playing the whole time with "semi-cheats" :swell, in that case, so is mouse-look ...

> **HAARP said:**
> What's the difference between the versions?
Hexen gets some conflicting packs removed, while doom gets some masive updates. To get an idea of what doom will look like check out these:
[http://forums.newdoom.com/showpost.php?p=474263&postcount=14](http://forums.newdoom.com/showpost.php?p=474263&postcount=14)
[http://forums.newdoom.com/showpost.php?p=474265&postcount=15](http://forums.newdoom.com/showpost.php?p=474265&postcount=15)
[http://forums.newdoom.com/showpost.php?p=474270&postcount=16](http://forums.newdoom.com/showpost.php?p=474270&postcount=16)
[http://forums.newdoom.com/showpost.php?p=474382&postcount=17](http://forums.newdoom.com/showpost.php?p=474382&postcount=17)

> **HAARP said:**
> Also, may I tell you that your /usr/share/pixmaps/deng.png is corrupted with 0 bytes? ;-)
Yes, it's been reported a few times now. Something went wrong in the build in the icon generation stage. It will become part of beta 5 so I think I should leave it for now.

---

### Post by HAARP on 2006-07-29
> **Yagisan said:**
> Do yoy have a map location for that ? I couldn't see it myself.

It was everywhere on the map, but always seemed to be inside a wall. As I said, it's not reproducable :/
Well, it's not that important anyway, just irritating

Screens looking sweet! :D

---

### Post by rogeriovinhal on 2006-07-31
I have been trying to play doomsday, but it doesn't let me!
It locks everytime at most after 5 minutes of gameplay, but it is completely random in time and place. It has even locked one time in the Menu Screen.

And the worst part is that doomsday takes over the control of the OS, cancelling all the hotkeys, making it impossible to do something like Ctrl+Alt+F1 to kill the proccess. So, It just makes me do a hard-reset everytime I play it.

Isn't there a way to make doomsday work in a window? It would at least make it possible to kill it when it locks without hard-resetting.

But when you have time, if I am not the only one experiencing these locks, I think that fixing them should be a number 1 priority to the project, since no one will want to play a game that locks after at most 5 minutes.

---

### Post by Yagisan on 2006-07-31
> **rogeriovinhal said:**
> I have been trying to play doomsday, but it doesn't let me!
It locks everytime at most after 5 minutes of gameplay, but it is completely random in time and place. It has even locked one time in the Menu Screen.I've never had a report of that before.

> **rogeriovinhal said:**
> And the worst part is that doomsday takes over the control of the OS, cancelling all the hotkeys, making it impossible to do something like Ctrl+Alt+F1 to kill the proccess. So, It just makes me do a hard-reset everytime I play it.Doomsday doesn't takeover the hotkeys, so a hard lock would not cause it to prevent things like Ctrl+Alt+F1 from working.

> **rogeriovinhal said:**
> Isn't there a way to make doomsday work in a window? It would at least make it possible to kill it when it locks without hard-resetting. You need to add -wnd to the doomsday comandline (it is documented in the manual - info doomsday)

> **rogeriovinhal said:**
> But when you have time, if I am not the only one experiencing these locks, I think that fixing them should be a number 1 priority to the project, since no one will want to play a game that locks after at most 5 minutes.You are the only one, but I'd like you to send me a diganostic report anyway.

Please run from a command prompt:
reportbug deng
Follow the prompts to type out your problem and mail it and all the information it gathers to me for debugging.

Two possible causes I can think of offhand are 1) ati binary drivers or 2) overheating

---

### Post by rogeriovinhal on 2006-07-31
I e filled up the report, but I can't find your e-mail address to send it, so I'm attaching it right here.

---

### Post by Yagisan on 2006-08-01
> **rogeriovinhal said:**
> I e filled up the report, but I can't find your e-mail address to send it, so I'm attaching it right here.

Reportbug usually reads the email address from the package and send it there. In any case I'll examine it as soon I have time. Thanks for the report

---

### Post by HAARP on 2006-08-02
When I use the secret teleporter in D2 MAP15 to get to MAP31 (Wolf), I end up in MAP16 instead. When i type **setmap 1 31** in console, I end up in MAP01. No suspicious console output either.
But I can remember playing the Wolf map on Doomsday, back in my Windoze days and with the same WAD. What gives?

---

### Post by Yagisan on 2006-08-07
> **HAARP said:**
> When I use the secret teleporter in D2 MAP15 to get to MAP31 (Wolf), I end up in MAP16 instead. When i type **setmap 1 31** in console, I end up in MAP01. No suspicious console output either.
But I can remember playing the Wolf map on Doomsday, back in my Windoze days and with the same WAD. What gives?

Use warp XX where XX is the level you want to go to. I'll make a note to check the map15 exit when I get time.

---

### Post by HAARP on 2006-08-07
> **Yagisan said:**
> Use warp XX where XX is the level you want to go to. I'll make a note to check the map15 exit when I get time.

**warp 01**-**30** works fine, **warp 31** does nothing.
I don't get it :|

---

### Post by Yagisan on 2006-08-07
> **HAARP said:**
> **warp 01**-**30** works fine, **warp 31** does nothing.
I don't get it :|

Levels 31 and 32 don't exist in the german version of doom2 because of the nazi symbols. Are you sure you don't have the german version ?

---

### Post by HAARP on 2006-08-07
> **Yagisan said:**
> Levels 31 and 32 don't exist in the german version of doom2 because of the nazi symbols. Are you sure you don't have the german version ?

I'm quite sure I have an english version.
But is there any way to be sure? Do you have a md5 of your doom2.wad? Mine is **d9153ced9fd5b898b36cc5844e35b520**

---

### Post by Yagisan on 2006-08-08
Doom2 Version 1.9
**25e1459ca71d321525f84628f45ca8cd  doom2.wad**

---

### Post by HAARP on 2006-08-08
I don't understand. I bought an English version, yet I seem to have a censored wadfile??

A friend gave me his game. I patched it and it's got the same md5 as yours now. The levels work now :) Thanks!

---

### Post by hk_2999 on 2006-10-26
Can anyone help me? Im running the 32 bit version in Edgy 64-bit, and it's 
fragging me with a segfault. :(

```
$ doomsday -anifilter -texcomp -game jdoom -file /usr/share/games/deng/Data/jDoom/doom2.wad
LoadPlugin: /home/maruko/den/lib/libdpdehread
LoadPlugin: /home/maruko/den/lib/libdpmapload
Z_Create: New 32.0 MB memory volume.
Con_Init: Initializing the console.
SW_Init: Startup message window opened.
Executable: Version 1.9.0-beta4 Oct 26 2006 (DGL).
G_PreInit: Registering Bind Classes...
Parsing configuration files.
W_Init: Init WADfiles.
W_AddFile: /usr/share/games/deng/Data/jDoom/doom2.wad
  IWAD identification: 00f36acb
W_AddFile: Data/Doomsday.pk3
W_AddFile: Data/jDoom/jDoom.wad
  IWAD identification: 00056533
Reading definition file: Defs/Doomsday.ded
Reading definition file: Defs/jDoom/jDoom.ded
  138 sprite names
  974 states
  140 things
    8 lights
  112 sound effects
   68 songs
  351 text strings
   27 particle generators
   22 animation groups
   51 surface decorations
   69 map infos
   12 finales
Sys_Init: Setting up machine state.
Sys_Init: Initializing keyboard, mouse and joystick.
I_InitJoystick: No joysticks found
Sys_InitTimer.
Sfx_Init: Initializing SDL_mixer...
open /dev/sequencer: No such file or directory
S_Init: OK.
R_Init: Init the refresh daemon.
Segmentation fault (core dumped)

```

---

### Post by Yagisan on 2006-10-29
Update your repo - and remember - until my website says Edgy is the current release, it may bite you like this. While pakages are there, they are not all ready.

---

### Post by hk_2999 on 2006-10-30
Thanks Yagi-san! Can't believe it actually worked. It's fraggin time. ;)

There is a little bug when you are changing the resolution though:
```
X Error of failed request:  GLXBadContextTag
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  144 ()
  Serial number of failed request:  188977
  Current serial number in output stream:  192123

```

So I guess im stuck at 600x480 though.

---

### Post by Yagisan on 2006-11-03
Can't say I've had that error before.
Run reportbug dengm paste the error in, then lookf for the report in /tmp and email it to me, and I'll investigate it.

---

### Post by hk_2999 on 2006-11-03
I also found out that most resource packs on auto don't work. After installing some of the resource packs to change the HUD, make monsters 3d, music pakcs, or  higher quality textures, I don't see these packages working in game.

Got to my /usr/share/games/deng directory and found out there are two data and defs directories. data, def Data and Def.

---

### Post by Yagisan on 2006-11-03
> **hk_2999 said:**
> I also found out that most resource packs on auto don't work. After installing some of the resource packs to change the HUD, make monsters 3d, music pakcs, or  higher quality textures, I don't see these packages working in game.

Got to my /usr/share/games/deng directory and found out there are two data and defs directories. data, def Data and Def.

Yes - it's not a bug. It will be updated in due time.

---

### Post by hk_2999 on 2006-11-09
K - but please fix it soon...

---

### Post by Yagisan on 2006-11-12
Will do, but I need to update the packs as they updated, and the upstream website is gone. To top it off, it is first week of uni as well, but I'll get it done when I get some free time.

---

### Post by tribunal on 2006-11-30
> **Yagisan said:**
> Will do, but I need to update the packs as they updated, and the upstream website is gone. To top it off, it is first week of uni as well, but I'll get it done when I get some free time.
Thank you! :)
Doom's fans from all over the world are waiting :)

---

### Post by hikaricore on 2007-03-27
For anyone who stumble upon this thread looking for doomsday packages,
Yagisan has taken a break from everything to deal with real life issues.  As
of this point the ubuntu/debian packages are offline and have been for
months now.  It was mentioned they might be up again in December or
shortly there after, but until then you'll need to compile the software
yourself.  I have no association with this project, I just noticed it was
down and wanted to share the news I tracked down about this.

Good luck folks.

Info here: [http://forums.newdoom.com/showthread.php?t=32511](http://forums.newdoom.com/showthread.php?t=32511)

---

### Post by darknewtony2k on 2007-06-10
**[SIZE="4"]T[/SIZE]**his is the worst Notice that I've Heard!!!! ¿Anyone tell us how to run Doom in Feisty Fawn?

---

### Post by hikaricore on 2007-06-10
Use another doom port instead of doomsday perhaps?  There's hundreds of them in existance.

You'll find atleast 5 in the ubuntu repos if I'm not mistaken.

---

### Post by darknewtony2k on 2007-06-10
Thanks for the Advice. [-o< The Family is grateful.

---

### Post by trogo on 2007-06-28
Just to report: prboom and lxdoom are not working on feisty with beryl while doomsday works like a charm! Prboom crashes and lxdoom works if u choose metacity ad window manager in an XGL session with gnome. However setting the "current" branch of yagisan's repo i installed and successfully played doomsday! Thank you Yagisan!

PS: i am still trying to use the 3d models but i think i'll find out soon how to do it!

---

### Post by weblordpepe on 2007-06-28
Doomsday works? Rad! I'll have to look into that cos its my favourite port by a mile. prboom works though. You just gotta specify the iwad path. I think. At least thats how it works for me.

---

### Post by trogo on 2007-06-28
I did specify the iwad path for prboom and it works... but just for the first room! As i try to shoot the first enemy the game freezes and i have to close it!! Lxdoom instead is semi -transparent if i use emeral as window manager but it works with metacity! Remember: i think the problem with these two ports is beryl, so if you didn't install it you should have no problem!

To install doomsday on feisty however you just have to add these who lines to your /etc/apt/sources.list:

#doom 3d! HEHEHHEHEH! Thanks Yagisan!
deb [http://eyagi.bpa.nu/~jamie/ubuntu](http://eyagi.bpa.nu/~jamie/ubuntu) current main restricted universe multiverse
deb-src [http://eyagi.bpa.nu/~jamie/ubuntu](http://eyagi.bpa.nu/~jamie/ubuntu) current main restricted universe multiverse

and then apt-get install deng-jdoom-ui and the iwad installer you need! I still miss the 3d effects even if i installed the deng-jdoom-rp packages, but i'll post here the solution when i'll find it!

Bye!

---

### Post by weblordpepe on 2007-06-28
YESSSSSSSSSSsssssssssssssssss

Although what the hell is doomu.wad ? Is that ultimate doom? I got doom2 going great. As a long time Doom nut, it is an honour to be in the same forum as Yagisan.

---

### Post by hikaricore on 2007-06-28
> **weblordpepe said:**
> YESSSSSSSSSSsssssssssssssssss

Although what the hell is doomu.wad ? Is that ultimate doom? I got doom2 going great. As a long time Doom nut, it is an honour to be in the same forum as Yagisan.

Yes doomu.wad is the Ultimate Doom.

The original Doom "wad" files are still commercial material.
You will need to either get the file from a copy of Ultimate Doom you own, or find it via another source.

---

### Post by weblordpepe on 2007-06-29
Coooooooooooooooooool.

---

### Post by DaniJ on 2007-06-29
Hey guys, glad to see so many of you enjoying Doomsday :)

I'm DaniJ, one of Doomsday's coders and historically a Windows-only developer... that was untill I decided that since Yagisan had been doing such a great job in improving our project for consumption under Ubuntu and *nix in general; that I would repay his efforts and our growing Ubuntu userbase by trying out this "Ubuntu thing" for myself.

In short, I really like it and would like to pledge a greater degree of support for your platform in future. I'm very much an Ubuntu newbie but a fairly experienced programmer, so with a little help I hope to be up to speed quickly.

---

### Post by weblordpepe on 2007-06-30
Wow!
I am a HUGE fan of Doomsday. Welcome to Ubuntu. You guys have made a damn nice port of Doom. I exploded when I saw that there was a native version for linux. 

Good on ya for taking a nose at Ubuntu. If theres anything we can help with, just shout out. Its the least we can do in return for the work you guys have put in on Doomsday.

---

### Post by hikaricore on 2007-06-30
> **DaniJ said:**
> Hey guys, glad to see so many of you enjoying Doomsday :)

I'm DaniJ, one of Doomsday's coders and historically a Windows-only developer... that was untill I decided that since Yagisan had been doing such a great job in improving our project for consumption under Ubuntu and *nix in general; that I would repay his efforts and our growing Ubuntu userbase by trying out this "Ubuntu thing" for myself.

In short, I really like it and would like to pledge a greater degree of support for your platform in future. I'm very much an Ubuntu newbie but a fairly experienced programmer, so with a little help I hope to be up to speed quickly.

Fantastic.  ^_^  Welcome.

---

### Post by bmwman91 on 2007-12-16
> **rogeriovinhal said:**
> I have been trying to play doomsday, but it doesn't let me!
It locks everytime at most after 5 minutes of gameplay, but it is completely random in time and place. It has even locked one time in the Menu Screen.

And the worst part is that doomsday takes over the control of the OS, cancelling all the hotkeys, making it impossible to do something like Ctrl+Alt+F1 to kill the proccess. So, It just makes me do a hard-reset everytime I play it.

Isn't there a way to make doomsday work in a window? It would at least make it possible to kill it when it locks without hard-resetting.

But when you have time, if I am not the only one experiencing these locks, I think that fixing them should be a number 1 priority to the project, since no one will want to play a game that locks after at most 5 minutes.

I an having the exact same problem myself actually.  Both Doomsday and prBoom do it.  Frustrating...

---

### Post by weblordpepe on 2007-12-16
> **bmwman91 said:**
> I an having the exact same problem myself actually.  Both Doomsday and prBoom do it.  Frustrating...I had it happening with prBoom.

I'm not sure about the crashing - but I think it was to do with a wonky pwad or iwad that shipped with it. But you should be able to use the menus or a config to at least put it in a window. 

Or

Can you redirect the stderr and stdout to a text file? You do that on the command line:
 **doomsday > filename**

---

### Post by Adrian Not on 2008-09-19
I seem to be OK with up-to-date doomsday and kubuntu (KDE4). I have compiled doomsday following their instructions, copied the iwad files and run doom1&2 using the command lines explained for the windows version (I guess these are included in the linux version too).

```
doomsday -nomouse -nofmod -nomusic -game jdoom -file /usr/share/games/doom/doom1.wad
```

I'm not using the mouse and I don't care about music, -nofmod seems to be needed. I did have problems, but reading the documentation helped. It's really great to play Doom after so many years! :KS

Cheers

---

### Post by chungy on 2008-09-20
> **hikaricore said:**
> You will need to either get the file from a copy of Ultimate Doom you own, or find it via another source.

Well it's probably easier to just use fewer words and tell people to [just buy it](http://www.amazon.com/Doom-Collectors-Pc/dp/B0002IBEJQ/ref=pd_cp_sw_3?pf_rd_p=433272301&pf_rd_s=center-41&pf_rd_t=201&pf_rd_i=B0002Z3KRS&pf_rd_m=ATVPDKIKX0DER&pf_rd_r=0N5HGS5V97EP3J773354)

---

### Post by Yagisan on 2008-10-22
I'm still alive and kicking. My packages would now be found over -> [https://launchpad.net/~yagisan/+archive](https://launchpad.net/~yagisan/+archive)

---

### Post by pirattrev on 2008-10-30
_**[COLOR="Red"]THE ULTIMATE SOLUTION TO YOUR PROBLEM[/COLOR]**_

instead of trying to compile or install the doomsday engine, which takes time, effort, blood and tears, do what I did. Torrent the "Doom + Heretic + Hexen" package on thepiratebay.org.  It works perfectly, no freezing, no problems.  Here's why: because it runs in java, through wine. It comes neatly packaged with jDoom.exe, jHexen.exe, and jHeretic.exe, each with all the WADS, extras and other wonderful goodies.  It's easy to install and set up your liking [longest part is unpackaging the .7z files] and there is, wait for it, literally 10 seconds of actual installation. I know that it's not linux, it's a windows and wine cop-out, but believe me, it's perfect, it's simple, and it just works.

*disclaimer: I cannot post the torrent files because the torrent in question contains the WADS for the full you-gotta-pay games.  So, if you want to do this the legal way, download the torrent, delete the WADS you aren't supposed to own and then procure your own legal WADS.  If you have the game aleady elsewhere, I believe it's okay to get the WADS again.  Besides, you don't need them, the most important part of the torrent is the .exe files for Doomsday, jDoom, jHexen and jHeretic.*

If you follow my advice, you will not be disappointed. Also for the linux-only among you, I believe it's possible to run the files without wine and only java, but I'm not positive on that.

---

### Post by Athropos on 2008-12-22
> **Yagisan said:**
> I'm still alive and kicking. My packages would now be found over -> [https://launchpad.net/~yagisan/+archive](https://launchpad.net/~yagisan/+archive)

Hey, just wanted to thank you for your work on Doomsday and your repository. For me, Doom will forever be the best and funniest FPS game.

---

