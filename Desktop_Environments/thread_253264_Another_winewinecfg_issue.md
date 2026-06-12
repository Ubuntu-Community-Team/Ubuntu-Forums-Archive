---
title: "Another wine/winecfg issue"
date: 2006-09-08
forum: Desktop Environments
---

### Post by nosmada on 2006-09-08
I'm just going to post what I get from the terminal window:

```
nosmada@nosmada-desktop:~$ winecfg
wine: creating configuration directory '/home/nosmada/.wine'...
fixme:ole:ITypeInfo_fnRelease destroy child objects
wine: Unhandled page fault on read access to 0x00000000 at address 0x7d483b37 (thread 0009), starting debugger...
err:syslevel:_EnterSysLevel (0x7edab040, level 2): Holding 0x7eca2940, level 3. Expect deadlock!
err:syslevel:_EnterSysLevel (0x7edab040, level 2): Holding 0x7eca2940, level 3. Expect deadlock!
err:syslevel:_CheckNotSysLevel Holding lock 0x7eca2940 level 3
err:seh:raise_exception Unhandled exception code 80000003 flags 0 addr 0x7eeb0ae4
wine: wineprefixcreate failed while creating '/home/nosmada/.wine'.
nosmada@nosmada-desktop:~$ wineserver: could not save registry branch to /home/nosmada/.wine-ZlgVea/system.reg : No such file or directory
wineserver: could not save registry branch to /home/nosmada/.wine-ZlgVea/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/nosmada/.wine-ZlgVea/user.reg : No such file or directory
```

I'm a second time noob on Ubuntu I tried 5.10 and gave up and then came back with 6.06 and am running it on two machines. It works fine on the compaq laptop and has problems on the self built desktop. Sorry if I didn't look hard enough and the answer is already out there.

I tried using automatix and am wondering if that caused the problem but I removed it and most of the apps that were installed using it. I've uninstalled and reinstalled 3 times with same fixme error or whatever it is. I tried searching for that but didn't find anything.

Thanks in advance for everyone's help.

---

### Post by BLTicklemonster on 2006-09-08
Wine crashes my desktop when I put in winecfg, if anyone who sees this has any idea, please post.
<hijack hijack hijack>

---

### Post by BLTicklemonster on 2006-09-08
Taken care of. I didn't have some fonts installed that it needed. I went to remove it using synaptic, and I saw something when I right clicked wine that said it was missing them, so I installed them and it worked. 

My bad, sorry about hijacking your thread. Hope you get things worked out.

---

### Post by JNowka on 2006-09-09
This may sound like a stupid question, but did you by any chance run wine to install anything first?  If you didn't, then it has not created the .wine folder in your home folder.  That may help.

---

