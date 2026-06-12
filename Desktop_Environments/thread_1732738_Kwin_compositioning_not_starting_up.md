---
title: "Kwin compositioning not starting up"
date: 2011-04-18
forum: Desktop Environments
---

### Post by el_koraco on 2011-04-18
Lol, for some unfathomable reason Kwin just went all Compiz on my Kubuntu Natty 11.04. Fresh install, x86 Emachines V140 AMD GPU, Mobility Radeon 4200, radeon driver. 

Anyhoo, desktop effects got disabled out of the blue, probably after some setting I've changed, and there was no way to get them back. I'd hit enable effects in the Desktop Effects panel, whereupon I would get a notification that dekstop effects were disabled because of another function using Kwin, and asking me to hit CRTL ALT F12 to restart them. Which would get me nowhere. I tried disabling functionality checks, getting the message: 

 > Failed to activate desktop effects using the given configuration options. Settings will be reverted to their previous values.

Check your X configuration. You may also consider changing advanced options, especially changing the compositing type.Change the compositioning type I did, to Xrender, but when I restarted there was no way to get them back to OpenGl, lol. Running 'kwin --replace' got me this output: 
```
OpenGL vendor string:                   X.Org
OpenGL renderer string:                 Gallium 0.4 on AMD RS880
OpenGL version string:                  2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
Driver:                                 R600G
GPU class:                              R600
OpenGL version:                         2.1
GLSL version:                           1.20
Mesa version:                           7.10.2
X server version:                       1.10
Linux kernel version:                   2.6.38
Direct rendering:                       yes
Requires strict binding:                yes
GLSL shaders:                           yes
Texture NPOT support:                   yes
kwin(1806) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_glide"  is not supported 
kwin(1806) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_magiclamp"  is not supported 
kwin(1806) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_blur"  is not supported 
kwin(1806) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_wobblywindows"  is not supported 
kwin(1806) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_startupfeedback"  is not supported , 
kwin(1806) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_cube"  is not supported 
kwin(1806) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_screenshot"  is not supported 
kwin(1806) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_cubeslide"  is not supported 
kwin(1806) KWin::EffectsHandlerImpl::loadEffect: EffectsHandler::loadEffect : Effect  "kwin4_effect_coverswitch"  is not supported 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/mreto/.config/ibus/bus

```Now, I got the matter "sorted out", kind of, by reinstalling Kwin, and renaming my ~/.kde folder, but I wonder what this might be, and when I'll get the same kind of hassle. Anybody had these problems or might know what's going on? Should I file a bug report? I don't think this is necessarily Ubuntu related, because I've seen older threads on the OpenSuse forums complaining about the same issues.

---

### Post by el_koraco on 2011-04-19
bump?

---

### Post by Zorael on 2011-04-19
Perhaps your videocard and/or driver version has been blacklisted? Check the definitions in **~/.kde/share/config/kwinrc** (the **[Blacklist]** sections) and compare them to your card.

```
$ **cat ~/.kde/share/config/kwinrc | grep -A5 "\[Blacklist\]"**
[**Blacklist**][Blur]
**[COLOR="Red"]Advanced Micro Devices=DRI R600:-:7.8.1,DRI R600:-:7.8.2[/COLOR]**
Ati=Radeon HD 3650:-:3.3.9901
NVIDIA=GeForce 6150/PCI/SSE2:-:195

[**Blacklist**][Lanczos]
**[COLOR="red"]Advanced Micro Devices=DRI R600:-:7.8.1,DRI R600:-:7.8.2[/COLOR]**
Intel=GM45 Express Chipset GEM 20100328:-:7.8.2,GM45 Express Chipset GEM 20091221:-:7.7.1,965GM GEM 20100328 2010Q1:-:7.8.2,965GM GEM 20091221 2009Q4:-:7.7.1,Ironlake Mobile GEM 20100328:-:7.8.2

[Compositing]
AnimationSpeed=

$ **echo "`glxinfo | grep 'OpenGL renderer string' | sed -e 's/^.*: //'`:-:`glxinfo | grep 'OpenGL version string' | sed -e 's/^.*: //'`"**
**[COLOR="Green"]GeForce GTX 580/PCI/SSE2:-:4.1.0 NVIDIA 270.41.03[/COLOR]**
```

It may also be that it's a whole new bug exposed by driver upgrades, and as such needs [reporting](https://bugs.kde.org). You can also try [**#kde** on Freenode](irc://irc.freenode.net/kde).

Remember; unreported bugs can only be fixed by accident.

---

### Post by el_koraco on 2011-04-20
Nope, not for the moment at least. I'll check it out if the problem appears again. As to whether it's a bug or not, that's the main reason for the thread. I don't wanna report it as a bug if it's not. Thanks for the info, I'll get back on it if the problem reappears.

---

