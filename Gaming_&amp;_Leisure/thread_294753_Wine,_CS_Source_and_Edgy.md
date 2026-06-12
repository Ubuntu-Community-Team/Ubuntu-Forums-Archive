---
title: "Wine, CS: Source and Edgy"
date: 2006-11-07
forum: Gaming &amp; Leisure
---

### Post by Brynster on 2006-11-07
i am not a person to ask for support i think i may have fluked this but hey hoo

This is how i got Steam, HL2 and CS: source to work in through Steam using wine.

1 Fresh clean Edgy Install
2 Synaptics search and install current Wine Version (0.9.24)
3 open terminal and type ```
winecfg
```
4 close the window that opens without making any changes
5 search for TTF Tahoma in google and download the font.
6 copy font to ./wine/program files/windows/fonts folder
7 download SteamInstall.exe from [www.steampowered.com](www.steampowered.com)
8 copy steam installer to Wine C folder within the ./wine directory
9 open a terminal window and install using ```
wine c:\\SteamInstall.exe
```

Steam will install, once installed the first time it is run Wine will complain that Mozzilla control dodaar is missing do you want to install it simply click yes when prompted.

Once everything is installed highlight Counterstrike Source or HL2 and install in the usual over steam manner (i.e slowly over the internet).

Wait patientally untill installs are complete once done they should work without issue.

My (basic) howtoo is based on a clean install of Edgy using the Nvidia based drivers as installed by Automatix (Big thanks to the Automatix Team)

---

### Post by d351GuJu on 2006-11-07
I have done this before on breezy, but the performance was not so great and the video was a little choppy (on GeForce 7800GT).  I will try this out again, and let you know how it goes.  :D 

d351GuJu

---

### Post by WhiteDawn on 2006-11-07
Games make advanced calls to the API, sadly wine is not perfect, and you might experence some slowdown.

also, the current virsion of wine is now 0.9.24

---

### Post by Brynster on 2006-11-08
ok i have ammended the the howtoo.

My performance with lots of detail and higher trillinear filter etc is shocking. 

But in 1024x768 and medicore levels of graphic enhancement it plays at a steady 48-70 frames (lol doesn't sound steady) with a Athlon XP 2800 512mb of ram and a Geforce 6600GT with 128mb on board.

---

### Post by d351GuJu on 2006-11-08
OMG, I could not believe that I was able to play the game with no problems whatsoever for around 5 minutes, and then suddenly it crashes.  When I ran the Video Stress Test with Highest level, I get around 50-60FPS.  I will post more details on this later.

d351GuJu

---

### Post by d351GuJu on 2006-11-12
OK, I have attached the debug.txt file which I created as Steam.exe launched to its crash period.  Thanks :)

---

### Post by scotty2hott2k on 2006-11-12
actually wine is now 0.9.25

---

### Post by hikaricore on 2006-11-12
> **scotty2hott2k said:**
> actually wine is now 0.9.25

Which came out yesterday morning around 3am EST... no reason to get snippy

And the debian/ubuntu packages were just build this morning or late last night.  Not even in the repos yet.

---

### Post by Polygon on 2006-11-12
ive read in tutorials that you should install the Mozilla control before you run steam... but if it prompts you to install it i guess its fine

i myself have never gotten any source game to work, as it just freezes on the loading screen. But i have seen other tutorials that say you should put -directx 70 -window and some other stuff to make it less prone to crashes. Ive also read to also put -debug=none or something to the "wine steam.exe" command to stop it spewing out errors.

---

### Post by techrush on 2006-11-12
no luck here although ive gotten condition zero to work in wine on dapper.

---

### Post by Brynster on 2006-11-13
Ok your mileage may vary but i have also found that if i run winecfg from terminal and set the version to windows 98 and check the buffering box in video option the my frame rates and overall performance improives.

This is based on 

an Athlon XP 2800
512mb of ddr3200
30GB maxtor HDD
Nvidia 6600gt (128mb)
Jetway Motherboard.
Nvidia drivers as supplied by automatix (will confirm which one later when i get home)

---

