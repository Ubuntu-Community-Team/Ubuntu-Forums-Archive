---
title: "Wine 0.9.33 doesn't work with CS:S?"
date: 2007-03-20
forum: Gaming &amp; Leisure
---

### Post by BongoBob on 2007-03-20
Hello everyone.

I recently followed a tutorial on linux-gamers.com on installing Steam and CS:S on ubuntu. I got it running fine last night, and went to bed. Today, I sudo apt-get update and upgrade, and it upgrades my wine to 0.9.33. I try it now, and it keeps giving me this error:

SteamStartup() failed: SteamStartup(0xf,0x0034E064) failed with error 1: The registry is in use by another process, timeout expired.

Can anyone help me? I apologize if this has been asked and answered elsewhere, but I could find no such thread.

---

### Post by Brynster on 2007-03-22
CS:S and steam does work in Wine 0.9.33

firstly install wine as laid out here :- [HTML]http://www.winehq.org/site/download-deb[/HTML]

once done open up a terminal session and type

```
winecfg
```

then close the window that pops up. All that does is set a base configuration

Then goto [HTML]www.steampowered.com[/HTML] and down load the steam installer

whilst thats dowloading search google for tahoma:ttf font.

add the tahoma font to ./wine/c_cdrive/widows/fonts folder. Remember that ./ folders are hidden so open nautilus and in the view menu on the toolber check the show hidden check box.

omce you have done that:

```
cd /path/to/steaminstaller
``` 

path to steam installer being whereever you downloaded the steam installer to i use the desktop so it would be 

```
cd Desktop
```

when you have got there type the following remembering that Linux is case sensetive so it has to be exactly as written here

```
wine SteamInstall.exe
```

this will install Steam. Once done allow it to download the game you want to play and hey presto job done

---

### Post by BongoBob on 2007-03-22
I already have Steam and CS:S installed. Bt for some reason since upgrading it to the latest version it won't work. Do I have to reinstall it with the new version?

---

### Post by Brynster on 2007-03-24
Actually I re-read your post, my mistake. The error your getting is caused by the steam client not releasing the registry correctly when it has finnished loading. Its a known fault thats plagued Cedega for sometime and now is plaguing Wine. 

The best why i find to get around it is to start a NON SOURCE BASED STEAM GAME (ie half life or original cs.) wait for it to load then cancel out of the game and immediatley start CS:S or HL:S. 

Its not perfect but does prevent you error appearing about 50% of the time

CS:S does work in Wine0.9.33 but a little patience is required to get it to launch.

---

