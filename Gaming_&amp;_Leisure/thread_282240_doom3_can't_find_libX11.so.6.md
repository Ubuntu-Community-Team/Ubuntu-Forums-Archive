---
title: "doom3 can't find libX11.so.6"
date: 2006-10-22
forum: Gaming &amp; Leisure
---

### Post by Episteme on 2006-10-22
I finally got doom 3 to install, but starting it results in ...

```
./doom.x86: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
```

```
find / -name libX11.so.6 -print
``` tells me that 

```
/usr/lib/libX11.so.6
```

and ```
file /usr/lib/libX11.so.6
```

states that ```
/usr/lib/libX11.so.6: symbolic link to `libX11.so.6.2.0'
```

and  ```
cat /etc/ld.so.conf
``` yields 

```
include /etc/ld.so.conf.d/*.conf
/usr/X11R6/lib
```

so I added 

```
/usr/lib
``` to that file, and ldconfig

But still, doom3 returns with

```
./doom.x86: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
```

I'm very new to linux - so if you can help, please try to be as specific as you can or I'll just get lost.

Many thanks,

Sean

[COLOR="Red"]
UPDATE 1:[/COLOR]

./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory.  

this file is also in the /usr/lib directory, so obviously the same problem here...

[COLOR="Red"]
UPDATE 2:[/COLOR]

I made a link in the /usr/local/games/doom3 folder called libX11.so.6 linking to /usr/lib/libX11.so.6.2.0  

Now, doom3 comes back to me with the following error

```
./doom.x86: error while loading shared libraries: libX11.so.6: wrong ELF class: ELFCLASS64
```

Apparently, while its supposed to run on a native 64 bit system - it needs the 32 bit version of libX11.so.6???  Hmmm.... that can't be right.

[COLOR="Red"]
UPDATE 3:[/COLOR]

Ok, I got ](*,)  by not being able to find the solution to this, so I just reverted back to Dapper so that I can get my frag on.  I'll wait for a 'edgy doom 3/quake4 howto' before I try it again.

---

### Post by horgh on 2006-10-27
Same problem here. But I don't want to downgrade my Ubuntu. I want to be able to run doom3 on Edgy. So if some guru is out there, please help us!

---

### Post by dreadmo on 2006-10-29
For some reason an upgrade from Dapper to Edgy on 64-bit systems removes the the 32-bit libraries that Doom 3 needs in order to run.  You'll need to install or reinstall the ia32 libraries. 
ia32-lib-sdl
ia32-libs
lib32asound2
Just install ia32-lib-sdl in your favorite package manager, and the other two libraries will also be installed.  That should do the trick.

---

### Post by horgh on 2006-10-30
Thanks! That did it! Anyway now I get this:

...
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()

Why is this so darn hard? Why can't everything just work? Now I have to figure out what is causing this, my guess is Nvidia beta drivers, but I need them for Beryl... The reason why most of the people don't use Linux is exactly this. Nothing works out-of-the-box. There is a chance to get it to work, but you'll need to spend your night browsing the web, and asking questions on these forums. Then maybe after month or so it'll work. ](*,)

---

### Post by dreadmo on 2006-10-30
I believe Beryl is the problem here.  OpenGL games (at least games like Doom 3) tend not to cooperate with eyecandy-makers like xgl, etc.  You'll probably have to go back to the standard xorg installation (with the standard nvidia-glx) to get it running again.

---

### Post by Perfect Storm on 2006-10-30
> Why is this so darn hard? Why can't everything just work? Now I have to figure out what is causing this, my guess is Nvidia beta drivers, but I need them for Beryl... The reason why most of the people don't use Linux is exactly this. Nothing works out-of-the-box. There is a chance to get it to work, but you'll need to spend your night browsing the web, and asking questions on these forums. Then maybe after month or so it'll work. 

Wrong! It's because beryl is in alpha stage and need to mature first. You did read that before starting installing beryl?
It takes time to learn a new system and its stuff, but you havn't chosen the easist way by installing 64 bit version (which very few application and games takes advantage off).

No need to smudge linux here, take deep breath and row down the river of learning.

---

### Post by LateNighter on 2006-11-01
> **Episteme said:**
> I finally got doom 3 to install, but starting it results in ...

```
./doom.x86: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
```

```
find / -name libX11.so.6 -print
``` tells me that 

```
/usr/lib/libX11.so.6
```

and ```
file /usr/lib/libX11.so.6
```

states that ```
/usr/lib/libX11.so.6: symbolic link to `libX11.so.6.2.0'
```

and  ```
cat /etc/ld.so.conf
``` yields 

```
include /etc/ld.so.conf.d/*.conf
/usr/X11R6/lib
```

so I added 

```
/usr/lib
``` to that file, and ldconfig

But still, doom3 returns with

```
./doom.x86: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory
```

I'm very new to linux - so if you can help, please try to be as specific as you can or I'll just get lost.

Many thanks,

Sean

[COLOR="Red"]
UPDATE 1:[/COLOR]

./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory.  

this file is also in the /usr/lib directory, so obviously the same problem here...

[COLOR="Red"]
UPDATE 2:[/COLOR]

I made a link in the /usr/local/games/doom3 folder called libX11.so.6 linking to /usr/lib/libX11.so.6.2.0  

Now, doom3 comes back to me with the following error

```
./doom.x86: error while loading shared libraries: libX11.so.6: wrong ELF class: ELFCLASS64
```

Apparently, while its supposed to run on a native 64 bit system - it needs the 32 bit version of libX11.so.6???  Hmmm.... that can't be right.

[COLOR="Red"]
UPDATE 3:[/COLOR]

Ok, I got ](*,)  by not being able to find the solution to this, so I just reverted back to Dapper so that I can get my frag on.  I'll wait for a 'edgy doom 3/quake4 howto' before I try it again.

 I'm about there myself, I just got a Dual Core 64 System ran fine in Dapper, Craps Out on Edgy.

 I get the same exact readings so don't feel so bad your not alone here.
 ](*,) ](*,) ](*,)

---

### Post by LateNighter on 2006-11-01
> **horgh said:**
> Thanks! That did it! Anyway now I get this:

...
glprogs/nv20_specularColor.vp
glprogs/nv20_diffuseAndSpecularColor.vp
glprogs/environment.vfp
glprogs/environment.vfp
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()

Why is this so darn hard? Why can't everything just work? Now I have to figure out what is causing this, my guess is Nvidia beta drivers, but I need them for Beryl... The reason why most of the people don't use Linux is exactly this. Nothing works out-of-the-box. There is a chance to get it to work, but you'll need to spend your night browsing the web, and asking questions on these forums. Then maybe after month or so it'll work. ](*,)

 Your forgetting ONE THING here.

 Windows very seldom WORKS perfect outta the box.

 Theres a big difference here, as I see it.

 Here you Work at it a little cost next too nothing...

 With Windows you Work alot and it cost you Hundreds...

 Just My Opinion.  You guessed it I Hate Windows period...

---

### Post by LateNighter on 2006-11-01
> **dreadmo said:**
> For some reason an upgrade from Dapper to Edgy on 64-bit systems removes the the 32-bit libraries that Doom 3 needs in order to run.  You'll need to install or reinstall the ia32 libraries. 
ia32-lib-sdl
ia32-libs
lib32asound2
Just install ia32-lib-sdl in your favorite package manager, and the other two libraries will also be installed.  That should do the trick.

 Listen to the Man!!!8) \\:D/ 

 This works for both DOOM3 as well as Quake4.

 But you will if your using anything Fancier then your Standard Nvidia glx modules.
 You'll have to revert back to the Nvidia glx modules.
 But ain't it WORTH it after all????

 To be able to FRAG a few Strogg as well as SAVE the Earth from the Demons of Hell....

 At least thats the way I see it... I get to FRAG ON....:mrgreen: 

 But once again I'd like to THANK my Friends here on the Forums for helping me Out, and for all they do to HELP further the cause off Linux....8) ;)

---

### Post by LateNighter on 2006-11-01
> **Artificial Intelligence said:**
> Wrong! It's because beryl is in alpha stage and need to mature first. You did read that before starting installing beryl?
It takes time to learn a new system and its stuff, but you havn't chosen the easist way by installing 64 bit version (which very few application and games takes advantage off).

No need to smudge linux here, take deep breath and row down the river of learning.

 Agreed...8)

---

