---
title: "HELP - Getting Prey to Work in Linux"
date: 2006-08-27
forum: Gaming &amp; Leisure
---

### Post by jackkerouac on 2006-08-27
As you can tell from the title, I need a little help getting prey to work in Linux. I have it installed just fine, but when I run it, I get the following error code:

```

1796 MHz AMD CPU with MMX & 3DNow! & SSE & SSE2 & x64
1008 MB System Memory
64 MB Video Memory
Winsock Initialized
Found interface: eth0  - 192.168.0.114/1.0.0.0
Found interface: sit0  - /
Found interface: vmnet1  - 192.168.27.1/1.0.0.0
Found interface: vmnet8  - 172.16.168.1/1.0.0.0
Sys_InitNetworking: adding loopback interface
prey using MMX & SSE & SSE2 for SIMD processing
enabled Flush-To-Zero mode
enabled Denormals-Are-Zero mode
------ Initializing File System ------
Current search path:
H:\/base
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Shutting down OpenGL subsystem
...shutting down QGL
Couldn't load default.cfg

```

Any help would be truly appreciated!

**EDIT:** I tried it with:

```
nice -20 wine prey.exe
```

... and received the following error:

```

Prey 1.0.103 win-x86 Jun 10 2006 00:44:11
1796 MHz AMD CPU with MMX & 3DNow! & SSE & SSE2 & x64
1008 MB System Memory
64 MB Video Memory
Winsock Initialized
Found interface: eth0  - 192.168.0.114/1.0.0.0
Found interface: sit0  - /
Found interface: vmnet1  - 192.168.27.1/1.0.0.0
Found interface: vmnet8  - 172.16.168.1/1.0.0.0
Sys_InitNetworking: adding loopback interface
prey using MMX & SSE & SSE2 for SIMD processing
enabled Flush-To-Zero mode
enabled Denormals-Are-Zero mode
------ Initializing File System ------
Loaded pk4 C:\Program Files\Prey\base\game00.pk4 with checksum 0xe0be2928
Loaded pk4 C:\Program Files\Prey\base\pak000.pk4 with checksum 0x7dc00ede
Loaded pk4 C:\Program Files\Prey\base\pak001.pk4 with checksum 0xd06647b1
Loaded pk4 C:\Program Files\Prey\base\pak002.pk4 with checksum 0x57dce443
Loaded pk4 C:\Program Files\Prey\base\pak003.pk4 with checksum 0x263006fe
Loaded pk4 C:\Program Files\Prey\base\pak004.pk4 with checksum 0xcc075380
Current search path:
C:\Program Files\Prey/base
C:\Program Files\Prey\base\pak004.pk4 (3739 files)
C:\Program Files\Prey\base\pak003.pk4 (4111 files)
C:\Program Files\Prey\base\pak002.pk4 (5337 files)
C:\Program Files\Prey\base\pak001.pk4 (6270 files)
C:\Program Files\Prey\base\pak000.pk4 (3318 files)
C:\Program Files\Prey\base\game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
2647 strings read from strings/english001.lang
Couldn't open journal files
couldn't exec editor.cfg
execing default.cfg
couldn't exec preyconfig.cfg
couldn't exec autoexec.cfg
2647 strings read from strings/english001.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Initializing OpenGL subsystem
...registered window class
...registered fake window class
...initializing QGL
...calling LoadLibrary( 'opengl32' ): succeeded
...calling CDS: ok
...created window @ 0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...PIXELFORMAT 1 selected
...creating GL context: failed
Shutting down OpenGL subsystem
...wglMakeCurrent( NULL, NULL ): success
...releasing DC: failed
...resetting display
...shutting down QGL
...unloading OpenGL DLL
Initializing OpenGL subsystem
...initializing QGL
...calling LoadLibrary( 'opengl32' ): succeeded
...calling CDS: ok
...created window @ 0,0 (640x480)
Initializing OpenGL driver
...getting DC: succeeded
...PIXELFORMAT 1 selected
...creating GL context: failed
Shutting down OpenGL subsystem
...wglMakeCurrent( NULL, NULL ): success
...releasing DC: failed
...resetting display
...shutting down QGL
...unloading OpenGL DLL
idRenderSystem::Shutdown()
Shutting down OpenGL subsystem
...shutting down QGL
Unable to initialize OpenGL

```

---

### Post by GregaS on 2006-08-27
64 MB of video memory? I think you can't play Prey with 64 MB video memory. Even in windows.

---

### Post by jackkerouac on 2006-08-27
I thought that was weird as well.

I have an ATI X700, so I have 256 MBs of RAM. I should mention that it runs great in Windows, with all the details, anti-aliasing, etc. turned up full.

---

### Post by 916 on 2006-08-28
> **GregaS said:**
> 64 MB of video memory? I think you can't play Prey with 64 MB video memory. Even in windows.
He can. My friend played Doom3 on Windows with 32 video memory (on the card). All he did was giving 256 MB of his 2 GB ram to the video card (somehow, I must ask him how did he do it, though)and it ran perfectly (without the shaders, of course)\\:D/

---

### Post by firezip on 2006-08-28
He sohuld of just bought a cheap 6600gt or something. BTW I never heard of allocating system ram to video ram.

---

### Post by Carrots171 on 2006-08-29
> **firezip said:**
> BTW I never heard of allocating system ram to video ram.

For AGP cards it's called the "AGP Aperture". You can adjust it in your BIOS. For low-end Nvidia PCI-Express cards it's called "TurboCache". I don't know about ATI though...

---

### Post by justin whitaker on 2006-08-29
What happens if you run it windowed? I'm thinking it may be a permissions issue: in the first error set, it balked when the system went "vid_restart". 

The second one, it was fine until it tried to init the OpenGL context. It looks like the game bypassed that error, tried another method, came back to it, and hit the same wall. 

Is this a native installer, or wine?

---

