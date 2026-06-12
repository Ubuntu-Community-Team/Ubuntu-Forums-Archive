---
title: "Installs fine. Then Doesn't run."
date: 2007-07-28
forum: Gaming &amp; Leisure
---

### Post by LinuxNewb51 on 2007-07-28
I have installed several games such as Starcraft, Warcraft, and more and they all do the same thing. They install fine but when I try to run it the wine desktop appears stays on a while then shuts off. It happens on every one of them. I think it's a simple problem i just don't know what I've done wrong.

Can anyone help? thx in advance.

---

### Post by cogadh on 2007-07-28
What are your winecfg settings?
What messages, if any, are produced in the terminal when the games fail?
Have you checked on [Wine's AppDB]("http://appdb.winehq.org/") for any specific configurations required by the games you are trying to run?
How are you running the games (i.e. what are entering into the terminal)?

Let's just start with that and move from there...

---

### Post by LinuxNewb51 on 2007-07-28
I'm not running it from the terminal. I run it from the applications menu. Should I?

---

### Post by cogadh on 2007-07-28
Until you have a game running smoothly, you really should use the terminal to launch it. If Wine produces any error messages, they can only be seen in the terminal window. Once you have the game running correctly, then using the menu shortcuts is usually fine.

What about the other questions?

---

### Post by LinuxNewb51 on 2007-07-28
I can't seem to get it to run in the terminal because it can't find the file. where should I put it? And there are no special configurations on the wine site. And what settings do you need to know? or what settings should I put?



EDIT:
I now got it to do something in the terminal and it came up with this:

err:module:import_dll Library Storm.dll (which is needed by L"C:\\windows\\system32\\WarcraftIIBNE.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\WarcraftIIBNE.exe" failed, status c0000135

---

### Post by cogadh on 2007-07-28
Open your home folder in the file browser and hit CTRL+H to show hidden files. Look for the .wine/drive_c directory and open it. At this point, the file directory structure will start to look like Windows (i.e. a Windows and Program Files directory). Go into Program Files and look for where the game is installed. Then do this in the terminal:
```
 cd $HOME/.wine/drive_c/Program\ Files/gamedirectory
```
If the game directory has any spaces in its name, put in a backslash like I did with "Program\ Files"
Next, run this to launch the game:
```
wine game.exe
```
Obviously, change the "game.exe" to match your game's executable. The game should now launch and if it doesn't, the errors associated with it will appear in the terminal.

As for your settings, click on the "Stuff I've learned about Wine" link in my signature. It leads to a post I wrote that will help you get Wine set up with a basic working configuration and may answer many other Wine questions you might have. 

Post back with any results you get.

---

### Post by LinuxNewb51 on 2007-07-28
scratch that

this is what it's doing

main/renderbuffer.c:2041: _mesa_add_renderbuffer: Assertion `bufferName == BUFFER_DEPTH || bufferName == BUFFER_STENCIL || fb->Attachment[bufferName].Renderbuffer == ((void *)0)' failed.
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...
Unhandled exception: assertion failed in 32-bit code (0xffffe410).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:ffffe410 ESP:0033e9f4 EBP:0033ea0c EFLAGS:00200202(   - 00      - - I1)
 EAX:00000000 EBX:00001ab9 ECX:00001ab9 EDX:00000006
 ESI:0033eaac EDI:b7e4dff4
Stack dump:
0x0033e9f4:  0033ea0c 00000006 00001ab9 b7d3adf0
0x0033ea04:  b7e4dff4 b7d0c6c0 0033eb38 b7d3c641
0x0033ea14:  00000006 0033eaac 00000000 00000130
0x0033ea24:  7c229dc0 00000000 00000000 b7d75dfd
0x0033ea34:  0033ea70 7c229d58 7c229dbc 0033eb48
0x0033ea44:  b7e4dff4 000000bb 000000bc 0033eb1c
Backtrace:
=>1 0xffffe410 (0x0033ea0c)
  2 0xb7d3c641 abort+0x101() in libc.so.6 (0x0033eb38)
  3 0xb7d3443b __assert_fail+0xfb() in libc.so.6 (0x0033eb7c)
  4 0x7e26ab9b _mesa_add_renderbuffer+0x13b() in unichrome_dri.so (0x0033eb9c)
  5 0x7e204c75 in unichrome_dri.so (+0x5bc75) (0x0033ebcc)
  6 0x7e20555a viaMakeCurrent+0x1ba() in unichrome_dri.so (0x0033ebfc)
  7 0x7e201859 in unichrome_dri.so (+0x58859) (0x0033ec3c)
  8 0x7e40c0ce glXMakeContextCurrent+0xbe() in libgl.so.1 (0x0033ecac)
  9 0x7e40c3b3 glXMakeCurrent+0x23() in libgl.so.1 (0x0033eccc)
  10 0x77566a40 in wined3d (+0x36a40) (0x0033ed9c)
  11 0x775680ea IWineD3DImpl_FillGLCaps+0x3a() in wined3d (0x0033ef3c)
  12 0x7756b75d InitAdapters+0x16d() in wined3d (0x0033ef7c)
  13 0x775c918f WineDirect3DCreate+0x1f() in wined3d (0x0033efac)
  14 0x7b98b293 in ddraw (+0x2b293) (0x0033f01c)
  15 0x7b98b942 DirectDrawCreate+0x102() in ddraw (0x0033f06c)
  16 0x0048a40d in warii (+0x8a40d) (0x0033fd10)
  17 0x004284b8 in warii (+0x284b8) (0x7edea380)
  18 0x7d8938ec (0x83e58955)
  19 0x00000000 (0x00000000)
0xffffe410: popl        %ebp
Modules:
Module  Address                 Debug info      Name (89 modules)
PE        400000-  4d8000       Export          warii
PE       2000000- 200f000       Deferred        w2local
PE      15000000-1503b000       Deferred        storm
ELF     774a4000-77524000       Deferred        libglu.so.1
ELF     77524000-775ef000       Export          wined3d<elf>
  \-PE  77530000-775ef000       \               wined3d
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7b95a000-7b9af000       Export          ddraw<elf>
  \-PE  7b960000-7b9af000       \               ddraw
ELF     7b9af000-7ba00000       Deferred        libgcrypt.so.11
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bcd2000-7bd00000       Deferred        libcrypt.so.1
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7bf06000-7bf76000       Deferred        libgnutls.so.13
ELF     7bf76000-7bfa7000       Deferred        libcups.so.2
ELF     7bfa7000-7c000000       Deferred        rpcrt4<elf>
  \-PE  7bfb0000-7c000000       \               rpcrt4
ELF     7c22a000-7c23f000       Deferred        libtasn1.so.3
ELF     7c276000-7c315000       Deferred        ole32<elf>
  \-PE  7c290000-7c315000       \               ole32
ELF     7c316000-7c31a000       Deferred        libgpg-error.so.0
ELF     7c331000-7c363000       Deferred        uxtheme<elf>
  \-PE  7c340000-7c363000       \               uxtheme
ELF     7c365000-7c36a000       Deferred        libxfixes.so.3
ELF     7c36a000-7c373000       Deferred        libxcursor.so.1
ELF     7c373000-7c390000       Deferred        imm32<elf>
  \-PE  7c380000-7c390000       \               imm32
ELF     7c390000-7c396000       Deferred        libxrandr.so.2
ELF     7c396000-7c39e000       Deferred        libxrender.so.1
ELF     7e1a9000-7e3e1000       Export          unichrome_dri.so
ELF     7e3e1000-7e3ea000       Deferred        libdrm.so.2
ELF     7e3ea000-7e44a000       Export          libgl.so.1
ELF     7e44a000-7e44f000       Deferred        libxdmcp.so.6
ELF     7e44f000-7e452000       Deferred        libxau.so.6
ELF     7e452000-7e543000       Deferred        libx11.so.6
ELF     7e543000-7e551000       Deferred        libxext.so.6
ELF     7e551000-7e556000       Deferred        libxxf86vm.so.1
ELF     7e556000-7e56e000       Deferred        libice.so.6
ELF     7e56e000-7e577000       Deferred        libsm.so.6
ELF     7e577000-7e600000       Deferred        winex11<elf>
  \-PE  7e590000-7e600000       \               winex11
ELF     7e679000-7e699000       Deferred        libexpat.so.1
ELF     7e699000-7e6c4000       Deferred        libfontconfig.so.1
ELF     7e6c4000-7e6d8000       Deferred        libz.so.1
ELF     7e6d8000-7e743000       Deferred        libfreetype.so.6
ELF     7e743000-7e756000       Deferred        libresolv.so.2
ELF     7e756000-7e774000       Deferred        iphlpapi<elf>
  \-PE  7e760000-7e774000       \               iphlpapi
ELF     7e774000-7e7a1000       Deferred        ws2_32<elf>
  \-PE  7e780000-7e7a1000       \               ws2_32
ELF     7e7a1000-7e7bb000       Deferred        wsock32<elf>
  \-PE  7e7b0000-7e7bb000       \               wsock32
ELF     7e7bb000-7e822000       Deferred        msvcrt<elf>
  \-PE  7e7d0000-7e822000       \               msvcrt
ELF     7e822000-7e83c000       Deferred        crtdll<elf>
  \-PE  7e830000-7e83c000       \               crtdll
ELF     7e83c000-7e850000       Deferred        lz32<elf>
  \-PE  7e840000-7e850000       \               lz32
ELF     7e850000-7e86a000       Deferred        version<elf>
  \-PE  7e860000-7e86a000       \               version
ELF     7e86a000-7e89d000       Deferred        winspool<elf>
  \-PE  7e870000-7e89d000       \               winspool
ELF     7e89d000-7e95a000       Deferred        comctl32<elf>
  \-PE  7e8b0000-7e95a000       \               comctl32
ELF     7e95a000-7e9b3000       Deferred        shlwapi<elf>
  \-PE  7e970000-7e9b3000       \               shlwapi
ELF     7e9b3000-7eab1000       Deferred        shell32<elf>
  \-PE  7e9c0000-7eab1000       \               shell32
ELF     7eab1000-7eb52000       Deferred        comdlg32<elf>
  \-PE  7eac0000-7eb52000       \               comdlg32
ELF     7eb52000-7eb9a000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb9a000       \               advapi32
ELF     7eb9a000-7eba6000       Deferred        libgcc_s.so.1
ELF     7ec9a000-7ed5a000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed5a000       \               gdi32
ELF     7ed5a000-7ee97000       Deferred        user32<elf>
  \-PE  7ed80000-7ee97000       \               user32
ELF     7efad000-7efb8000       Deferred        libnss_files.so.2
ELF     7efb8000-7efcf000       Deferred        libnsl.so.1
ELF     7efcf000-7eff6000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d03000-b7d0c000       Deferred        libnss_compat.so.2
ELF     b7d0d000-b7d11000       Deferred        libdl.so.2
ELF     b7d11000-b7e52000       Export          libc.so.6
ELF     b7e53000-b7e6a000       Deferred        libpthread.so.0
ELF     b7e74000-b7f88000       Deferred        libwine.so.1
ELF     b7f8a000-b7fa5000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\WarII\warii.exe
        0000000d    1
        00000009    0 <==

---

### Post by LinuxNewb51 on 2007-07-29
okay can anyone help me with this?

---

### Post by buttons on 2007-07-29
> **LinuxNewb51 said:**
> okay can anyone help me with this?

Silly question: Do you have direct rendering working?

```
glxinfo | grep direct
```

Type that in a terminal.  You should see something like this:
> direct rendering: **Yes**
The helpful bit is that Yes there.  If it's a no, please see the Binary Driver Howto [here]("https://help.ubuntu.com/community/BinaryDriverHowto").

---

### Post by kernalsanders123 on 2007-09-06
Hello all, kind of new here to the forum, and linux in general, so sorry if i can't provide any solutions. I do have a similar problem though, i can install wine just fine, but whenever I try to run an application, though, it usually errors out. Oddly enough, eMule runs fine via wine, but other programs don't. For example, when I try to run Frets on FIre via wine, the terminal spits this out at me:

err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x188f98) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1773b0)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1773b0)->((nil),00000008)

p.s.: sorry if I didn't format the code correctly, I'm pretty much a n00b at Linux and forums, but if anyone would care to fill me in as to properly inserting code into a reply so I don't screw it up again, that' be a big help, thanks!

---

### Post by cogadh on 2007-09-06
First off, why are you trying to run FoF in Wine? There is a Linux native client.

Second, those errors would seem to indicate that you do not have the 3D accellerated driver for your video card installed. What kind of video card do you have?

Thirdly, you can pretty much ignore any "fixme" messages from Wine. 9 times out of 10, they are just developer messages and notes that actually mean nothing to an end user. They are just there to remind the developers of what they still have left to work on.

---

### Post by kernalsanders123 on 2007-09-07
When I try to run Frets on Fire in linux, the terminal gives me this:

```
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 189, in __init__
    self.data = Data(self.resource, self.svg)
  File "/usr/share/games/fretsonfire/game/Data.py", line 48, in __init__
    self.loadSvgDrawing(self, "star1",   "star1.svg", textureSize = (128, 128))
  File "/usr/share/games/fretsonfire/game/Data.py", line 106, in loadSvgDrawing
    drawing  = self.resource.load(target, name, lambda: SvgDrawing(self.svg, fileName), synch = True)
  File "/usr/share/games/fretsonfire/game/Resource.py", line 157, in load
    return l.finish()
  File "/usr/share/games/fretsonfire/game/Resource.py", line 68, in load
    self.result = self.function()
  File "/usr/share/games/fretsonfire/game/Data.py", line 106, in <lambda>
    drawing  = self.resource.load(target, name, lambda: SvgDrawing(self.svg, fileName), synch = True)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 543, in __init__
    self.texture = Texture(bitmapFile)
  File "/usr/share/games/fretsonfire/game/Texture.py", line 202, in __init__
    self.loadFile(name)
  File "/usr/share/games/fretsonfire/game/Texture.py", line 206, in loadFile
    self.loadImage(Image.open(name))
  File "/usr/share/games/fretsonfire/game/Texture.py", line 214, in loadImage
    self.loadRaw(image.size, string, GL_RGBA, 4)
  File "/usr/share/games/fretsonfire/game/Texture.py", line 281, in loadRaw
    gluBuild2DMipmaps(self.glTarget, components, w, h, format, GL_UNSIGNED_BYTE, string)
OpenGL.GLU.GLUerror: [Errno 100901] invalid value

```

I believe that this has something to due to to my lack of amanith on my computer, which I tried installing, but frankly I could not make heads or tails of the instructions. However, this is probably another issue for another forum.

As for video card drivers, I downloaded and installed the drivers from ATI, which are listed under the restricted drives manager as the ATI accelerated graphics driver, and is listed as being enabled and in use.

As for the fixme messages, that clears up quite a bit, Thanks!

---

