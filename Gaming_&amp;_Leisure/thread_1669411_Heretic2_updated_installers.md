---
title: "Heretic2 updated installers"
date: 2011-01-17
forum: Gaming &amp; Leisure
---

### Post by cjns1989 on 2011-01-17
I have this old Loki games CD: Heretic 2 and I still had it installed on my old laptop. 

I eventually had to upgrade to more recent machine. One thing I can't get to install properly is this old game. The install process runs fine, but when I click the 'play' button, I get the following errors:

**********************************************************
Registered 11 signal handlers

========================== Heretic II ===========================

Could not find /home/cjns/.loki/heretic2/default.cfg
Unable to exec default.cfg
Could not find /home/cjns/.loki/heretic2/config.cfg
Unable to exec config.cfg
NET Initialized
Failed to load DLL /usr/local/bin/base/client_effects.so:
        /usr/local/bin/base/client_effects.so: cannot open shared object file: No such file or directory
Failed to load DLL /usr/local/bin/base/client_effects.so:
        /usr/local/bin/base/client_effects.so: cannot open shared object file: No such file or directory
Failed to load DLL /client_effects.so:
        /client_effects.so: cannot open shared object file: No such file or directory
Failed to load any DLL client_effects

Exiting Heretic II...
Bummer. No cinematics/refresh running to close
Shutting down sound.
Shutting down input handling

*************************************************************

I have found a few threads  on this forum discussing 'old lokigames' compatibility issues, and I understand that I need to:

1. download a more recent installer than the one on the CD
2. download and apply two patches

Now the problem is that the links that were posted to the forum where I might be able to download the installer and patches appear to no longer be alive.

I would really like to get this piece of GNU/Linux history up and running again.

Thanks in advance for any advice.

cj

---

### Post by R33D3M33R on 2011-01-18
Try if this installer works: [http://www.liflg.org/?catid=7&gameid=94](http://www.liflg.org/?catid=7&gameid=94)

---

### Post by cjns1989 on 2011-01-19
Success..!

I first tried on debian lenny.. and was still getting the same errors.. Then I tried on ubuntu 10.10, and I was able to run the game, at least with the software renderer. On my new machine, it's not even slow or choppy at the highest 1600x1200 resolution and with maximum level of details. I'm not even sure I'm missing anything.

When I try OpenGL, I believe the game complains that it cannot find libgl.?.? and shuts down right away.. sounds like something that could easily be fixed. 

The other problem is that I don't have any sound..  just as well for now.. since it's already after 2 AM here in New York.. :-)

Anyway, I'll tweak it a bit over the weekend.

Thanks a bunch for the link..!

cj

PS. I think the link page has some kind of a forum.. or place for comments.. I'll make sure I thank them as well and report that I got it to work.

---

### Post by R33D3M33R on 2011-01-19
Try to run the game with the command padsp, like:

```
padsp executable
```

That could fix the sound issues.

Then run the command ldd, like:

```
ldd executable
```

That should tell you what dependencies are missing. Also: you can always try and symlink the libGL.so to the game directory using proper name.

---

### Post by cjns1989 on 2011-01-20
Sorry for the delay and thanks for reminding me of padsp. I had read about using the padsp command to launch heretic2, but I only have pulseaudio running on the ubuntu system, so I had forgotten about it.

As to switching from the softtware renderer to OpenGL, I think it is really worth my trying: I took a closer look and I'm pretty sure I'm not getting the texture quality I was getting with my old system. I thought I'd boot the partition that I religiously kept all those years on my former laptop, and try as I may I cannot get any of the 2.4 kernels that live there to boot..! Totally inexplicable, since I am pretty sure I took a look about two months ago and the system has been 'read-only' since then. They all appear to either end in a kernel panic or the boot process restarts automatically. It would be nice to be able to start both systems so I can have a side by side comparison. 

As to using ldd, I'm not sure how I can use the output. I guess you want me to check the existence of each lib that is listed on the ubuntu system, and if it's not there, install it? But then, are they still available anywhere, and won't they clash with more recent versions of the same lib's that are already installed?

You also mention creating a symlink from libgl.so to the game directory, but I don't know either why I would need to do that, and what to specify. 

Thanks,

cj

---

### Post by R33D3M33R on 2011-01-21
> **cjns1989 said:**
>  

As to using ldd, I'm not sure how I can use the output. I guess you want me to check the existence of each lib that is listed on the ubuntu system, and if it's not there, install it? But then, are they still available anywhere, and won't they clash with more recent versions of the same lib's that are already installed?

You also mention creating a symlink from libgl.so to the game directory, but I don't know either why I would need to do that, and what to specify. 

Thanks,

cj

Yes, ldd does that and if a dependency isn't satisfied you can always try and symlink the newer library to the game folder with the name, the game requests. Your first task would be to see if libGL is already installed:

```
dpkg -S libGL
```

With this code you can check the packages that contain the libGL.x.x.so. If you haven't already installed the right ones, you should do this. If the game still doesn't run, just do a symlink from /usr/lib/(wherever libGL.x.x.so is) to the directory where the binary is.

```
ln -s /usr/lib/(wherever libGL.x.x.so is) /game/directory/libGL(insert required version numbers here).so
```

This did work for me in many cases.

---

### Post by cjns1989 on 2011-01-21
> **R33D3M33R said:**
> Yes, ldd does that and if a dependency isn't satisfied you can always try and symlink the newer library to the game folder with the name, the game requests. Your first task would be to see if libGL is already installed:

```
dpkg -S libGL
```

[..]

```
ln -s /usr/lib/(wherever libGL.x.x.so is) /game/directory/libGL(insert required version numbers here).so
```

This did work for me in many cases.

Actually, the whole thing became a little clearer in my mind just after I went to bed last night: I need to check the error message and that should (hopefully) give me the name of the missing lib, hence what I need to call my symlink. Now, if the executable cannot find the lib via the system's ldconfig-uration.. it should also look for the lib in the directory where the executable was loaded from.

I need to reboot into ubuntu, and check what version is there and create the symlink. 

All the same if the library is in one of the usual places on the system, I'm not sure why the heretic2 executable is not able to find it. 

If the library is incompatible, I suppose I could look for an older version and copy it directly to the games directory. I have one on the old debian sarge system that worked, so maybe I could give that a try.

Hopefully, this won't turn out to be a case of a mismatch between the libgl that heretic2 needs and my (recent) card's capabilities and the nvidia closed source driver.

I'll probably be able to find more about this sometime tonight.

Till then.. 

Thanks much for all the help.

cj

---

### Post by cjns1989 on 2011-01-23
Well, I found a number of libGL.* libraries on the ubuntu system with the proprietary nvidia driver installed and tried creating symlinks to just about all of them, libGL.so.. libGL.1.so, ./nvidia/libGL.so, .nvidia/libGL.1.so.. etc. and I'm still getting the same 'failed to open OpenGL' error messages. I also tried pegging down my screen color depth to 16bits (as recommended in other threads) and specifiying a resolution of 640x400 in the heretic2 video configuration options.. No dice. 

I'm beginning to think that I won't be able to get OpenGL rendering with this FX 3700 nvidia card. I've seen other threads where other folks had to revert to an older version of the nvidia driver to get this to work. 

I haven't been able to get debian sarge to boot on  my old system, so as to compare the rendering, and this is yet another mystery, since I stopped making changes to that old laptop a couple of months ago, and certainly did not change anything to that sarge system or the bootloader for as long as I can remember. 

All the same, I'm pretty sure that I am not getting the most of heretic2 with the software renderer: the texture of walls for instance is far from optimal..

So right now, I'm pretty much stuck.. 

I did notice in the tarball I downloaded, that there are mentions of a 'c' level of updates.. (a README file in particular).. as opposed to the 'b' installer that I used.. so I'll take another look at the site you recommended and make sure I did use the most recent version.

A bit frustrating, of course.. but then even with the software renderer.. it's definitely much better than nothing.

Thanks,

cj

---

