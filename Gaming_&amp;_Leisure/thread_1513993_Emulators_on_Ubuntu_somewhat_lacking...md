---
title: "Emulators on Ubuntu somewhat lacking.. ?"
date: 2010-06-20
forum: Gaming &amp; Leisure
---

### Post by razorblade_freshfade on 2010-06-20
Hi everyone, this is my first post (just lettin you know :p )

Anyways, I recently switched to Ubuntu, cause I wanted my laptop to run even faster than it did with windows 7 (it's a 4 gig ram hp laptop with a good 64 bit amd processor) and since i don't game, i found the switch to be only an improvement. However, I do have some quite annoying troubles with emulators, the only time i DO game.. 

For SNES emulating I use Snes9x and not Zsnes, because i remember from running zsnes on windows that the joypad support wasn't always that great and the interface is sluggish, while snes9x is way handier. However, running it in a small window will just work speed-wise, but running it full-screen, will go really laggy. I don't know why this is, because when i had Windows 7 I could run it full screen and it wouldn't lag at all. This i find quite weird, also because my specs, 4 gig ram, nvidia 8200, amd dual core processor 2.1 mghz, should make it run really smoothly...

Second, I find that emulating N64 goes even worse... I use mupen64, the only n64 emulator available in the sofware repository (and i wouldn't know how to manually install software so i just chose that one). I find it to be a downgrade on project 64 in almost each possible way... It runs really sluggish, the graphics sometimes glitch, the sound runs slowly, ... it's a nightmare in windowed mode, but when i do it full-screen it becomes even worse! Unplayable.. 

I wonder if anyone else has also experienced this and what his/her solutions might be to this kind of annoying problem... i have the power to play these roms in full screen with the best resolution in windows, but when i try it on ubuntu, it's like my hardware just stripped off and i got stuck with windows 98 ?

---

### Post by sakuramboo on 2010-06-20
Did you install the Nvidia proprietary drivers?

---

### Post by razorblade_freshfade on 2010-06-20
> **sakuramboo said:**
> Did you install the Nvidia proprietary drivers?

Ehm well i was thinking on doing that but i read somewhere on the site that the ubuntu drivers are just as good as the proprietery drivers... but this wouldn't make sense since i am also able to run cube 2 or wolfenstein:ET smoothly?

---

### Post by BigSilly on 2010-06-20
No dude, you'll need the Nvidia proprietary driver for proper emu fun. System/Administration/Hardware Drivers. Tick the latest one.

:)

---

### Post by razorblade_freshfade on 2010-06-20
> **BigSilly said:**
> No dude, you'll need the Nvidia proprietary driver for proper emu fun. 

:)

ooooh, i'm sorry :p i just really think i read somewhere on the site that the ubuntu drivers are just as good?


but how can i install such a proprietary driver?

---

### Post by BigSilly on 2010-06-20
Sorry, I must have just edited my post as you posted! :D  See above.

---

### Post by Perfect Storm on 2010-06-20
> **razorblade_freshfade said:**
> Ehm well i was thinking on doing that but i read somewhere on the site that the ubuntu drivers are just as good as the proprietery drivers... but this wouldn't make sense since i am also able to run cube 2 or wolfenstein:ET smoothly?

The default open source nvidia driver which are pre-installed with Ubuntu are not good with 3D stuff you need to install the restricted drivers.

Whoever told you that the default drivers are equally good with the restricted nvidia drivers are either lying or totally mis-informed.

---

### Post by razorblade_freshfade on 2010-06-20
Wait a second, i googled how to add hardware drivers to ubuntu, so i went to system -> administration -> hardware drivers and it said 'searching for hardware drivers' and then i got this list:

[[IMG]http://img714.imageshack.us/img714/4724/screenshotee.png[/IMG]](http://img714.imageshack.us/i/screenshotee.png/)

---

### Post by BigSilly on 2010-06-20
Click "Activate", then wait.

:D

That's it. :)

---

### Post by razorblade_freshfade on 2010-06-20
Yeah but I already have the current one running don't i?

---

### Post by Mike_IronFist on 2010-06-20
> **razorblade_freshfade said:**
> Yeah but I already have the current one running don't i?

No, you have to activate it, it's installed but it's not being used. Click on the "current" driver and click activate, restart, and your performance will go from lame to GOOD.

Also, if you would like to know about Emulation on Ubuntu, I've recently completed an AMAZING setup on my own laptop, running with an NVIDIA card as well.

The Emulators I am using are:
SNES9x
Kega Fusion (Sega Genesis, Game Gear, Master System, 32x, and CD)
Hu-Go! (for PCE/Turbografx-16)
SDLMAME
Mednafen (For Gameboy, GBC, and Gameboy Advance, as well as NES)

Since SDLMAME and Mednafen are rather command-line dependent, I use a frontend app called Wah!Cade.

---

### Post by BigSilly on 2010-06-20
Ah I see. If the one highlighted green is activated, then yes you're using it. You're fully up to date, yes? You could try Options/Preferences/Display in SNES9x and click "Use [however many] threads for filtering and scaling". I have a dual core CPU so I use 2 threads. Could help.

I can't imagine why you're getting this problem though. Are you using the latest driver (v.195.36.24) in System/Administration/Nvidia X Server Settings? Do you have Compiz effects enabled, such as desktop cube etc?

---

### Post by razorblade_freshfade on 2010-06-20
> **BigSilly said:**
> Ah I see. If the one highlighted green is activated, then yes you're using it. You're fully up to date, yes? You could try Options/Preferences/Display in SNES9x and click "Use [however many] threads for filtering and scaling". I have a dual core CPU so I use 2 threads. Could help.

I can't imagine why you're getting this problem though. Are you using the latest driver (v.195.36.24) in System/Administration/Nvidia X Server Settings? Do you have Compiz effects enabled, such as desktop cube etc?

No I don't use Compiz since my friend who uses Ubuntu says it's not really a plus but just a nice extra and it might sometimes slow down your performance... 

And I am running Nvidia driver 195.36.15, how do i update it to .24 then?

But my nvidia driver was already activated!

---

### Post by razorblade_freshfade on 2010-06-20
Screenie:
[[IMG]http://img412.imageshack.us/img412/7565/screeniez.png[/IMG]](http://img412.imageshack.us/i/screeniez.png/)


Notice that above, you see my processor usage, and despite the fact that it is running a few apps while also an emulator with my thrustmaster dual analog controller plugged in, it doesn't even use half of it's capacity.. however i still get laggy sound, and blue spots and squares on the screens and lagging when i shoot?

---

### Post by BigSilly on 2010-06-20
Blimey. Don't want to scare you but blue dots and squares could be a sign there's something up with the card! I recently had the fan on my 9800GT stop, and this resulted in a similar issue with sparklies on screen, then random reboots. :shock:

The updated driver came to me through the usual daily Update Manager recently. You could try System/Administration/Update Manager and see what you get.

However if that isn't the problem, have you tried different plug ins on Mupen64Plus, and also played with the settings on the other emulators? I can honestly say I have a great experience with these emu's on Ubuntu, and the performance is mostly exactly as it is on my W7 install, if not better. This doesn't help you much sadly, but I bet it's something silly somewhere. :confused:

---

### Post by hikaricore on 2010-06-20
Is that GoldenEye?  I've never had much luck running it with mupen due to lag issues ona decent system, do you have similar problems with other games?

---

### Post by Mike_IronFist on 2010-06-21
> **razorblade_freshfade said:**
> Screenie:
(IMAGE)
Notice that above, you see my processor usage, and despite the fact that it is running a few apps while also an emulator with my thrustmaster dual analog controller plugged in, it doesn't even use half of it's capacity.. however i still get laggy sound, and blue spots and squares on the screens and lagging when i shoot?

N64 emulators are the one thing I find to be lacking on the Linux side of things, and this is coming from someone who is otherwise very happy with his emulation setup. The version of mupen64plus that you can get from the Software Center is old, and the new version requires command line usage or a frontend program. Either way, it can be a pain to set up, and once it's running, it doesn't always run that great either. That being said, you can get some N64 games to run very well if you put in the effort, it's just a pain in the butt.

All the other emulators I use, and I mean this, ALL OF THEM, work perfectly with a little bit of configuration. You might have to edit config files and stuff like that, but it's so worth it - the performance I get simply blows Windows out of the water.

---

### Post by Gimme_A_Freaking_Break on 2010-06-21
Hi guys, it's me razorblade_freshfade, for some bizarre reason, Ubuntu forums keep banning me cause I once flamed a guy who flamed another guy first. Consequently I get banned each time i create an account, but conveniently for them, they never ever let me defend myself but just instaban me, so i'm forced to keep creating new accounts. But anyways, this isn't of the matter.

Goldeneye isn't the only thing that isn't working, i've tried it with mario kart 64 and big mountain 2000: weird polygonal colored fields appear in the middle of the emulator screen. I don't know what's causing this at all, and it makes me kind of sad since i could run it so well on windows... 

Are there any other n64 emulators available for Ubuntu or am I stuck with mupen64? And how do i install a newer version because the explanation on the site looked quite complicated for a noob like me.

---

### Post by BigSilly on 2010-06-21
Mupen64Plus really is the best there is. You shouldn't be having these issues you describe, though Hikari is right - Goldeneye isn't that great on Mupen. 

Have you tried the other graphics plugins for Mupen? I suppose you could use Project 64 in WINE. I believe that works fine.

---

### Post by doorknob60 on 2010-06-22
By the way, are you using Mupen64plus or just plain old Mupen64? You definetely need to be using mupen64plus, it's much better. Also, Project64 works very well in Wine, but for me most games work fine in Mupen (mess around with the different graphics plugins, some work better than others, and certain games work better with certain plugins).

---

### Post by Pangoria on 2010-06-25
> **razorblade_freshfade said:**
> 
For SNES emulating I use Snes9x and not Zsnes, because i remember from running zsnes on windows that the joypad support wasn't always that great and the interface is sluggish, while snes9x is way handier. However, running it in a small window will just work speed-wise, but running it full-screen, will go really laggy. I don't know why this is, because when i had Windows 7 I could run it full screen and it wouldn't lag at all. This i find quite weird, also because my specs, 4 gig ram, nvidia 8200, amd dual core processor 2.1 mghz, should make it run really smoothly...

Had same issue with SNES9x.  Switched the display mode to scanlines or something like that, and suddenly fullscreen was fine with no lagging.

Also I increased the ms slider for the sound, (I'm not at home so I can't remember the actual name).

---

### Post by Kolk1604 on 2010-07-11
> **Mike_IronFist said:**
>  
Also, if you would like to know about Emulation on Ubuntu, I've recently completed an AMAZING setup on my own laptop, running with an NVIDIA card as well.
 
The Emulators I am using are:
SNES9x
Kega Fusion (Sega Genesis, Game Gear, Master System, 32x, and CD)
Hu-Go! (for PCE/Turbografx-16)
SDLMAME
Mednafen (For Gameboy, GBC, and Gameboy Advance, as well as NES)
 
Since SDLMAME and Mednafen are rather command-line dependent, I use a frontend app called Wah!Cade.
 
Hey, do you by chance have a guide how to set up Wahcade? Or maybe post your config/setup? I've been looking forever for a good Wahcade tutorial, but I can't find one. The only time I've used Wahcade is with thezerogameproject, and that was just a bash script that does everything for you. 
 
Thanks :)

---

### Post by shaunsmith_99 on 2010-07-13
> **Pangoria said:**
> Had same issue with SNES9x.  Switched the display mode to scanlines or something like that, and suddenly fullscreen was fine with no lagging.

Also I increased the ms slider for the sound, (I'm not at home so I can't remember the actual name).

 This is a good Thread! I wasted most of my High School Career on GoldenEye (N64) and I plan on doing much of the same my last semester of Grad School. :popcorn:

 I too have found Mupen64 lacking compared to it's windows counterparts, although I've found a few little tweaks that keep it smooth - For example, regardless of the setup I use, the "? /" key always crashes the emulator. My solution: Don't use that Key....

 I'd like to go buy a good N64-ish controller - any suggestions?

---

### Post by Åtta on 2010-07-13
> **shaunsmith_99 said:**
> I too have found Mupen64 lacking compared to it's windows counterparts, although I've found a few little tweaks that keep it smooth - For example, regardless of the setup I use, the "? /" key always crashes the emulator. My solution: Don't use that Key....

 I'd like to go buy a good N64-ish controller - any suggestions?

You shouldn't be using mupen64 since it's not being developed anymore. Mupen64plus is a lot better. The latest version has been largely rewritten, which means there's only a command-line interface. It's pretty simple though, so it shouldn't be much of a problem. There are some guis out there that you can use, but they're not all that mature yet.

---

### Post by WarrenSH on 2010-07-13
> **Kolk1604 said:**
> Hey, do you by chance have a guide how to set up Wahcade? Or maybe post your config/setup? I've been looking forever for a good Wahcade tutorial, but I can't find one. The only time I've used Wahcade is with thezerogameproject, and that was just a bash script that does everything for you. 
 
Thanks :)

A setup/config tutorial with screenshots would be great :popcorn:

---

### Post by JustinR on 2010-07-13
On an unrelated note. Project64 (Nintendo64 emulator) works flawlessly under Wine.

---

### Post by WarrenSH on 2010-07-15
> **kolk1604 said:**
> hey, do you by chance have a guide how to set up wahcade? Or maybe post your config/setup? I've been looking forever for a good wahcade tutorial, but i can't find one. The only time i've used wahcade is with thezerogameproject, and that was just a bash script that does everything for you. 
 
Thanks :)

bump

> **warrensh said:**
> a setup/config tutorial with screenshots would be great :popcorn:

bump

---

