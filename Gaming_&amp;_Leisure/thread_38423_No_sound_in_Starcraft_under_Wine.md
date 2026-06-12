---
title: "No sound in Starcraft under Wine"
date: 2005-05-31
forum: Gaming &amp; Leisure
---

### Post by wylie348 on 2005-05-31
Can anyone help me to get sound working in Hoary with Starcraft under Wine?  SC runs just fine in Hoary, but I have no sound (and killall esd does not help - but it does work for enemy territory).
Thanks for the help in advance!
 :)

---

### Post by Mez on 2005-05-31
[http://appdb.winehq.org/appview.php?versionId=51](http://appdb.winehq.org/appview.php?versionId=51)

---

### Post by wylie348 on 2005-05-31
Thanks for the link, but I cannot find any information on sound related issues at the site?
Thanks again.
 :neutral:

---

### Post by DarkKnight on 2005-05-31
[QUOTE=wylie348]Thanks for the link, but I cannot find any information on sound related issues at the site?
Thanks again.
 :neutral:[/QUOTE]
 Have you tried configuring ALSA? 

You may also want to check your config file for wine (~/.wine/config) and check which sound it's set to use. :) 

On a side note, how did you get the CD working? Mine keeps asking for the CD that's already mounted...

Edit: Ok, forget about the CD, thats working now, buw now the same error as Diablo2...

```
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c6f698)->(00010024,00000013)
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found! (NoRes)
Wine exited with a successful status

```

---

