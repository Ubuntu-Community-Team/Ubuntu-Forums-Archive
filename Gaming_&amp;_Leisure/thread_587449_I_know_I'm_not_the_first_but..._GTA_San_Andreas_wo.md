---
title: "I know I'm not the first but... GTA San Andreas won't work after install"
date: 2007-10-22
forum: Gaming &amp; Leisure
---

### Post by djrobthaman on 2007-10-22
Hi there,

I'm on a gutsy install running fusion using winefix and getting the following output:

```

douglas@douglas-desktop:~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas$ winefix 'gta_sa.exe'
Creating winefixrc\:

WINDOW_MANAGER=""
WM_POLICY="ask"
COMPIZ_FUSION_FIX=""
NICE=""
ERROR_LOGGING=""
/usr/bin/winefix: line 207: [: Direct: unary operator expected
Wine has crashed! To enable full error reporting, please run winefix with the flag 
"-d 1"

Errors:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
err:quartz:GraphBuilder_AddSourceFilter Load (80070002)
err:quartz:GraphBuilder_AddSourceFilter Load (80070002)
Initialised SoundManager
The Wine Application Database (App DB) is a collection of user-submitted information about application compatibility with Wine.

```

and when I trun off compiz by executing metacity --erplace I get this:

```

douglas@douglas-desktop:~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas$ winefix 'gta_sa.exe'
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  6 ()
  Serial number of failed request:  9
  Current serial number in output stream:  9
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  6 ()
  Serial number of failed request:  9
  Current serial number in output stream:  9
Wine has crashed! To enable full error reporting, please run winefix with the flag 
"-d 1"

Errors:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
err:quartz:GraphBuilder_AddSourceFilter Load (80070002)
err:quartz:GraphBuilder_AddSourceFilter Load (80070002)
Initialised SoundManager
douglas@douglas-desktop:~/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas$ 

```

Does anyone know what I can do to get this thing working?

Thanks a bunch

---

### Post by hikaricore on 2007-10-22
What exactly is "winefix" and why are you running it?
I think that needs to be the first question answered.

GTA:SA runs fine under WINE with a few tricks found around these forums.

---

### Post by djrobthaman on 2007-10-23
Well... winefix is supposed to be an add-on to wine I guess.  I found it on ubuntuforums [here]("http://ubuntuforums.org/showthread.php?t=533257&highlight=winefix+install").  A lot of people seemed to think it worked so I figured I'd try it.

Also, I know what you're gonna say.  Uninstall it and just use wine.  I did try with wine and it didn't work (why try winefix if wine works right). [ Here's a pretty full description of what happens with just wine]("http://ubuntuforums.org/showthread.php?p=3595114#post3595114").  I posted that after installing and trying gta with just wine.

PS where can I find these tricks.  So far tried removing the mpgs from the gta folder but that didn't work.

---

### Post by cogadh on 2007-10-23
deadlydeathcone wrote that script using a lot of the info from the Wine wiki and my own basic doc about using Wine (see the "Stuff I've learned about Wine" link in my sig). Pretty much anything winetricks does can be done using the info from those sources.

As for GTA:SA in particular, according to info on Wine's Application Database, the game seems to have problems running on anything other than Nvidia-based graphics cards. What do you have for a graphics device?

---

### Post by djrobthaman on 2007-10-23
Ahhh... I see.  I'm actually using an ATI X1300 all-in-tv-wonder.  So that might be the problem then.  

You wouldn't happen to know of any tricks I could use to fool the damn thing into actually working (first it refuses to give me tv on linux, now this... errggghhhh)

---

### Post by cogadh on 2007-10-23
Sorry, I'm a die-hard Nvidia fanboy, I really don't know any tricks that might work with an ATI card. When the next crop of ATI drivers come out, you might have better luck. There's quite a bit of hope around here that the drivers are going to get much better, now that they have gone open source.

---

### Post by djrobthaman on 2007-10-23
Yeah... I was getting ready to bite the bullet and shell out more cash to  go nvidia until that bit of news came out.

Thanks for the info

---

### Post by djrobthaman on 2007-10-23
Holy crap... [speaking of]("http://www.phoronix.com/scan.php?page=article&item=887&num=1") (not the open source drivers but maybe it'll make a difference)

---

### Post by cogadh on 2007-10-23
Hey, it may be worth trying, I'd definitely give it a shot.

---

