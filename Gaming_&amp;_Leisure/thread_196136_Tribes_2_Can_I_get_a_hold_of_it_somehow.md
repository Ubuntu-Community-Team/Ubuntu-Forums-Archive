---
title: "Tribes 2: Can I get a hold of it somehow?"
date: 2006-06-13
forum: Gaming &amp; Leisure
---

### Post by rjcube on 2006-06-13
When they were doing that Tribes 2 Promo where they gave away CD keys, I got one of them and have an account on there. But since then I had had my hard drive reformatted, is there any way to download Tribes 2 again? or is it gone forever?

---

### Post by GameGod on 2006-06-14
[http://www.filemirrors.com/search.src?type=begins&file=tribes2&action=Find]("http://www.filemirrors.com/search.src?type=begins&file=tribes2&action=Find")

tribes2_gsi.exe is the free packaged up version of it... No Linux version I guess, but it's definitely worth a shot in WINE or Cedega (or both)... There's a good chance of it working just fine...

---

### Post by rjcube on 2006-06-14
[QUOTE=GameGod][http://www.filemirrors.com/search.src?type=begins&file=tribes2&action=Find]("http://www.filemirrors.com/search.src?type=begins&file=tribes2&action=Find")

tribes2_gsi.exe is the free packaged up version of it... No Linux version I guess, but it's definitely worth a shot in WINE or Cedega (or both)... There's a good chance of it working just fine...[/QUOTE]

Thanks, I shall give that a try. According to the Wine Application DB, Tribes 2 runs great on Ubuntu 5.10, so it shouldnt have a problem with 6.06.

---

### Post by leech on 2006-06-14
[QUOTE=rjcube]Thanks, I shall give that a try. According to the Wine Application DB, Tribes 2 runs great on Ubuntu 5.10, so it shouldnt have a problem with 6.06.[/QUOTE]

Not neccesarily.  Wine has the awful habit of breaking things in newer versions.  Not entirely their fault, but it does happen.  For example, according to the AppDB, Rainbow Six 3: Raven Shield (one of the few games that ties me to Windows) worked in Wine at one point in time.  It hasn't for a long time now though, and just about every new version for a while there I was trying without success.

I do wish you good luck though.  If you can find a copy of Tribes 2 for linux, the key should work for it though.

Leech

---

### Post by rjcube on 2006-06-14
It seemed to install ok in wine, but I have no idea how I would get to it...anyone know?

---

### Post by markmark on 2006-06-14
[QUOTE=rjcube]It seemed to install ok in wine, but I have no idea how I would get to it...anyone know?[/QUOTE]

It would have installed on your wine "c drive" which is usually located in your home directory. You should be able to launch it from the command line doing something like:
```
wine "~/.wine/drive_c/Program Files/Tribes 2/tribes2.exe"
```

Obviously change that to be the path to the actual install file, have a hunt around ~/.wine/drive_c/Program Files (Remebering .wine is a hidden directory and won't show up in Nautilus by default.)

---

### Post by rjcube on 2006-06-15
[QUOTE=markmark]It would have installed on your wine "c drive" which is usually located in your home directory. You should be able to launch it from the command line doing something like:
```
wine "~/.wine/drive_c/Program Files/Tribes 2/tribes2.exe"
```

Obviously change that to be the path to the actual install file, have a hunt around ~/.wine/drive_c/Program Files (Remebering .wine is a hidden directory and won't show up in Nautilus by default.)[/QUOTE]

First of all thanks for lettin me know where the keep the wine files, I was lookin for that. 

But heres what comes up when I type in the directory.

```
rjcube@rjcube-desktop:~$ wine /home/rjcube/.wine/drive_c/Dynamix/Tribes2/GameDat a/Tribes2.exe
fixme:keyboard:X11DRV_GetKeyNameText (00000000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00540000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00550000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00590000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (005a0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (005b0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (005c0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (005d0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (005e0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (005f0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00600000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00610000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00620000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00630000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00640000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00650000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00660000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00670000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00680000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00690000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (006a0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (006b0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (006c0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (006d0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (006e0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (006f0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00700000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00710000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00720000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00730000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00740000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00750000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00760000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00770000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00780000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (00790000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (007a0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (007b0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (007c0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (007d0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (007e0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (007f0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01000000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01010000,0x7fb9f49c,256): unsupported key,  vkey=001b, ansi=001b
fixme:keyboard:X11DRV_GetKeyNameText (010e0000,0x7fb9f49c,256): unsupported key,  vkey=0008, ansi=0008
fixme:keyboard:X11DRV_GetKeyNameText (010f0000,0x7fb9f49c,256): unsupported key,  vkey=0009, ansi=0009
fixme:keyboard:X11DRV_GetKeyNameText (012a0000,0x7fb9f49c,256): unsupported key,  vkey=0010, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01360000,0x7fb9f49c,256): unsupported key,  vkey=0010, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01390000,0x7fb9f49c,256): unsupported key,  vkey=0020, ansi=0020
fixme:keyboard:X11DRV_GetKeyNameText (013a0000,0x7fb9f49c,256): unsupported key,  vkey=0014, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01460000,0x7fb9f49c,256): unsupported key,  vkey=0091, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (014c0000,0x7fb9f49c,256): unsupported key,  vkey=000c, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01540000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01550000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01590000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (015a0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (015b0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (015c0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (015d0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (015e0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (015f0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01600000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01610000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01620000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01630000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01640000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01650000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01660000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01670000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01680000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01690000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (016a0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (016b0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (016c0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (016d0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (016e0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (016f0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01700000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01710000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01720000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01730000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01740000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01750000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01760000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01770000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01780000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (01790000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (017a0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (017b0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (017c0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (017d0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (017e0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
fixme:keyboard:X11DRV_GetKeyNameText (017f0000,0x7fb9f49c,256): unsupported key,  vkey=0000, ansi=0000
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=D1,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=D1,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=C9,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=C9,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=CF,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=CF,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=C7,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=C7,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=CB,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=CB,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=C8,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=C8,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=CD,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=CD,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=D0,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=D0,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=B7,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=B7,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=D2,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=D2,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=D3,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=D3,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=B3,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=B3,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=B5,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=B5,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=9C,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=9C,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=64,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=64,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=65,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=65,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=66,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=66,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=9D,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=9D,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=B8,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=B8,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=DB,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=DB,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=DC,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=DC,keycode=8,state=1)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=DD,keycode=8,state=0)
err:keyboard:X11DRV_ToUnicodeEx Please report: no char for keysym 0000 (No Name)  :
err:keyboard:X11DRV_ToUnicodeEx (virtKey=0,scanCode=DD,keycode=8,state=1)

```

no idea what any of that means...

---

### Post by UltraSonicSite on 2006-10-19
I recently got this error as well, am figuring out a solution right now.

---

