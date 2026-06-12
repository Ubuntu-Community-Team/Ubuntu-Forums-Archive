---
title: "how do I start HFS running in WINE?"
date: 2010-04-26
forum: Desktop Environments
---

### Post by spelingchampeon on 2010-04-26
I installed HFS-HTTP (a Windows program) a week ago, and use it with WINE. Everything seems to be ok (a couple of oddities now and again, but very stable)...however, I would like to have HFS run automatically during bootup. I associated HFS with WINE, so just clicking the hfs.exe file, the program opens with WINE, but I can not get the program to startup on its own. 

I went to SESSIONS and added 'hfs.exe' to the the startup, but no luck. 

Any help would be appreciated. Thanks

---

### Post by SnickerSnack on 2010-04-27
1) Locate the exe in the linux filesystem, something like /home/[user]/.wine/drive_c/Program\ Files/hfs/hfs.exe

2) System>Preferences>Startup Applications, Click "Add"

3) Put ```
wine /home/[user]/.wine/drive_c/Program\ Files/hfs/hfs.exe
``` in the "Command" field.  Fill in other fields.

That should do it.  Maybe not though, I've never run wine at startup, so there may be a problem with that.

GL,
Zach

---

### Post by spelingchampeon on 2010-04-30
I copied and pasted your suggestion (changed the USER of course), and rebooted 2 times, no go. As for filling in the other fields, I just did more of a description.. there was nothing else that I could think of filling in. 
Thanks for trying though, I appreciate it!

Anyone else?

---

### Post by spelingchampeon on 2010-04-30
If I understand what your asking.. does HFS work in Ubuntu, the answer so far for me is YES. The program doesnt install like a regular program, you just extract it into a folder, and use WINE to open it up. 

What I did was to 'install' HFS into a folder. Then downloaded and installed WINE via Synaptic. I then went to the HFS.EXE file and right clicked "open with WINE" and set HFS up with no problems (except for starting up HFS during boot). 

I've been able to log in remotely and d/l and u/l files with no issues so far. Its been very stable from what I've seen so far.

---

