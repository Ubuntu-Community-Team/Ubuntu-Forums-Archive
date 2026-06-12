---
title: "Unity won't start after login"
date: 2013-04-10
forum: Desktop Environments
---

### Post by dipiscingelit on 2013-04-10
Hi, I'm having some troubles getting unity working again.. this problem came after I installed ubuntu updates and removing some repositories (gwibber-daily and some google chrome repos), then I restarted my system, typed the login normaly and then I just get my wallpaper and cursor, I can't select anything or access to right-click menu, I just can open the console (ctrl+alt+t) and control the volume (volume notification appears). Before I opened this thread, I've been searching around the web and I tryed several solutions like installing compizconfig(ccsm) and select unity plugin, restart compiz and unity, etc but nothing solves my problem.. I also reinstalled unity and it didn't work too. When I type on console the command **setsid unity** to restart unity I get this output:

```
daniel@daniel-pc:~$ setsid unity
daniel@daniel-pc:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
**unity-panel-service: nenhum processo localizado** (translate: no process located)
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
[B]libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.[/B]
**compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).**
compiz (core) - Info: Starting plugin: opengl
[B]libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.[/B]
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
**compiz (expo) - Warn: failed to bind image to texture**
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
**compiz (unityshell) - Error: GL_ARB_vertex_buffer_object not supported**

[B]compiz (core) - Error: Plugin initScreen failed: unityshell
compiz (core) - Error: Failed to start plugin: unityshell
compiz (core) - Info: Unloading plugin: unityshell
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x2600162
  Serial number of failed request:  9390
  Current serial number in output stream:  9396[/B]


```

I'm not a real expert, but I can see there are some errors that don't let unity start.. My question is, what can I do to get my normal desktop again? Since steam for linux have been released I've formated my old windowsucks partition and installed a fresh new ubuntu environment and I liked it, it's fast, beauty but this unstable situations sucks, in a moment is everything ok and then this :/ Sorry for my bad english but I'm a portuguese guy who need to practise his english :)

Thanks in advance

---

### Post by JeanT on 2013-04-10
I had exactly the same issue.

I followed what was said here and it fixed my problem: [http://askubuntu.com/a/192670](http://askubuntu.com/a/192670)

I have an ATI graphic card as well. HD 7970.


Hope it helps.

---

### Post by stinkeye on 2013-04-10
Looks like a gfx hardware/driver issue.

Info from these two commands will help.
```
lspci -k | grep -A3 VGA
```
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by dipiscingelit on 2013-04-11
> **JeanT said:**
> I had exactly the same issue.

I followed what was said here and it fixed my problem: [http://askubuntu.com/a/192670](http://askubuntu.com/a/192670)

I have an ATI graphic card as well. HD 7970.


Hope it helps.

Sorry but i've already tried that solution with no results..

> **stinkeye said:**
> Looks like a gfx hardware/driver issue.

Info from these two commands will help.
```
lspci -k | grep -A3 VGA
```
```
/usr/lib/nux/unity_support_test -p
```

Maybe, i've catalyst control center installed manualy, in the additional drivers menu says that but on synaptic says fglrx and fglrx-updates are not installed..

here are the results of the first command:

```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Juniper [Radeon HD 5700 Series]
    Subsystem: Giga-byte Technology Device 21d7
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

```

and the second one:

```
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5700 Series
OpenGL version string:  1.4 (2.1 (4.2.12171 Compatibility Profile Context 12.10.17))

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  no
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no


```

thanks for the help

---

### Post by dipiscingelit on 2013-04-12
problem solved, formated a new installation of ubuntu. thanks anyway

---

