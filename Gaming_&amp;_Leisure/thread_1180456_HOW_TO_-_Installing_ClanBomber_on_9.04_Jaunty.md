---
title: "HOW TO - Installing ClanBomber on 9.04 Jaunty"
date: 2009-06-06
forum: Gaming &amp; Leisure
---

### Post by feardotcom on 2009-06-06
After about an hour of searching and trying to to figure out why i could not install ClanBomber, not even though apt-get, i came across a few threads and sites that were helpful. I am posting my how to. Some of the more advanced users may think this is simple, but i feel accomplished! lol :-P

1st: You need to add the dapper man universe. Click 'System/Administration/Software Sources' and then click the tab 'Third Party Software' look close to the bottom of the window and click 'add'.

Now add this just like it is.
```
deb http://cz.archive.ubuntu.com/ubuntu dapper main universe

```

It will ask you to reload, and tell it yes.

2nd:
Goto Synaptic Package Manager and search for clanlib and install the 'libclanapp-0.8-1'

Now, 3rd: 
Goto a terminal window and type the following:
```
sudo apt-get update
sudo apt-get install clanbomber
```

Now just make a launcher or run in terminal and your good to go!

Quick Notes:
-I wasn't sure if apt-get would install clanlib runtime or not so thats why i added it in the 2nd step.
-For some reason i cant compile clanbomber in terminal it errors out. Im assuming im not the only one this happens to.
-This game is freaking awesome!

---

### Post by _rsl_ on 2009-06-09
You can also try this fork of ClanBomber 2 that uses SDL [http://www.nongnu.org/clanbomber/](http://www.nongnu.org/clanbomber/)

---

### Post by feardotcom on 2009-06-10
my god that application was a pain in the *** to install. There zero install confg thing of whatever wasn't listed so i tried installing the regular clan bomber 2 and it wouldn't install. Then i finally decided to do with the manual install from that page and kept install this, install that, install this, and then that also...freak'n annoying, i dont really see a major difference in the game other than alot of bugs, and few graphics changed around.

---

### Post by _rsl_ on 2009-06-11
Well I'm the author of it and I a sure you that there are a lot of changes but most are not user visible, it plays and looks like the last release of clanbomber2 (cb2 was made by the original devs of clanbomber).

I choose to use Zero Install because some people I asked thought it was easier than just using the tar and updating constantly (I update it each month).

I like the original CB quite a lot and the problem was when it was removed from Debian (and Ubuntu), I checked the lists and they said it was to old to keep it. My intention is to maintain it usable by updating it and my first efforts are targeted at converting it to use SDL (instead of ClanLib) which is mostly done.

What you say about the requirements are true, it just are to many and some too big (Boost) that why I started to put also a compiled package to make is somewhat easier to use.

Sorry if it was bad for you but my idea was to get somebody to test it so I can improve it.

PS. If you have some suggestions or bugs, you can submit them to the mailing list or mail them directly to me. Thanks.

---

### Post by feardotcom on 2009-06-11
well hell, thats all you had to say...

Was it your intention to have the extra squares being shown on some levels? Also, the extra squares were being put on top of the permanent blocks.

EDIT: If your going to name it clan bomber 2, i would add some features the original didn't have, like different characters, Maybe add in different extras, or add in different disabilities. Maybe add options for bigger maps.

---

### Post by Ubentoo on 2010-10-05
It seems that my update-manager wanted to remove lots of packages during upgrade due to the new dapper entry in sources.list. See here: [http://ubuntuforums.org/showthread.php?t=1588604Installing](http://ubuntuforums.org/showthread.php?t=1588604Installing) clanbomber as described and removing the entry afterwards should solve the problem.

---

