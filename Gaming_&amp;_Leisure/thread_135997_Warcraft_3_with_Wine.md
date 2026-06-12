---
title: "Warcraft 3 with Wine"
date: 2006-02-25
forum: Gaming &amp; Leisure
---

### Post by WackToMack on 2006-02-25
Hello everyone.  So, I finally managed to figure out how to use Wine.  My first project with Wine is to get Warcraft 3 installed using the tutorial from Frank's Corner.

> Type wine /pathtocdrom/install.exe to install Warcraft 3.
Download a fixed .exe from [www.megagames.com](www.megagames.com).
Rename War3.exe to War3_orig.exe and Worldedit.exe to Worldedit_orig.exe.
Copy the fixed .exes to the Warcraft directory.
Rename the Movies directory to Movies_orig.

Type wine -- warcraft.exe -opengl in the installation directory to play Warcraft 3.


I managed to get up to this part:

> Type wine -- warcraft.exe -opengl in the installation directory to play Warcraft 3.

But I am stuck here.  I don't know what this step means... and it's the last step of the whole process... lol.  Talk about frustrating... so... anyone know where to type that command or what to do to finally play Warcraft 3?  I've already tried typing this in the Terminal, but I get this error:
  
> wacktomack@Linux:~$ wine -- warcraft.exe -opengl
wine: cannot find '--'

Thanks in advance! :D

---

### Post by Trab on 2006-02-25
ah, it should be...
```

wine warcraft.exe -opengl

```
but you have to do this in the directory where u installed warcraft... so like ~/C/Program File/Warcraft (or wherever it is...)
the -- option was a mistake in the guide i believe...

---

### Post by WackToMack on 2006-02-25
[QUOTE=Trab]ah, it should be...
```

wine warcraft.exe -opengl

```
but you have to do this in the directory where u installed warcraft... so like ~/C/Program File/Warcraft (or wherever it is...)
the -- option was a mistake in the guide i believe...[/QUOTE]

Sorry... forgot to mention that I'm a noob... What do you mean by:

> but you have to do this in the directory where u installed warcraft...

:confused: :confused: :confused: :confused: :confused: :confused: :confused:

What *exactly* do I have to type in the Terminal to get Warcraft to work?

---

### Post by WackToMack on 2006-02-25
OK... I managed to figure out what command to use to run Warcraft:

```
wine "c:\\Program Files\\Warcraft III\\war3_orig.exe" -opengl
```

But when I use that command, I get this error:

> wacktomack@Linux:~$ wine "c:\\Program Files\\Warcraft III\\war3_orig.exe" -opengl
err: ole:CoCreateInstance apartment not initialised
err:virtual:map_image Image was mapped at 0x7d590000: standard load address for a Win32 program (0x00400000) not available
err:virtual:map_image Do you have exec-shield or prelink active?
err:module:import_dll Loading library War3.exe (which is needed by L"C:\\Program Files\\Warcraft III\\Game.dll") failed (error c000007b).

Any ideas???  Thanks in advance!!! :D

---

### Post by SVFUSiON on 2006-02-25
Cedega is much easier :P

---

### Post by Albi on 2006-02-25
try wine .wine/drive_c/Program Files/Warcraft III/war3_orig.exe instead maybe?

---

### Post by Wallakoala on 2006-02-25
I can help up to a certain point on this one.
I see you have war3_orig instead of war3. Did you download the no cd crack and then rename the original to war3_orig? Because if you did not, it is not nessesary to rename it. 
Wine makes a virtual drive c, which is located at /home/yourusernamehere/.wine/drive_c/
If you go into that directory, you are now in the virtual drive c. You can go to program files, and then to Warcraft III and then you will be in the warcraft III directory. You should rename the "Movies" directory to something else, because the movies mess up the game. You can then run ```
wine "Warcraft III.exe" -opengl
```
This should work. I have gotten this game to work under wine.

---

### Post by WackToMack on 2006-02-26
Whew!  I *finally* managed to get Warcraft 3 to work using Wine... But now when I run it and switch over to the terminal, I see all these errors:

> wacktomack@Linux:~$ wine "c:\\Program Files\\Warcraft III\\war3.exe" -opengl
err: ole: CoCreateInstance apartment not initialised
fixme: win: EnumDisplayDevicesW ((null),0,0x7faff4d4,0x00000000), stub!
fixme: win: EnumDisplayDevicesW ((null),0,0x7faff50c,0x00000000), stub!
fixme: sync: CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme: win: EnumDisplayDevicesW ((null),0,0x7fafddb4,0x00000000), stub!
fixme: mm: ImmGetOpenStatus (0x7fdaef88): semi-stub
fixme: imm: ImmReleaseContext (0x10022, 0x7fdaef88): stub
fixme:imm: ImmGetOpenStatus (0x7fdaef88): semi-stub
fixme: imm: ImmReleaseContext (0x10022, 0x7fdaef88): stub
fixme: imm: ImmGetOpenStatus (0x7fdaef88): semi-stub
fixme: imm: ImmReleaseContext (0x10022, 0x7fdaef88): stub
fixme: win: EnumDisplayDevicesW ((null),0,0x7fafcacc,0x00000000), stub!
fixme: win: EnumDisplayDevicesW ((null),0,0x7fafcd84,0x00000000), stub!
fixme: win: EnumDisplayDevicesW ((null),0,0x7fafcfc8,0x00000000), stub!
fixme: win: EnumDisplayDevicesW ((null),0,0x7fafd048,0x00000000), stub!
fixme: wave: OSS_AddRingMessage two fast messages in the queue!!!! toget = 23(WINE_WM_RESTARTING), tosave=26(UNKNOWN(0x00000000))
fixme: wave: OSS_AddRingMessage two fast messages in the queue!!!! toget = 1(WINE_WM_RESTARTING), tosave=3(UNKNOWN(0x00000000))
fixme: wave: OSS_AddRingMessage two fast messages in the queue!!!! toget = 1(WINE_WM_RESTARTING), tosave=3(UNKNOWN(0x00000000))
fixme: wave: OSS_AddRingMessage two fast messages in the queue!!!! toget = 1(WINE_WM_RESTARTING), tosave=3(UNKNOWN(0x00000000))
fixme: wave: OSS_AddRingMessage two fast messages in the queue!!!! toget = 1(WINE_WM_RESTARTING), tosave=3(UNKNOWN(0x00000000))
fixme: wave: OSS_AddRingMessage two fast messages in the queue!!!! toget = 1(WINE_WM_RESTARTING), tosave=3(UNKNOWN(0x00000000))
fixme: wave: OSS_AddRingMessage two fast messages in the queue!!!! toget = 1(WINE_WM_RESTARTING), tosave=3(UNKNOWN(0x00000000))
fixme: wave: OSS_AddRingMessage two fast messages in the queue!!!! toget = 1(WINE_WM_RESTARTING), tosave=3(UNKNOWN(0x00000000))
fixme: wave: OSS_AddRingMessage two fast messages in the queue!!!! toget = 1(WINE_WM_RESTARTING), tosave=3(UNKNOWN(0x00000000))
fixme: imm: ImmGetOpenStatus (0x7fdaef88): semi-stub
fixme: imm: ImmReleaseContext (0x10022, 0x7fdaef88): stub
err: dsound: DSOUND_MixOne underrun on sound buffer 0x7fe030b8
fixme: wave: OSS_AddRingMessage two fast messages in the queue!!!! toget = 61(WINE_WM_RESTARTING), tosave=62(UNKNOWN(0x00000000))
err: dsound: DSOUND_MixOne underrun on sound buffer 0x7fe030b8
err: dsound: DSOUND_MixOne underrun on sound buffer 0x7fe030b8
err: dsound: DSOUND_MixOne underrun on sound buffer 0x7fe030b8
fixme: imm: ImmGetOpenStatus (0x7fdaef88): semi-stub
fixme: imm: ImmReleaseContext (0x10022, 0x7fdaef88): stub


The game runs fine, but it's gonna bug me to know that these errors are popping up and I don't know what they are or how to fix them... Any ideas?
Thanks in advance!!! :D

---

### Post by cdsboy on 2006-02-26
use this command. 
> wine "c:\\Program Files\\Warcraft III\\war3.exe" -opengl : exit
it doesn't acualy fix the bug it just makes it so they won't bother you anymore.

---

