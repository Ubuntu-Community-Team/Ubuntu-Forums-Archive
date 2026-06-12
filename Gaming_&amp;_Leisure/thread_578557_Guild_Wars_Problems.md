---
title: "Guild Wars Problems"
date: 2007-10-17
forum: Gaming &amp; Leisure
---

### Post by bostonca on 2007-10-17
Hello to all. I've been trying to get Guild Wars to work on linux and i've run into some problems. 

I can get it to install, after I can play it but without a cursor.

After that first play I can't restart it in wine, it says it can't access the dat file. These problems might be due to me being new to Linux as well but any help would  be great, thank you.

---

### Post by unkemptwolf on 2007-10-17
What version of WINE are you using?

I think that was fixed in the newest version. I play on 0.9.46 with no problems. If the mouse does disappear, you can try right clicking to see if it comes back up.

---

### Post by bostonca on 2007-10-17
I'm using wine 0.9.33 so that might be the problem. Thank you I'll try that out.

---

### Post by bostonca on 2007-10-17
alright, i upgraded wine to its current version ( 0.9.47 ) I installed Guild Wars with no problems and it played great right after that. The only problem is now that I turned the game off I can't figure out how to turn it back on!! 

I used this walkthrough [http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine](http://wiki.guildwars.com/wiki/Guild_Wars_on_Wine) to get it done. I enter the part they tell me to start the game and it says it can't find the directory. Any help would be great because if I can get this game working I have no need for windows and that just makes me feel all warm and fuzzy inside :).

---

### Post by unkemptwolf on 2007-10-19
I'm actually getting something similar to that. Wine seems to be resetting the permissions on my Guild Wars files to no read, no write. What it all comes down to is that I have to go into the folder and manually reset the permissions (r/w for user) to restart the game. I'm trying to figure out whats causing it, but if I cant figure it out I'll just write a script to change it for me when I start.

I'll have more info after I get home from work today.

---

### Post by paulr on 2007-10-20
Known bug in 0.47 unfortunately.

---

### Post by dorath on 2007-10-20
I am so glad you started this thread, .47 was on my list of things to do today.

Thanks! :)

My list of things to do today is now shorter.  ;-)

---

### Post by leetcharmer on 2007-10-20
I have .46

```
simbala@gerbert:~$ WINEDEBUG=-all wine "C:\Program Files\Guild Wars\Gw.exe" -windowed -dsound -dx8 -noshaders
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 469
Software fallback:ctx->Multisample.Enabled
***************************************************************************
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  144 (XFree86-DRI)
  Minor opcode of failed request:  9 ()
  Value in failed request:  0x400009f
  Serial number of failed request:  1012
  Current serial number in output stream:  1012

```

Could this be why my Guild Wars runs incredibly slow?  I'm using the Open Source ati driver (that one lets me use compiz :D!).  Upgrading the fglrx for Guild Wars shouldn't be much of a problem though.

---

