---
title: "Access Violation when running World of Warcraft under Wine"
date: 2007-02-23
forum: Gaming &amp; Leisure
---

### Post by nouse66 on 2007-02-23
I'm trying to get World of Warcraft running properly in Wine and got everything installed and running but within minutes of logging into the game it crashes because of an access violation.

The error message I get is:
```
This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:7E36F966

The instruction at "0x7E36F966" referenced memory at "0x00000010".
The memory could not be "read".
```

I've noticed that It's always trying to reference that same address: "0x00000010".  I running Wine 0.9.31 and the latest WoW patch (2.0.8) but I've been trying to solve this problem for the last 2 or 3 patch versions (of both WoW and Wine).  I've tried all the howto tips for changing wine settings and the WoW config file but nothing has helped.  I'm using an nvidia 7600gs video card btw.

Has anyone else seen this problem or have any advice?

---

### Post by hikaricore on 2007-02-23
Config.wtf aside, have you tried running the game directly with the opengl flag?

```
wine WoW.exe --opengl
```

Most crashes I have seen in this manner are caused by accidently running the game in d3d mode.  The second you actually log in, the game crashes.

You may also want to try running wine as "root" just to make sure there aren't any odd file permissions causing the problem.

```
sudo wine WoW.exe --opengl
```

If all else fails, double check that your video drivers are working properly and direct rendering is enabled:

```
glxinfo | grep rendering
```

Good luck to ya.

I'm going against my own better judgement by replying to a WoW thread in the hopes that it's something simple to fix.

---

### Post by nouse66 on 2007-02-23
Thanks for the ideas.  I do always make sure that I'm running in opengl mode because direct 3d mode is even worse for me.  I tried your idea of running wine with sudo and that didn't help unfortunately. I also double checked and direct rendering is turned on.  

I'll see if i can find some other issue with x or my nvidia driver but running WoW is the only time that I have problems with it so I'm not very confident that I'll be able to find something.

---

### Post by hikaricore on 2007-02-23
Hm... have you recently changed any graphical settings in WoW?  I'm not sure if you ever had it running or not, but things such as fullscreen glow effects are known to crash the game on some video cards.  Checkout the Config.wtf overview at the [wine application database]("http://appdb.winehq.org/appview.php?iVersionId=6482") for info on making an optimized Config.wtf setup.  It may take a little while but at this point I'm betting it could be as simple as one config setting.

---

### Post by Rockett86 on 2009-05-14
I have an identical error, and have tried everything that nouse66 has tried. I verified my drivers and that rendering says 'yes', even tried to run it as root with the opengl tag. not sure what is going on. I also did all of the reccomended config.wtf modifications. I must be missing something, because I know people run WoW on linux, I've seen it in the past.

---

