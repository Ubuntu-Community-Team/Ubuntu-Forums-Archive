---
title: "Unreal Tournament 2004"
date: 2006-09-08
forum: Gaming &amp; Leisure
---

### Post by neoclaw on 2006-09-08
I just installed Ubuntu Dapper Drake, with Unreal Tournament 2004. Everything works fine ingame.. but! There is no text on the screen ingame or HUD. 
Any who can help me fixing this?

---

### Post by Rhubarb on 2006-09-08
It could be your video drivers?
If you've got an nVidia card there, type in nvidia-settings in the terminal, and mess around with the opengl settings.
I could be wrong here btw.

I just tried to install UT2004 last night, but it claimed it was missing some files after install (and patch).  Was working fine for me a few weeks ago on a different install of Ubuntu.

---

### Post by neoclaw on 2006-09-08
I got a Nvidia Card, and i'm using nvidia-glx drivers. Any alternative driver for nvidia cards?

---

### Post by Perfect Storm on 2006-09-08
Installing the patch might do the trick. Go for Ut2004 megapack which contains the latest patch plus alot of bonus stuff.

---

### Post by Scunizi on 2006-09-11
I'm running the nvidia drivers but I'm also using a dual monitor setup w/ xinerama.  When I try to run the game I get the following error.

mark@mark-desktop:~/ut2004$ sh ut2004
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  78 (X_CreateColormap)
  Value in failed request:  0x3a00001
  Serial number of failed request:  58
  Current serial number in output stream:  63

I'm sure this has something to do with the dual monitor setup so I tried CTRL-ALT-F2 to get to a different session without any graphics and monitors that were mirrored.  I still had issues.  Any thoughts,help etc? It's always been a pain trying to get a game running that requires full screen access.  American Army is the same.

---

### Post by perfran on 2007-09-02
Is your desktop resolution the same than the game resolution? If it's not the case try to set the same resolution everywhere.
I had the same error because my desktop was in 1152 and the game in 1280
I hope this'll help :)

---

### Post by Quid on 2007-09-23
I installed it and had no problems .. 
BUT 
After about 30 mins of game play 
*poof*

UT2004 Exits without so much as a "By your leave"!

Looks like something my wife would install - we all know you are just getting warmed up after 30 mins!! :)

Any idea where to look for error logs?

Thanks...
And thanks for the tip on the megapack...

Quid

---

### Post by Quid on 2007-10-08
In reply to my post... I did a little research.

Seems I needed to update my UT2004 with  a patch...

Got that at the Unreal site. NOTE you need to make sure you are using the right bin.

There is a 64 bit bin in the patch. So I edited the script to use it... 

Of course it didn't work - I needed to make it executable with chmod and put it in thr right directory...

voila - it worked - and in the last few hours  - no crashes...
I do note that the the servers still think it is not updated to a internet interactive level as the Windows version is a higher rev version - -any suggestions on that ?

---

### Post by Cappy on 2007-10-08
you need the newest patch:
[http://www.gamershell.com/download_11985.shtml](http://www.gamershell.com/download_11985.shtml)

---

### Post by Quid on 2007-10-08
Thanks - Cappy 
That did the trick!

---

