---
title: "Steam in WINE"
date: 2006-08-27
forum: Gaming &amp; Leisure
---

### Post by newbreed9000 on 2006-08-27
I have wine configed and installed. I got steam installed fine but when it goes to update i get to 28% and stop. any clues?

---

### Post by mejy on 2006-08-27
> **newbreed9000 said:**
> I have wine configed and installed. I got steam installed fine but when it goes to update i get to 28% and stop. any clues?

There's a hack around this that involves (something like) copying steam_new.exe to steam.exe, but it's touch and go, is prone to breakage at a later date and none of the source games run on Ubuntu.  Give it another year or so would be my advice.  (I looked into this for two days, but never got anywhere).

---

### Post by HAARP on 2006-08-27
It's a known bug. Search the forum, there's a workaround.

---

### Post by mipstien on 2006-08-27
steam and source all run perfect on my ubuntu install. i still get like 200+ fps .... everything maxxed


26% Bug Workaround:

Run this from the directory you installed Steam.

wine steamTmp.exe SelfUpdate "Steam.exe" 14

---

### Post by mejy on 2006-08-28
> **mipstien said:**
> i still get like 200+ fps .... everything maxxed

200fps?  What game's this on?  CS:S/HL 2 just crashed on me...

---

### Post by newbreed9000 on 2006-08-28
I cant seem to locate ANYTHING in ubuntu.. where would the "c" file be located by default? i cant find anyfolder for WINE at all. Any help would be nice ty.

---

### Post by maka on 2006-08-28
> **newbreed9000 said:**
> I cant seem to locate ANYTHING in ubuntu.. where would the "c" file be located by default? i cant find anyfolder for WINE at all. Any help would be nice ty.

the filesystem in ubuntu works differently then what you are used to in windows.

anyways wine, you would find by typing "cd ~/.wine" in a terminal.  the . means that the folder is hidden so if you want to see the folder in nautilus, press ctrl+h to reveal hidden folders, and again to hide.

hope this helped ;)

---

### Post by newbreed9000 on 2006-08-29
i type this in the terminal nad it work's its self into the command line leaveing me to type more? I hit enter nothing. I was hoping i could open the wine/steam folder to run the steam updater. ](*,) 

Im crying inside.

---

### Post by mipstien on 2006-08-29
easiest way is to type 'ls' which is a directory list command. but if you wanna go through your file manager open that up and click 'view' then 'view hidden'  or "ALT+V   H" that will show your hidden folders and you can scrolls around through them and look for them
it will be in your home/*******/.wine/drive_c     
if you have installed it correctly
if this doesn't work you could give someone remote access and let them help you there.
its not the safest thing but its bound to show you something :P

---

### Post by bugz0r on 2006-08-29
Try this [link](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games).

---

### Post by khedron on 2006-08-29
For me, the command that stopped Steam from crashing at 26-28% was
```
wine "C:\Program Files\Steam\SteamTmp.exe" SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```

WRT Counterstrike, whenever I open it (from the Steam menu) it puts X into 800x600 mode, shows the loading screen and then crashes, showing the desktop still in 800x600. To get X functioning normally I have to Ctrl-Alt-Backspace.

Anyone have any tips?

---

### Post by toipot on 2006-08-29
This bug does seem to appear on this forum every couple of weeks

Search people! 

](*,) 
:p

---

### Post by ubu-for on 2006-08-30
> **khedron said:**
> For me, the command that stopped Steam from crashing at 26-28% was
```
wine "C:\Program Files\Steam\SteamTmp.exe" SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```

WRT Counterstrike, whenever I open it (from the Steam menu) it puts X into 800x600 mode, shows the loading screen and then crashes, showing the desktop still in 800x600. To get X functioning normally I have to Ctrl-Alt-Backspace.

Anyone have any tips?

Since Wine 0.9.20 I have this bug, too!

---

### Post by HAARP on 2006-08-30
Try **[Ctrl]+[Alt]+[+]** and **[Ctrl]+[Alt]+[-]** (numpad) to change the resolution on-the-fly

---

### Post by khedron on 2006-08-31
> **khedron said:**
> 
WRT Counterstrike, whenever I open it (from the Steam menu) it puts X into 800x600 mode, shows the loading screen and then crashes, showing the desktop still in 800x600. To get X functioning normally I have to Ctrl-Alt-Backspace.


I have learned how to stop this from happening. There is a bug in Wine that causes CS to crash when not running at the native resolution.

To solve the problem, go into Steam and select the Games tab. Right click on CS and select Properties. Then click the Launch Options... button and enter
```
 -fullscreen -height 1024 -width 768
```
of course, if your native resolution is not 1024x768, change the numbers accordingly.

Now CS will run. But no sound, since I have to use the OSS driver in winecfg yet I use the ALSA driver for my soundcard. Another day, another challenge...

EDIT:
By the way, if anyone is experiencing winecfg crashing when the audio tab is selected, try this:
```
sudo mv /usr/lib/wine/winearts.drv.so winearts.drv.so_bak
```

Someone should create a thread in the HOWTO section explaining how to fix all the bugs in Wine+CS:S, so everyone else doesn't have to trawl the Internet to find out how.

---

### Post by newbreed9000 on 2006-09-02
mipstien had the answer i was looking for.. the commands helped me too. ty all.

---

