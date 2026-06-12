---
title: "problems with wine and cs 1.6"
date: 2006-03-27
forum: Gaming &amp; Leisure
---

### Post by syklitengutt on 2006-03-27
When I try to open cs I can get in, but under some actions It freezes.
Some exaples:
browsing settings, trying to start a game, trying to browse 
servers.

I have actually never managed to play cs.
I think the problem is at steam, because where it should me an X and -
to close and minimize its nothing and when I try to minimize it freezes.
The button to the left.

Actually my whole computer freeze.
I have to press cntl alt backspace and log in again.

I use ubuntu 5.10 up to date, and I use the newest wine.
Anyone got any ideas?

---

### Post by shinygerbil on 2006-03-27
What kernel are you using?

The default kernel which comes with Breezy is version 2.6.12, which has problems with CS1.6 etc. I upgraded to 2.6.16 (which has not long come out) and it solved the random hangs.

The trouble is, upgrading your kernel is not a simple matter. You might want to try an earlier version of Wine - the latest version is 0.9.10, but apparently version 0.9.6 is the best version to use; later versions have OpenGL issues. This is the version I use, but it didn't solve my problem, so I still had to upgrade my kernel.

](*,)

There are some threads about kernel upgrading around - try the following thread:

[http://ubuntuforums.org/showthread.php?t=84174](http://ubuntuforums.org/showthread.php?t=84174)

but wherever it says 2.6.14, replace with 2.6.16 for the latest kernel, although both work. :)

Hope this post isn't too confusing ;)

Steve

---

### Post by syklitengutt on 2006-03-28
ok... I tried this, and have some difficulties. 
My hdb cant be mounted and I have a black screen until I get the loginscreen.
But over to cs. Now it starts with grafics as software and if I change to opengl
I get first this error:
ChoosePixelformatfailed
and when I press ok I get this error:
The spesified video mode is not supported.
The game will now run in software mode.
And then it messes up my screenresolution and quit cs.
this is what terminal sais:

> chris@chris:~/.wine/drive_c/Program Files/Steam1$ WINEDEBUG="-all" wine steam.exe -applaunch 10
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
Win32 MiniDump Helper version 1.0.0.0 (c) Copyright 2000-2003 Valve CorporationAll rights reserved.

Expected argument 'ProcessId'.

Usage: WriteMiniDump [@argfile] [/?|h|help] [/v|version] [/Type <value>] <ProcessId> <DumpFile>

@argfile        Read arguments from a file.
/?              Show usage.
/v              Show version.
/Type <value>   Select dump type values are:
                   normal
                   full
ProcessId       Select process id for which to generate a dump
DumpFile        Select path of output dump file

wine: Call from 0x7fc12410 to unimplemented function dbghelp.dll.SymGetSymFromAddr64, aborting



---

### Post by shinygerbil on 2006-03-28
If you visit the following page:

[http://ubuntuforums.org/showthread.php?t=138650](http://ubuntuforums.org/showthread.php?t=138650)

I found it very useful. (Much more useful than I have been ;) ) Basically, you need to reinstall your graphics drivers after upgrading your kernel. Also, the kubuntu-evms patch this page links to will hopefully fix your hard drive problem. Trouble is, you'll need to recompile the kernel... :/ I can't help with the black screen, I've just left mine as it is now, i hardly ever turn my computer off anyway! :-?

---

### Post by syklitengutt on 2006-03-29
I downgraded to 0.9.6...
Got it working with some small hangups.
Downgraded my kernel again.
Thnx!

---

