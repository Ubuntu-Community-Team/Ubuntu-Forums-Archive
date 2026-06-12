---
title: "Quake Wars Patch 1.2"
date: 2008-01-04
forum: Gaming &amp; Leisure
---

### Post by SidewinderPro2 on 2008-01-04
I have just downloaded the 1.2 patch for Linux for Enemy Territory Quake Wars. I have managed to get the installer running, and it looks exactly like the original installer. Its asking me to insert the DVD again. Is this normal or am I doing something wrong and its trying to reinstall the game?

I did this to get it going:

```
chmod +x ETQW-client-1.2-full.r5.x86.run
./ETQW-client-1.2-full.r5.x86.run
```


As I am new to Linux, I basically substituted in the file name with the original installer client, so I am not sure if I did it right.

Anyone who has patched it, please help. I love this game. I bought it the day it came out for Windows and I have been playing ever since. Now I want it to work on my Ubuntu drive, so any help here would be greatly appreciated.

---

### Post by BreathEasy on 2008-01-04
There are two types of installers for ETQW - the **full** and the **nomedia** versions. You're trying to install the full client, which is designed for installations from scratch and as such, expects the DVD so it can copy files to a new game installation. I think you can still use it like a normal patch though. The nomedia version just copies the updated files, but not the media from the DVD, which makes it easier to use as a patch.

That's why the "patch" you ran looked exactly like the original installer - it is! Just with the 1.2 updates. I recommend just going ahead and installing over the top. If you ever uninstall the game and want to reinstall, run that 1.2 installer you've got there, and it'll do the rest.

---

### Post by SidewinderPro2 on 2008-01-04
Interesing. I am not waiting for another 250 meg download, so here we go again. 

Reinstaller for the future, I'm not so sure about that. If it gives me a lot of problems I will just hit the restart button and boot into Necrosoft Vista and play the game. Only game that doesn't crash in Vista. iD makes a wicked good product.

---

### Post by Sockerdrickan on 2008-01-04
There will be a 1.4 patch / demo this week

---

### Post by SidewinderPro2 on 2008-01-05
Where did 1.3 go? Did I miss something? I finally got the thing going on Linux. I went through the patch client and it ended up uninstalling the game. I did it over again and now the thing is all set. 

One problem though. My 360 controller will not work. I installed the Xpad360 drivers and then did the Xpad-fix update. The controller doesn't even flash now. Is there any way to get this thing running? I hate using a mouse and keyboard for a shooting game, or almost any game for that matter.

---

### Post by w0rt3x on 2008-01-05
I know this is not exactly to the topic, but ill ask a probably quick question:
What to do if the file is in my Desktop, I do this:

tomas@Unix:~/Desktop$ chmod +x ETQW-client-1.2-full.r5.x86.run
tomas@Unix:~/Desktop$ ./ETQW-client-1.2-full.r5.x86.run
bash: ./ETQW-client-1.2-full.r5.x86.run: cannot execute binary file

Why doesn't it work?

---

### Post by Sockerdrickan on 2008-01-05
Try this
sh ETQW-client-1.2-full.r5.x86.run

---

### Post by w0rt3x on 2008-01-06
I dunno why is it like this, but that doesn't work too :|

tomas@Unix:~/Desktop$ sudo sh ETQW-client-1.2-full.r5.x86.run
ETQW-client-1.2-full.r5.x86.run: 1: Syntax error: word unexpected (expecting ")")

---

### Post by BreathEasy on 2008-01-06
Just as a guess, are you running the 64-bit version of Ubuntu by any chance? If so you'll need the 32-bit compatability libs, otherwise I'm not so sure what's going on here. Could be a stuffed download.

---

### Post by w0rt3x on 2008-01-06
Well, my processor CAN emulate 64 bit, but I'm pretty sure I picked the normal 32 bit release ( I could also check if someone would tell me a command).

Hmm... I guess its rly possible the download is bad, since I downloaded it with windows, then copied to Linux. Plenty of space to stuff up :)

Ill try to download once more.

---

### Post by w0rt3x on 2008-01-06
Ok, got it to work with my user (the other user wasn't mine) and a fresh download. Thanks guys.

---

### Post by Sockerdrickan on 2008-01-06
Great have fun

---

