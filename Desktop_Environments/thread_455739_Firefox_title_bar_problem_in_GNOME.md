---
title: "Firefox title bar problem in GNOME"
date: 2007-05-26
forum: Desktop Environments
---

### Post by Feba on 2007-05-26
[IMG]http://img135.imageshack.us/img135/3991/screenshot1im0.png[/IMG]As you can see, it randomly turns gray while i'm using it (especially if I load an new tab or page), as if it had lost focus, but it also loses it's title name, and the window management buttons clip in and out. I'm thinking this might have something to do with my installing kubuntu-desktop earlier, but i've since removed it, and this problem won't go away. Anyone know how to deal with this? I've tried turning on and off title bar transparency in compiz tray icon, but it didn't work

---

### Post by gavintlgold on 2007-05-26
I would imagine that to be a compiz problem, as that sometimes happens to me after reloading compiz (a minimize/unminimize fixes it).

---

### Post by Feba on 2007-05-27
So there's no fix for it? =/

---

### Post by gavintlgold on 2007-05-27
I would probably just wait and see what happens after Compiz/Beryl merges and releases their new program. That should happen in a few months.... :)

I don't know too much about Compiz, sorry, I'm a Beryl person until CompComm gets a release.

---

### Post by Sain on 2007-07-22
I am also having the same problem...  and it's quite annoying. It happens only with firefox when it's maximized.

Also it's a bit funny when Im trying to convince my friends that ubuntu is great and then titlebar of my windows dissapears :)

Are there any updates of compiz libraries or something? Nothing can be done?

---

### Post by crimesaucer on 2007-07-22
This may not be a fix....but you could always install Compiz fusion and Emerald: [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)


Then you can use a window theme that doesn't do that. Plus, Emerald is about the best looking window theme out there...if you want to impress your friends.

...so after you install Compiz Fusion, then install Emerald and Emerald themes.

```
sudo aptitude emerald emerald-themes
```

then run this command in "alt+f2" to use Emerald:

```
emerald --replace
```


....also, after you have both Compiz fusion and Emerald installed, and you've tried them both and would like it to load on start up, then add them both to your Strat up apps with these commands in your Autostarted Applications:

```
compiz --replace
```

```
emerald --replace
```

---

