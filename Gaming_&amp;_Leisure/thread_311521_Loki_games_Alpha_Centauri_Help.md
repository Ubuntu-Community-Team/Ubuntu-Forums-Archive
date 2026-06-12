---
title: "Loki games Alpha Centauri Help"
date: 2006-12-03
forum: Gaming &amp; Leisure
---

### Post by Abaddon on 2006-12-03
Hi all,

I've recently acquired a copy of the Loki games version of Alpha Centauri.  Installed no dramas (although the intro runs like a dog).  But when I start a game, as soon as it gets me into the 3d window, the game crashes with the error:

```
X Error:  BadMatch
  Request Major code 66 ()
  Error Serial #1980
  Current Serial #1983
trent@black-beast:~$ 


```

And drops me back to the desktop.

I've tried to patch the game using the Loki Updater, but most of the servers no longer carry the file.  When I did manage to find one that has the .run file, I can't get the GPG key from the loki webpage.

Has anyone been able to get it running, and does anyone have a copy of the keyfile lurking around?

Cheers,

---

### Post by edemark on 2006-12-03
Hi I have the game and working well without any problem. I have just installed and that was all (no patching or so). Could your error be something else and not the game. Something to do with your X (for example you do not have 1024x768 resolution added to your xorg.conf file)?

---

### Post by leech on 2006-12-03
Do you have Beryl or Compiz enabled?  That could cause problems as well.

Leech

---

### Post by Abaddon on 2006-12-04
Have checked the X-org, and it lists:

```
 Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350" 
```

at all colour depths, and I'm not running Beryl or Compiz.

No idea....

---

### Post by Antonlacon on 2006-12-04
```
Section "Extensions"
	Option "Composite" "Disable"
EndSection
```

At the bottom of xorg.conf and try again (after restarting X).

---

