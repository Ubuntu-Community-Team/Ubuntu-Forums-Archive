---
title: "GoogleEarth under wine?"
date: 2005-12-16
forum: Desktop Environments
---

### Post by rainbowjoshua on 2005-12-16
So, I'm sorry if this is the wrong forum for such a question, since I'm running the wine package directly from the winehq depository, and I don't think it's anywhere in universe or multiverse, but it installed easily using Synaptic, and the GoogleEarth install program ran (with one windows error about a missing dll, but it installed anyway), and when I try to run the GoogleEarth executable via:

```
cd /home/joshua/.wine/drive_c/Program\ Files/Google/Google\ Earth/
./GoogleEarth.exe &
```

What I get is:

```
fixme:atl:AtlModuleInit SEMI-STUB (0x466920 0x4658f0 0x400000)
fixme:imm:ImmGetContext (0x10020): stub
fixme:imm:ImmReleaseContext (0x10020, 0x7fddfb98): stub
fixme:imm:ImmGetContext (0x10020): stub
fixme:imm:ImmReleaseContext (0x10020, 0x7fddfb98): stub
fixme:imm:ImmGetContext (0x10024): stub
fixme:imm:ImmReleaseContext (0x10024, 0x7fddfb98): stub
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpWithHandleData
fixme:dbghelp:MiniDumpWriteDump NIY MiniDumpFilterMemory

[1]+  Exit 255                wine ./GoogleEarth.exe

```
And no application.  Anyone have any ideas, did I miss something that needs to be installed for wine?  All help is much appreciated!  Thank you!  :)

---

### Post by sjh on 2005-12-16
Disreguard, I read the post wrong.

sorry
SJH

---

### Post by sup on 2006-01-15
see this: [https://wiki.ubuntu.com/GoogleEarth?highlight=%28google%29]("https://wiki.ubuntu.com/GoogleEarth?highlight=%28google%29")

---

### Post by Delp on 2006-01-26
I have the same exact output, i get the program for a cuople of seconds and then... it disapear.

Any sugestion??

Thanks.

PS: i followed exactly the wiki page about google earth, and tried all the problems which appear.

---

