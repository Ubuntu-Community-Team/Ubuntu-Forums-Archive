---
title: "Unreal Tournament Binaries"
date: 2008-11-16
forum: Gaming &amp; Leisure
---

### Post by HexJunkie on 2008-11-16
I have Unreal Tournament GOTY installed on my Windows partition, and I'm wondering if there's some way to just obtain the Linux binaries for UT, and put them in the Windows UT folder and play the game that way.

I'd rather not waste space installing the game twice on one drive. Has anyone done this before? I can't even find the Linux binaries anywhere, just the Linux install scripts for the CD.

Thanks!

---

### Post by borlosky on 2008-11-22
Ut2004 is a native linux game, you should be able to run the game from the windows directory and it should run fine. it worked that way for me. a lot of games actually work that way (doom 3, ut2004, warcraft 3, spore, to name a few that i have working with existing windows installations running in ubuntu)

---

### Post by Frem on 2008-11-22
@borlosky: WarCraft 3 and Spore are not native Linux games; you're running them through Wine.

Additionally, the Linux binaries don't get installed when you install the game in Windows. You might try doing a Linux installation of the game, using ls and diff to figure out what files are unique to the Linux version, then deleting the rest and making system links to the windows files and folders.

I suspect you could also just copy the entire Linux install over to the windows partition and edit the game's configuration files (/home/yourname/.ut2004/System/UT2004.ini and UT2004.ini in the game's System folder) to update the paths, but the permissions might get messed up, and I don't know if it would work properly.

Either way is sort of a pain, though. Your best use of time is to just install it twice, or figure out which operating system you'd rather play it under.

---

### Post by borlosky on 2008-11-22
> @borlosky: WarCraft 3 and Spore are not native Linux games; you're running them through Wine.


very true they are running under wine, but I also didn't say those games were linux native, just that i was able to run them from the existing windows installs. I've found quite a few programs will continue to work fine (albeit even if using wine) i do have a good guide to install ut2004 under linux, but i'll have to post that guide once i get back home (has screen shots, and it uses gui, not command line based, so it's pretty easy, even for a linux noob, in fact it's the very guide i used to install it when i was still new to ubuntu)

---

### Post by DoktorSeven on 2008-11-22
What I do with UT99 is install the Linux version under Linux and Windows under Windows, keep my Windows partition mounted, then under Linux delete the Maps, Sounds, Textures, and Music directories for the Linux version and symlink to the Windows ones.

So if I have ~/UnrealTournament (Linux version, fresh install) and /media/sda1/UnrealTournament/ (Windows, with all the extra content):

```
cd ~/UnrealTournament; rm -Rf Maps Sounds Textures Music; ln -s /media/sda1/UnrealTournament/Maps; (and same for the rest)
```

(Please note my statement in my signature below regarding my use of rm -Rf.)

---

### Post by borlosky on 2008-11-22
ok, so here's the guide i used to get ut2004 up and running perfectly in ubuntu 8.04, and 7.10 (both 32bit)[http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd#unreal_tournament_2004_dvd]("http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd#unreal_tournament_2004_dvd")

---

### Post by diiphantom on 2009-01-02
Borlosky, any ideas of where i can get a guide to run UT99 perfectly aswell as this one fro ut2004? thanks!

---

