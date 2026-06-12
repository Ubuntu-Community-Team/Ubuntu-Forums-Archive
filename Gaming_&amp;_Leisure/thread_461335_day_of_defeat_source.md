---
title: "day of defeat source"
date: 2007-06-01
forum: Gaming &amp; Leisure
---

### Post by toosweetnitemare on 2007-06-01
ive read a few posts and it sounds like people are getting day of defeat source to work in ubuntu. am i correct in assuming you can do this? and if it is true, any one know of a walk through on installing it and running it? cause thats the only reason i keep a windows box around, just for that game. thanks

---

### Post by ghandi69_ on 2007-06-01
I'm not certain.. but I know I was able to get CounterStrike Source working in ubuntu... and from the instructions I used it seemed any Steam game would work just the same.

CounterStrike however had one glitch... the screen would freeze for about a 2nd every time I saw a flash grenade!!

I've been told there was a fix for this but I have ventured to try it out.

---

### Post by justin whitaker on 2007-06-01
> **toosweetnitemare said:**
> ive read a few posts and it sounds like people are getting day of defeat source to work in ubuntu. am i correct in assuming you can do this? and if it is true, any one know of a walk through on installing it and running it? cause thats the only reason i keep a windows box around, just for that game. thanks

I've got HL2, CS:S and a bunch of mods running on Ubuntu, but DoD:S is still buggy for me. I downloaded it and installed it via Steam, but it runs laggy for me.

Here is the WineApp post:

[http://appdb.winehq.org/appview.php?iVersionId=4571](http://appdb.winehq.org/appview.php?iVersionId=4571)

Good luck!

---

### Post by toosweetnitemare on 2007-06-01
thanks guys thats a big help. i hope it works cause i wanna burn that windows box. keep me up to date if you guys find anything else though please. thanks again for your time!:D

---

### Post by lordhebe on 2007-06-01
Here is a useful guide for getting it working, it's for Half life 2 and counter strike source, but the same thing should work for Day of Defeat source. They all run through steam and the source engine, plus it has a gold rating on wine appdb. [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games")

---

### Post by toosweetnitemare on 2007-07-10
********FIXED  IT*******

This is a known issue with some graphic card / driver combinations.

A work around you can try is to modify the command line for the Steam game you are trying to run. For example in Half-Life 2, right click on the game in the Steam games list. Then choose properties. Click the 'Set Launch Options' button. In the text field add this to the end:

-dxlevel 70 -width 1024 -height 768

You can also change the resolution to what you want to run. dxlevel lowers the HL2 engine to DirectX 7.0 levels. This is more compatible on some chipsets. For example, regular MacBook users must use this this setting as the Intel video chipset does not support shaders.


i did this last night and  then i gamed for almost an hour before my woman tells me to get off the computer cause "its working now, congrats. no do the dishes". haha 

happy gaming all

---

