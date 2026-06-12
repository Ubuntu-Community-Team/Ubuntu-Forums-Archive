---
title: "OMG! Dungeon Siege 2 under WINE!"
date: 2006-06-03
forum: Gaming &amp; Leisure
---

### Post by seth0x2b on 2006-06-03
Hey guys.I was getting a little bored so I thought I'll try some of my "older"(as in already finished 2-3 times :) ) games under WINE. I tried Sacred with no luck(if anyone managed to install Sacred under WINE, I'll really like to know..how), then tried Dungeon Siege 2.The installation worked like a charm, and the game moves almost as on Winblowz(speed and all).
So...now I have both Neverwinter and Dungeon Siege on Linux.
Windows who?! :D

I only have one problem before having a perfect game install: I can't see the mouse cursor :(.It's there, because I can click and my character moves, the menus are highlighted when I'm hovering over them, but I can't see it.If anyone had this issue with DS or any other game, please let me know how you fixed it, 'cause I really missed this game :).

Cheers

---

### Post by Matrix101 on 2006-06-03
You could try to use a native dll of direct input. Afaik in Empire Earth 2 there was the same problem and the dll override fixed the problem there.

---

### Post by seth0x2b on 2006-06-03
Seems it's a known wine bug.wined3d doesn't support cursors or something like that.
Could you elaborate a bit on how could I use the native dll? I've never tweaked wine before and really don't know where to start.

Thanks in advance.
Cheers

---

### Post by B0rsuk on 2006-06-03
Original poster:

I strongly suggest that you post your Dungeon Siege2 impressions on Wine appdb, and method used to run it. This makes it easier for people to find working Linux games. Judging by what you say I'd give it at least 'silver'.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Matrix101 on 2006-06-03
Put the dll in your system folder of your fake windows drive.Then execute winecfg and set the dinput.dll to native. 

PS:dont forget to backup the original dinput.dll

---

### Post by seth0x2b on 2006-06-03
Ok.I tried copying dinput.dll in windows/system, and in windows/system32, and windows/Directx, and windows/drivers. I added DungeonSiege2.exe to the wine app list in winecfg, set dinput to native, tried to set dinput8 to native to, and now it doesn't start at all.
I compiled the latest version of wine 0.9.14.
Now, when I run Dungeon Siege(with or without dinput set to native, it only goes into fullscreen and an error about D3D failing to initialize appears...

What should I do now?!I guess I spoke too soon about the whole thing going to smooth.Damn mouse cursor :(

Any advice / hint is more than welcomed!

Cheers
[EDIT] BTW, there was no dinput.dll in any of the directories..but that's because wine is using only builtins at the moment probably...
the only thing I see related to direct..anything..is ddraw.dll.

---

### Post by JoWilly on 2006-06-03
[QUOTE=seth0x2b]
Windows who?! :D
[/QUOTE]

:mrgreen:

---

### Post by Matrix101 on 2006-06-04
Wich Wine did you use before? In Wine 0.9.14 are some problems with ddraw. Afaik there is a patch which solves this problem, but i don´t
know where to download it.

Edit:Just found this [http://stud4.tuwien.ac.at/~e0526822/](http://stud4.tuwien.ac.at/~e0526822/). There is also a link to a patched wine version.

---

### Post by seth0x2b on 2006-06-04
```

seth@orion:~$ wine --version
Wine 0.9.9
seth@orion:~$

``` This is the older wine I used.I rolled it back and Dungeon Siege runs again, but still no cursor.I guess i'll wait for the wine devs to patch things up, because I browsed all night long and everybody has the mouse cursor problem.It's even on the winehq site. Oh well...just got all Neverwinter modules today.That should keep me occupied for a few weeks :)
I'll try the patched wine version(I compiled 0.9.14 because it's already patched with the D3D thing)...

Cheers and thanks for your help

---

### Post by willneedshelp... on 2006-07-19
well i have a problem i have no clue cause im a complete noob to linux...installation went fine but when i try to run it with wine it gives me these error messaegs:

fixme:crypt:I_CryptCreateLruCache (0x7fb8fc94, 0x7159bdc8): stub!
fixme:crypt:I_CryptInstallOssGlobal 7159bbb8 00000000 00000000
err:module:LdrInitializeThunk "wintrust.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Microsoft Games\\Dungeon Siege 2\\DungeonSiege2.exe" failed, status c0000142


i have no clue what these really mean and ive tried to look it up but it just isnt working for me...can i get some help please?

---

### Post by Icon41 on 2006-07-19
I hate dugeon seige 2, number 1 as better in my opinion.

---

