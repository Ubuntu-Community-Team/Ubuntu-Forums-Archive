---
title: "Wine and resolution switching."
date: 2005-05-31
forum: Gaming &amp; Leisure
---

### Post by DarkKnight on 2005-05-31
Does anyone else have the problem with wine and games that require a resolution change? 

Everytime I try and start up either Diablo2 or Starcraft I get an error like this: 

```
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c6fa40)->(00010022,00000013)
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found! (NoRes)
```

Any ideas? 

(I've already spent 2 days googling it with little to no luck :( )

---

### Post by DarkKnight on 2005-06-01
[QUOTE=DarkKnight]Does anyone else have the problem with wine and games that require a resolution change? 

Everytime I try and start up either Diablo2 or Starcraft I get an error like this: 

```
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c6fa40)->(00010022,00000013)
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found! (NoRes)
```

Any ideas? 

(I've already spent 2 days googling it with little to no luck :( )[/QUOTE]
 All fixed thanks to Kirtaner posting his xorg.conf file ^___^

This was is alll that needed to be fixed...

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
        Load    "GLcore"
        # Load "extmod"
        SubSection "extmod"
            Option "omit xfree86-dga"
        EndSubSection
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

---

### Post by Rodrigo on 2005-06-01
Thank you man!, now I can play starcraft in fullscreen  :grin:

---

### Post by OuTcRy on 2007-05-12
i cannot play cm4 in fullscreen.i did what darkknight said but i have the same error (x11.....)

please help. i cannot play any games on feisty

---

