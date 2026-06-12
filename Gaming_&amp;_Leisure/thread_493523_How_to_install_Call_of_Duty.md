---
title: "How to install Call of Duty"
date: 2007-07-05
forum: Gaming &amp; Leisure
---

### Post by cogadh on 2007-07-05
I've been trying to install Call of Duty: Game of the Year Edition with Wine and I've gotten past the whole "can't swap the CDs" problem, but the install craps out after I have to swap back to the first CD. Since the Loki installers are no longer available, does anyone have a trick for getting this game installed properly?

---

### Post by cogadh on 2007-07-06
No ideas?

---

### Post by weblordpepe on 2007-07-06
Try a no-CD crack. I cannot stand having to put in the CD all the time.
[http://www.megagames.com]("http://www.megagames.com")

---

### Post by EvilMarshmallow on 2007-07-06
I too am having the same problem.

How would a no-cd crack help on installation though?

---

### Post by weblordpepe on 2007-07-06
Oh I see.
Well install it in Windows or an emulator, and then use the game folder with a no-cd crack.

---

### Post by cogadh on 2007-07-06
Tried that, it doesn't work. The install fails before it can make some required registry entries. Copying a Windows install of the game won't give you those entries. I have no idea what those entries are, so I can't even manually create them.

---

### Post by weblordpepe on 2007-07-06
Hmm I copied the install from my XP machine & fired it up in Wine. Runs perfectly.

---

### Post by cogadh on 2007-07-06
How exactly are you launching it? Mine fails to start without even producing any error messages from Wine in the terminal.

---

### Post by weblordpepe on 2007-07-06
I went to the terminal and changed to the directory where call of duty is.
typed wine CoDSP.EXE
It said that it crashed the previous time it loaded (this is the first time Ive ran it) and asked if i want to launch in safe mode.
I clicked OK
Then it asked me to autodetect my hardware & change the settings. I clicked Yes the first time & It broke everything. Click No to autodetect your settings. 

It works flawlessly for me. I have a no-cd crack.

---

### Post by cogadh on 2007-07-06
I think the crack is it. I just installed one and it works now. That's a little odd, since usually wine throws a bunch of errors when it encounters copy protection problems.

---

### Post by weblordpepe on 2007-07-06
Cool well hey at least it works. Does it run well? It runs flawlessly for me. Pretty fast too I can bump the resolution way up.

---

### Post by cogadh on 2007-07-07
It works fantastic, just as good if not better than on Windows. I just got the United Offensive expansion installed too, it runs just as well. Thanks for the help!

---

### Post by weblordpepe on 2007-07-07
Dont thank me, thank the Wine project ;)
I am more & more impressed with Wine every day.

---

### Post by EvilMarshmallow on 2007-07-07
I still can't get the multiple-cd installation to go right.  I install the first disk, and it allows me to do 

wine eject

on it, but it says my second disk is blank when I put it in.  Once I exit the installation process, and open the cd, it shows the files... it's as if it's not getting mounted properly during install.  Anyone have any suggestions?  I don't have Windows at all so I can't copy it from there.

---

### Post by cogadh on 2007-07-07
Now that I am a little more familiar with how Wine works, I am definitely impressed with it. I went from having no working Windows games to having quite a list of working games in a matter of weeks:
[list][*]American McGee's Alice
[*]Star Trek Armada 2
[*]GTA Vice City
[*]Hitman 2
[*]Hitman Contracts (with screwed up cutscenes, still working on that)
[*]Star Wars Knights of the Old Republic
[*]Star Wars Knights of the Old Republic II (no sound though, also still working on that)
[*]Call of Duty
[*]Call of Duty: United Offensive
[*]Vampire: the Masquerade - Redemption
[*]Tribes 2
[*]Lego Digital Designer (for my son... no, really)
[*]Blood Omen: Legacy of Kain
[*]X-COM Interceptor
[*]Worms 2
[*]Pong[/list]

The only games that don't work at all for me are (either won't install or do install but don't run):
[list][*]Tron 2.0
[*]Freedom Force
[*]Vampire: The Masquerade - Bloodlines
[*]Star Trek Armada
[*]Advent Rising
[*]Star Wars Shadows of the Empire (installs and runs, but no character or enemy graphics)
[*]Transformers: Beast Wars[/list]

And I still have yet to try running:
[list][*]Freelancer
[*]Mechwarrior Vengeance
[*]American McGee's Scrapland
[*]Outwars
[*]X-Wing vs Tie Fighter
[*]X-Wing vs Tie Fighter: Balance of Power
[*]Tomb Raider: The Last Revelation[/list]
As you can see, I haven't thrown out a game since 1995, in the hopes that they would some day be playable again. Well, that packrat nature is finally starting to pay off with Wine!

---

### Post by cogadh on 2007-07-07
> **EvilMarshmallow said:**
> I still can't get the multiple-cd installation to go right.  I install the first disk, and it allows me to do 

wine eject

on it, but it says my second disk is blank when I put it in.  Once I exit the installation process, and open the cd, it shows the files... it's as if it's not getting mounted properly during install.  Anyone have any suggestions?  I don't have Windows at all so I can't copy it from there.
The only way I could get the CD swap to work was first make sure that Wine is emulating a virtual desktop, then run this:
```
wine /media/cdrom0/setup.exe
```
When prompted for the second CD, I open a second terminal and do this:
```
wine eject d:
```
I insert the second CD and wait for it to automount, then click on the OK button in the install. When it asks to go back to the first CD, I do the same wine eject command and swap the CDs, however this is the point that the installation fails for me. It produces some kind of error indicating that an install file has become corrupt. I think it might be a symptom of the lack of copy protection support, but I'm not sure.

Without a Windows installation to copy the install from and since Loki has removed the installer for it from their site, I really don't see how you can get past the problem.

---

### Post by weblordpepe on 2007-07-07
Warez!
Hey its not illegal if you own the game, right?

---

### Post by Vendetta_NZ on 2007-07-07
Does anyone know if its possible to run Call of Duty 2 on Wine or Cedega?

---

### Post by cogadh on 2007-07-08
Yes it is possible, check Wine's AppDB if you ever want to find out what can and cannot run in Wine:
[http://appdb.winehq.org/appview.php?iVersionId=3794](http://appdb.winehq.org/appview.php?iVersionId=3794)

---

### Post by berserker on 2007-07-08
Does PB work for CoD 1.5 without the loki installation method?  I installed it a long time ago using the loki installer but somewhere along the way PB stopped working and kicks me off a server after a few seconds with a ```
Unknown Windows API function
``` error.

---

### Post by cogadh on 2007-07-08
I've heard that if you switch the Windows version in Wine to Windows 98, PunkBuster problems go away. However, I have also read that PunkBuster doesn't work in Wine at all...

---

### Post by weblordpepe on 2007-07-08
I had no end of problems trying to play online using Wolfenstein Enemy Territory for Windows under Wine. Yeah I got the unknown API error as well. Haven't tried that Windows 98 trick though.

Of course, I just downloaded & installed the Linux native version ;) Go iD software!

---

### Post by cogadh on 2007-07-10
This is kind of interesting...

I just downloaded and installed the first alpha release of Wine-Doors and it inlcudes an installer for Call of Duty 1 and 2. I'm trying the CoD 1 installer right now to see if it will work for cleanly installing the game, I'll post back the results.

Also, if you are interested, it also includes installers for Prey, Steam, Half-Life 2, World of Warcraft and Warcraft.  Check out the site for more info: [http://www.wine-doors.org/](http://www.wine-doors.org/)

EDIT - UGH! Nevermind, this app is still too immature, none of it actually works beyond the initial launch/configuration.

EDIT2 - I spoke too soon, I just broke it when I didn't allow the CoD install script to completely download. It's running again, we'll see what happens next...

EDIT3 - Nope, it wasn't me, the app really doesn't work, at least for installing CoD. Looks like we need to wait for this to mature some more before it can be used regularly, but at least it looks very promising.

---

### Post by weblordpepe on 2007-07-10
yeah it looks cool

---

### Post by Rytron on 2011-03-07
Has anyone managed to get Call of Duty 1 to work in WINE?

---

