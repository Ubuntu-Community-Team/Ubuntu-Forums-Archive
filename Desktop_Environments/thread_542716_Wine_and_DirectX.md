---
title: "Wine and DirectX"
date: 2007-09-04
forum: Desktop Environments
---

### Post by Denizen08 on 2007-09-04
First off, sorry but I don´t know where to put this... with wine being more of a desktop environment than anything else...

Here's my problem:
I have successfully installed ragnarok using wine but I get an error that it needs higher versions of directx, while the default package already has dx7 I need to install dx9. How do I do this?

From what I've read Wine cant install MS directx redist. and does not do drivers but has its own implementations, so I know wine-install of dx9 wont work. Despite this I know it should be possible since wine has advertised that it CAN run Eve-Online-- a much more visually demanding game.

EDIT1: I use wine 9.5 or the latest in the repository,

---

### Post by Toet on 2007-09-04
You could have a look at WineX from transgaming, but it's commercial I think. They also have Cedega which is definitelly commercial.

---

### Post by Denizen08 on 2007-09-13
OK, I tried using their winecvs.sh script installer to no avail. When installation is being processed I get this error (specifically during checkout stage of installation):

> 
WineCVS.sh - Progress(u) : Green is current

   0 = Uninstall
   1 = Cleanup
   2 = CVS checkout
   3 = Configure
   4 = Make depend
   5 = Make
   6 = Make install
   7 = Finish up

-------------------------------------------

Checking out CVS ... May take a while




--------- Error log - file /home/denizen/.WineCVS/sources/cvswine/ErrorLog : ---------
/home/denizen/.WineCVS/Functions/RunWineCVS: line 736: cvs: command not found


Error in CVS checkout

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


I think I might need to uninstall my current wine version or just do it all over again on a fresh ubuntu install. Are there other wine versions that already has dx8 or dx9 prepackaged?

---

