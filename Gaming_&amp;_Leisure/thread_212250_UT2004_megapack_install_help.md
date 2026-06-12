---
title: "UT2004 megapack install help"
date: 2006-07-09
forum: Gaming &amp; Leisure
---

### Post by dipswitch on 2006-07-09
I'm back to give ubuntu and UT2004 another try. I was able to get the game installed but for some reason I can't install the megapack. I've tried two different megapacks and each time the archive integrity is good. However when it tries to install it says that I first need to install UT2004. WTF? Is it really this hard to get a game installed and working properly with linux?

---

### Post by pharcyde on 2006-07-09
Did you try isntalling UT2004 with this -> [http://liflg.org/?catid=6&gameid=17](http://liflg.org/?catid=6&gameid=17)

---

### Post by dipswitch on 2006-07-09
Yes. I just finished trying that one. First I ran...
```

$ sudo chmod +x ut2004.megapack-english-2.run

```
then...
```

$ /bin/bash ut2004.megapack-english-2.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 2004 Megapack............................................................

Gdk-WARNING **: locale not supported by C library

```
Then a small gui popped up that said I must first have UT2004 installed and thats it.

---

### Post by dipswitch on 2006-07-09
Finally got it installed by downloading tarball from [http://treefort.icculus.org/ut2004/](http://treefort.icculus.org/ut2004/) and copying over my installation folders.

Game runs but there is no sound/audio. WTF???

I've tried killall artsd as I've seen that plenty of others have had the same problem with no audio or sound with Unreal and some have said that it works but I get...
```

$ killall artsd
artsd: no process killed

```
And still no audio with UT2004. The audio works with everything else that I know of. Any advice?

---

### Post by Brighid on 2006-08-01
> **dipswitch said:**
> Finally got it installed by downloading tarball from [http://treefort.icculus.org/ut2004/](http://treefort.icculus.org/ut2004/) and copying over my installation folders.

Game runs but there is no sound/audio. WTF???

I've tried killall artsd as I've seen that plenty of others have had the same problem with no audio or sound with Unreal and some have said that it works but I get...
```

$ killall artsd
artsd: no process killed

```
And still no audio with UT2004. The audio works with everything else that I know of. Any advice?

I know this isn't much comfort, but I had the same problem.  I also installed from Icculus.  After updating, the game runs, but without sound.  I haven't found a solution to this, but if I do, I will post it here.  I hope that perhaps someone else can provide a solution ..

---

### Post by daller on 2006-09-26
If you run Kubuntu (KDE) - simply disable the sound "engine" in KDE! (Who need startup sounds anyway?)

---

### Post by Lagtw on 2011-02-14
[QUOTE=dipswitch;1233811]Game runs but there is no sound/audio. WTF???

First, you have to have libopenal installed. Secondly, you have to create a symbolic link of the library to your UT2004/System folder. Like this:

ln -sfn /usr/lib/libopenal.so /path/to/game/install/System/libopenal.so

If this doesn't work, try doing things like:

ln -sfn /usr/lib/libopenal.so /path/to/game/install/System/libopenal.so**.1**

or

ln -sfn /usr/lib/libopenal.so /path/to/game/install/System/[B]openal.so
[/B]

or

ln -sfn /usr/lib/libopenal.so /path/to/game/install/System/openal.so[B/].1
[/B]

Hope it helps :)

---

