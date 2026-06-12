---
title: "No CD found using Wine"
date: 2005-05-16
forum: Gaming &amp; Leisure
---

### Post by Nissemand on 2005-05-16
No matter what i try to install, or run, using Wine, the game i try to run tells me that it can't find the CD... I've tryed with Diablo 2, Diablo 1, Heroes Of Might And Magic 4 and Red Alert... Can someone solve my problem? or at least try to?

---

### Post by philipacamaniac on 2005-05-16
Okay, wine is a scary beast to tame. Here's a quick check through:

1. Go to ~/.wine/dosdevices (.wine is a hidden directory in your home directory)
```
cd ~/.wine/dosdevices
```

2. Make sure you have a symbolic link in there (usually **r::**) that is pointing to /media/cdrom

3. If you do, make sure the CD is mounted in linux
```
mount /dev/cdrom
```

If you don't have any drives in your dosdevices directory, you should check out [http://winehq.org/site/docs/wine-user/config-drive-main](http://winehq.org/site/docs/wine-user/config-drive-main), which has a great tutorial on setting up devices in Wine.

You may need to try Transgaming's [Cedega](http://www.transgaming.com/) with some of those games. Wine doesn't have very much Direct3D support.

---

### Post by gil-galad on 2005-05-16
[QUOTE=Nissemand]No matter what i try to install, or run, using Wine, the game i try to run tells me that it can't find the CD... I've tryed with Diablo 2, Diablo 1, Heroes Of Might And Magic 4 and Red Alert... Can someone solve my problem? or at least try to?[/QUOTE]
 Actually it is because cds use copy protection that wine does not emulate so it cannot "detect" your cd when running.  You need to crack the game by replacing the exe with one that does not ask for the cd.  I recomend looking under game fixes--PC Games at [www.megagames.com](www.megagames.com). 

This will allow you to run the game without a cd.

---

### Post by ante0 on 2005-05-17
But Diablo 1 doesnt have a cdprotection does it? I got i running, almost, in wine. In cedega it works and the same goes with diablo 2 (though it didnt work with the cd due to cd-protection).
Has anyone got Diablo II Battle.net working?

---

### Post by gil-galad on 2005-05-17
It should work fine.  Make sure you use a crack that allows you to play on bnet.

---

### Post by ante0 on 2005-06-04
I downloaded a crack that lets you play on bnet, Loader.exe, it uses Apihooks which cant be found by wine/cedega. 

I found out a way to get the D2 cd working though, this is for cedega only (i think), in .transgaming dir you find a config file, open it and scroll down to where it says [version] change the "Windows" = "win95" to "winxp", that made my cd work.
   :smile:

---

