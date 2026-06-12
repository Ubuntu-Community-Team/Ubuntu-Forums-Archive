---
title: "Steam Games, and mic broken"
date: 2007-04-24
forum: Gaming &amp; Leisure
---

### Post by duncan_nz on 2007-04-24
Hi,

I'm just wondering if anyone has got their mics to work using steam based games such as, Counterstrike Source, Day of Defeat Source, or any of the hl one mods such as cs or dod etc, when they are run using WINE.

I've tried to get my one to work, but when I listen to what it sounds like (using voice_loopback 1 a console command from the game) all I can hear is just some crazy buzzing noise!

I have a decent computer, but I'm using the inbuilt sound (AC97 chip) and its worked for sound mixing in windows runnning the exact same games.

If anyone out there has got their mic working in these games, could they please post how they did it? :)

Thanks!

---

### Post by braveerudite on 2007-04-24
Is it hard to get steam to work with Ubuntu? Are you using wine?


Can I just install wine the steam and thats it?

---

### Post by duncan_nz on 2007-04-24
No its not hard, I'm using 7.04 and the latest wine. You can install steam, but you need an account to log into. Anyone can make an account, but to play a game you have to buy it first.

---

### Post by braveerudite on 2007-04-24
> **duncan_nz said:**
> No its not hard, I'm using 7.04 and the latest wine. You can install steam, but you need an account to log into. Anyone can make an account, but to play a game you have to buy it first.

I do have an account but my problem now is that when I try putting my user name and password there is no text on th elogin windows.

Example

The words: Username:
Password:

Cance:
Continue:

What gives.

---

### Post by duncan_nz on 2007-04-24
Ahh thats because you need the "Tahoma" font in your wine font directory. Copy it froma  windows partition or download it etc.

Put it in ~/.wine/drive_c/windows/fonts

or something similar.

---

### Post by abowman on 2007-04-24
My mic just works with my old Soundblaster Live! card.  I had a lot of trouble with my motherboard's built in sound.  I recommend getting a sound card that is known to work well in Linux.  It will save you a lot of time trying to figure out how to get sound working in games like Enemy Territory and Quake 3.

---

### Post by braveerudite on 2007-04-24
> **duncan_nz said:**
> Ahh thats because you need the "Tahoma" font in your wine font directory. Copy it froma  windows partition or download it etc.

Put it in ~/.wine/drive_c/windows/fonts

or something similar.

I understand but right when I was about to paste them there was no option to do so. I'm using 

Applications-->Accessories-->Wine File


I don't know any other way.

---

### Post by duncan_nz on 2007-04-24
> **abowman said:**
> My mic just works with my old Soundblaster Live! card.  I had a lot of trouble with my motherboard's built in sound.  I recommend getting a sound card that is known to work well in Linux.  It will save you a lot of time trying to figure out how to get sound working in games like Enemy Territory and Quake 3.

Ok, looks like I'll have to shell out, I dont want to spend too much though. I only have one headset and a mic so I dont need to get all the mod cons etc.

How does one find out which sound cards work well with linux?

@braveerudite

Just use cntrl c and cntrl v man, its the short cut for copy and paste

---

### Post by bluewagon on 2007-04-24
go to home folder, push ctrl+h, find .wine -> drive_c -> windows -> fonts
ctrl+h shows hidden files

edit: I've been having trouble with sound with steam games too, whenever i try to run both vent and a steam game, which ever program i ran first, gets dibs on my sound, the other program is muted :(

---

### Post by duncan_nz on 2007-04-24
I'm looking at buying a Creative Sound Blaster 5.1, its cheap, and better than onboard apprently.

[http://www.nzoczone.com/product_info.php?products_id=2464](http://www.nzoczone.com/product_info.php?products_id=2464)

---

### Post by braveerudite on 2007-04-24
> **bluewagon said:**
> go to home folder, push ctrl+h, find .wine -> drive_c -> windows -> fonts
ctrl+h shows hidden files

edit: I've been having trouble with sound with steam games too, whenever i try to run both vent and a steam game, which ever program i ran first, gets dibs on my sound, the other program is muted :(

Thx that tip work.

---

### Post by duncan_nz on 2007-04-24
@bluewagons edit:

Do a search for aoss, it might be helpful for you :)

---

### Post by abowman on 2007-04-25
> **duncan_nz said:**
> I'm looking at buying a Creative Sound Blaster 5.1, its cheap, and better than onboard apprently.

[http://www.nzoczone.com/product_info.php?products_id=2464](http://www.nzoczone.com/product_info.php?products_id=2464)

I have a 5.1 and a Live! and I found that the Live! card works better for me for some reason.

---

### Post by aknapp on 2007-05-02
> **abowman said:**
> I have a 5.1 and a Live! and I found that the Live! card works better for me for some reason.

How exactly do you have your setup that allows you to use your mic in Counter-Strike?

---

### Post by AndrewRiedi on 2007-05-02
There has been and will be a bunch more work on the Sound code in Wine for ALSA.  Type ```
winecfg
``` in a terminal.  Go to the Sound tab, uncheck everything, then recheck only ALSA.

A couple months ago the ALSA driver sucked, but it is getting better every release now.  It will eventually solve all of your problems, once it is complete.  Again, it is not finished yet, but wait 'till the end of summer and hopefully it should be in great shape.

---

### Post by aknapp on 2007-05-02
Forgive my ignorance, but how do I need the mixers setup? I have onboard nvidia and sound blaster live. Also, in System>Prefs>Sound, what does that need to look like? Thanks.


Also, I did as you suggested and unchecked everything (only OSS was checked) and checked only ALSA, but when I launch CS it only shows the backdrop of the two dudes holding guns, never loads the menu (find servers, options, etc)

---

### Post by aknapp on 2007-05-11
> **aknapp said:**
> Forgive my ignorance, but how do I need the mixers setup? I have onboard nvidia and sound blaster live. Also, in System>Prefs>Sound, what does that need to look like? Thanks.


Also, I did as you suggested and unchecked everything (only OSS was checked) and checked only ALSA, but when I launch CS it only shows the backdrop of the two dudes holding guns, never loads the menu (find servers, options, etc)

Does anyone know?

---

### Post by FunnyLookinHat on 2007-08-07
I think my problem is related to the mixers too...  for some reason it won't recognize my "Microphone" input as active...   when I try to use the mic it just sends a high frequency/pitch whining noise.

Go figure???  I'll try missing with winecfg I suppose, I was told that using OSS was actually better so I'll switch it back to ALSA.

---

