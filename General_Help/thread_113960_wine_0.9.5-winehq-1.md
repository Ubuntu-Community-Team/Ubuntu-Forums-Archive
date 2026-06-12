---
title: "wine 0.9.5-winehq-1"
date: 2006-01-07
forum: General Help
---

### Post by Nikusan on 2006-01-07
Hi all,
I just installed the latest wine using apt from 

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/

When I went to the Audio tab in winecfg it crashed with an error mentioning that /dev/snd/seq could not be found. I tried changing between ALSA, OSS, ESD, Artsd but none of them worked.

Now when I run winecfg and go to the Audio tab I get this:

```

wine: Unhandled page fault on write access to 0x45cd6584 at address 0x7eca93b1 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on write access to 0x45cd6584 in 32-bit code (0x7eca93b1).
In 32 bit mode.
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
...
...

```
Then Stack dump, backtrace, modules, etc.

I should note that I get this error even after changing back to ALSA (which I was originally using).

Could this be because the package at the wine sf site is for debian? Can anyone else reproduce this / know how to help me?
thanks

---

### Post by ember on 2006-01-07
If I remember correct, /dev/snd/seq is related to midi-output. You should try to install Timidity and add Midi support to ALSA.

---

### Post by Nikusan on 2006-01-07
Thanks for the quick reply ember :)
I've installed Timidy but winecfg still crashes, is there anything I need to do to add midi support to ALSA beyond installing Timidity?

---

### Post by dcstar on 2006-01-07
[QUOTE=Nikusan]Hi all,
I just installed the latest wine using apt from

deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
......[/QUOTE]
That new version stuffed up my wine install, I rolled back to the standard Ubuntu version.

I have seen other people with problems since they got it last week, it could be more trouble than it is worth (until the next version comes out).

---

### Post by newuser111 on 2006-01-08
i get the same issue with winecfg crashing when clicking on the audio tab, since about version 0.9.1+?

I don't know if it just affects ubuntu users, but it seems like a bug rather than a problem with your computer

---

### Post by magnusbb on 2006-01-08
Same problem here. Wine 0.9.5.

---

### Post by cb951303 on 2006-01-08
Maybe this isn't the right place but where is the ubuntu version of wine. I searched in Synaptic but there is no wine packages. Insted there is libwine, xwine etc..
I also checked the universe multiverse community maintained repositories. 

thanks

---

### Post by lutosdemayo on 2006-01-08
[QUOTE=cb951303]Maybe this isn't the right place but where is the ubuntu version of wine. I searched in Synaptic but there is no wine packages. Insted there is libwine, xwine etc..
I also checked the universe multiverse community maintained repositories. 

thanks[/QUOTE]

You are not going to find it unless you won't go to winehq.org.
I've taken this from there:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

Just add it to your repository in synaptic.

---

### Post by lutosdemayo on 2006-01-08
[QUOTE=magnusbb]Same problem here. Wine 0.9.5.[/QUOTE]

I think the problems in ur pc and not with wine. I have no problems there. I just upgraded wine today.

---

### Post by mrsad on 2006-01-08
how did you set up wine? use winetools from winehq to configure everything for you, it works like a charm.

---

### Post by cb951303 on 2006-01-08
[QUOTE=lutosdemayo]You are not going to find it unless you won't go to winehq.org.
I've taken this from there:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

Just add it to your repository in synaptic.[/QUOTE]
I think I'm misunderstood, I wasn't talking about version 0.9.5. Anyway, I think I can't find it because I'm using the amd64 version. 

Thanks anyway, sorry to bother

---

