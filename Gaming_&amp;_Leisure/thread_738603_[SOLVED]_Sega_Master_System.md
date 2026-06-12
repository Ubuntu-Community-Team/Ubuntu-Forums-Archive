---
title: "[SOLVED] Sega Master System"
date: 2008-03-28
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2008-03-28
Hi,
I have downloaded mekanix and mednafen as I heard these can play Sega Master System games.

I can not get neither to work. 

If anyone has got  mekanix and mednafen to work, please reply here. Alternatively has anyone got Sega Master System games to work in other programs in Ubuntu?

Thanks.

---

### Post by GSZX1337 on 2008-03-28
I've been busting my *** looking for an SMS for Linux. The only one I found was Mednafen, but I haven't installed it yet. Never heard of Mekanix, are you talking about [MEKA]("http://www.smspower.org/meka/")?

---

### Post by DarkSim on 2008-03-28
If you don't mind using Wine there is Kega Fusion. Thats what I use for an SMS emulator.

[http://www.eidolons-inn.net/tiki-index.php?page=Kega](http://www.eidolons-inn.net/tiki-index.php?page=Kega)

The one I can think of that is native is called Dega I believe.

---

### Post by GSZX1337 on 2008-03-28
> **DarkSim said:**
> If you don't mind using Wine there is Kega Fusion. Thats what I use for an SMS emulator.

[http://www.eidolons-inn.net/tiki-index.php?page=Kega](http://www.eidolons-inn.net/tiki-index.php?page=Kega)

The one I can think of that is native is called Dega I believe.

Aren't there fullscreen graphics problems with Kega Fusion in Wine? I'm thinking of having Virtual Box fullscreened in a workspace and have Kega run fullscreen in that.

---

### Post by FranMichaels on 2008-03-28
Mednafen runs them, just a matter of right clicking and open with mednafen. :)


Press F1 in mednafen for hotkeys :KS

Fan translated, ips softpatched. Love the hackers. :guitar:

---

### Post by mister_k81 on 2008-03-28
I haven't seen any good stand alone Sega Master System emulators for linux, But I will definitely add another vote for Mednafen.   

Another option is [XE-Mulitisystem](http://www.xe-emulator.com/), which has good Sega Master System compatibility. You might want to read the installation instructions first though: 

[http://ubuntuforums.org/showpost.php?p=3993413](http://ubuntuforums.org/showpost.php?p=3993413)

---

### Post by acoustibop on 2008-03-28
MEKA is buggy to the point of being unusable in Linux - a pity, because it's a great SMS emulator in Windows.  I could never get Medafen to play Master System games, although it's supposed to; I've been meaning to try Dega, but haven't yet.

It's a great pity, because some of my favourite games are on the Master System, and there just don't seem to be any really workable emulators for it in Linux. :(

---

### Post by Rytron on 2008-03-29
> **GSZX1337 said:**
> I've been busting my *** looking for an SMS for Linux. The only one I found was Mednafen, but I haven't installed it yet. Never heard of Mekanix, are you talking about [MEKA]("http://www.smspower.org/meka/")?

Hi,
The title is Meka, when I go to this [link]("http://www.smspower.org/meka/download.shtml#version070") the package is mekanix. Don't know why. Also there is a DOS version, I was considering trying to get it to work via dosbox.

---

### Post by acoustibop on 2008-03-29
Yes, that's right, the Linux version is called Mekanix, Rytron.  Unfortunately it's buggy as anything and not really workable - all the more of a pity because MEKA is such a nice emulator in Windows.

> **FranMichaels said:**
> Mednafen runs them, just a matter of right clicking and open with mednafen. :)


Press F1 in mednafen for hotkeys :KS

Fan translated, ips softpatched. Love the hackers. :guitar:

You convinced me; I'm going to have to try Mednafen again, Fran - Phantasy Star is such a cracker of a game! ;)

---

### Post by FranMichaels on 2008-03-29
> **acoustibop said:**
> 
You convinced me; I'm going to have to try Mednafen again, Fran - Phantasy Star is such a cracker of a game! ;)

:biggrin: Go with it :)
I should really write a review with screenscaps for mednafen on my never updated blog. it is one heck of an emulator IMHO. :KS

---

### Post by Rytron on 2008-03-29
Hi,
I could not get mednafen to work by right clicking on the master system rom.
I presume that the ms roms must still be left zipped. Is this correct?

I tried the terminal. Here is the result:

```
myname@Tron:~/Desktop/-mastersyst$ mednafen 'Lucky Dime Caper.zip' 
Starting Mednafen 0.8.1
 Loading settings from "/home/myname/.mednafen/mednafen.cfg"...
 Initializing joysticks...
  Joystick 0 - Microsoft&#65533; Microsoft&#65533; SideWinder&#65533; Game Pad USB - Unique ID: 42190af389429475
 Loading Lucky Dime Caper.zip...

Unrecognized file format.  Sorry.
```

What must I do?
:confused:

---

### Post by FranMichaels on 2008-03-29
Try renaming the file in the zip to end with .gg or .sms
That should do it :)

P.S. Are you running mednafen 0.8.7?

EDIT: D'oh. Noticed the output, you need a newer version. Yours is 0.8.1, no sms/gg support in that release.

I have a deb I made with checkinstall, should work since you have the old one installed (all the dependencies) but it's 1.8mb... I could upload to rapidshare or something. Just let me know.

---

### Post by Rytron on 2008-03-29
Hi FranMichaels,
You are so knowledgeable.

I got mednafen_0.8.7 here
[http://ftp.debian.org/debian/pool/main/m/mednafen/]("http://ftp.debian.org/debian/pool/main/m/mednafen/")

When I clicked on it, I got this message:

dependency is not satisfiable: libasound2

If it is not too much trouble, could you link your mednafen_0.8.7 on rapidshare?

Or else, how do I solve the libasound2 problem?

---

### Post by acoustibop on 2008-03-29
Interesting, Menafen 0.8.7 is actually in the Hardy repositories...

libasound2 is in the repositories too, Rytron - I'm in Hardy beta ATM but I'm pretty sure it'll be in the Gutsy ones too.  Either install it from Synaptic or do```
apt-get update

apt-get install libasound2
```

**Edit:** ah, looks like you may need libsdl-net1.2 as well.  Install it the same way.

---

### Post by FranMichaels on 2008-03-29
Thank you :KS

[http://rapidshare.com/files/103384244/mednafen_0.8.7-1_i386.deb.html](http://rapidshare.com/files/103384244/mednafen_0.8.7-1_i386.deb.html)

---

### Post by acoustibop on 2008-03-29
Thank *you* if you're thanking me, Fran - it works! :D

Now to figure out how to configure it... ;)

---

### Post by FranMichaels on 2008-03-29
> **acoustibop said:**
> Thank *you* if you're thanking me, Fran - it works! :D

Now to figure out how to configure it... ;)

And Rytron :)

But anyway, it is easy once you've done it once.

---

### Post by Rytron on 2008-03-30
> **FranMichaels said:**
> Thank you :KS

[http://rapidshare.com/files/103384244/mednafen_0.8.7-1_i386.deb.html](http://rapidshare.com/files/103384244/mednafen_0.8.7-1_i386.deb.html)

Hi FranMichaels, that version works a treat. I was able to start dime caper and bubble bobble but about eight other games would not start. It does not seem to make a difference if you leave the extension as .zip / .gg / .ms as both dime caper and bubble bobble worked under each extension type. I dont know why the other master system games did not start.

I presume that the old Mednafen does not need to be uninstalled and that the newer Mednafen just overwrites the old one. Would this be true?

Also I am perplexed as to how to configure gamepad controls. The interface seems very user unfriendly. I tried F1 but am unsure as to using the interface.

:(

---

### Post by acoustibop on 2008-03-30
Quite simple, Rytron - see FAQ on the Mednafen site.  Press Alt+Shift+1, then you'll be asked to input the keys/buttons for each control - you'll have to press each twice.

One annoying thing, though - although I configured a button on my controller as Pause, and it appears to have been accepted, it doesn't work - you need the Pause control to change weapons, armour, special devices etc in Wonderboy: the Dragon's Trap, and it won't allow me to - any ideas, Fran?  I can't find anything relating to this in their forum.

---

### Post by GSZX1337 on 2008-03-30
MEKA got a Platinum in Wine.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6478](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6478)

---

### Post by FranMichaels on 2008-03-30
> **acoustibop said:**
> Quite simple, Rytron - see FAQ on the Mednafen site.  Press Alt+Shift+1, then you'll be asked to input the keys/buttons for each control - you'll have to press each twice.

One annoying thing, though - although I configured a button on my controller as Pause, and it appears to have been accepted, it doesn't work - you need the Pause control to change weapons, armour, special devices etc in Wonderboy: the Dragon's Trap, and it won't allow me to - any ideas, Fran?  I can't find anything relating to this in their forum.

Never ran into that issue myself... I would suggest try to configure it with some other button or maybe enter on the keyboard. Maybe it has some issue mapping to your controller? In that case a bug report would be in order. 

And Rytron, if certain games do not load, it is either that it is unsupported or just a bad rom file. So my advice is try a different one.

---

### Post by acoustibop on 2008-03-30
I don't think it's failing to map to the button, Fran, it's just that the Pause function doesn't seem to be working - although I'll check it out.

I suppose it's the sort of thing that could slip by easily - most people wouldn't use the Pause function anyway.  But there are games where it has another function. :(

**Edit:** nope, tried configuring Pause to another button, and to a keyboard key.  No luck.  I checked in the configuration file as well; the appropriate button or key is being configured.  It would seem the Pause function isn't working.  :(

---

### Post by GSZX1337 on 2008-03-30
I've tried [Fusion]("http://http://emulator-zone.com/doc.php/genesis/fusion.html") in Wine. It works fine, although you can't right click.

---

### Post by FranMichaels on 2008-04-03
> **acoustibop said:**
> 
I suppose it's the sort of thing that could slip by easily - most people wouldn't use the Pause function anyway.  But there are games where it has another function. :(


Your bug report paid off :)
From mednafen 0.88 changelog

"SMS: SMS pause and 2-player support were erroneously commented out. Fixed."

Grab it here.

[http://mednafen.sourceforge.net/](http://mednafen.sourceforge.net/)

If anyone needs a deb built, let me know, and I'll upload it to rapidshare :KS

---

### Post by acoustibop on 2008-04-04
A .deb would be very welcome, please, Fran! ;)

---

### Post by FranMichaels on 2008-04-04
> **acoustibop said:**
> A .deb would be very welcome, please, Fran! ;)

[http://rapidshare.com/files/104964065/mednafen_0.8.8-1_i386.deb.html](http://rapidshare.com/files/104964065/mednafen_0.8.8-1_i386.deb.html)

Made with checkinstall, should work fine if you have a previous version of medafen installed (since the runtime dependencies are the same.)

---

### Post by wingnux on 2008-04-05
I use "Xe" for sms/gen/nes/gb/ngpc... emulation, it's really good and GUI-driven :)

---

### Post by acoustibop on 2008-04-05
Many thanks, Fran - will this run Ok on Hardy (should have changed my profile by now, I guess!)?

It works!  Vampire Dragon,you haven't seen me for a long time - get your insurance paid up now! :D

Many thanks again, Fran!

---

### Post by frenchn00b on 2008-12-21
> **DarkSim said:**
> If you don't mind using Wine there is Kega Fusion. Thats what I use for an SMS emulator.

[http://www.eidolons-inn.net/tiki-index.php?page=Kega](http://www.eidolons-inn.net/tiki-index.php?page=Kega)

The one I can think of that is native is called Dega I believe.

hmm hmm we are using linux here :) 
thanks anyhow

---

### Post by frenchn00b on 2008-12-21
```
/tmp/mekanix$ ./meka.exe

Meka 0.70 (c) Omar Cornut (Bock), Hiromitsu Shioya, Marat Faizullin & co.
--
Loading MEKA.MSG (messages)..
Initializing Allegro...
Loading MEKA.CFG (configuration)... File not found!
Running setup...
[Setup]
Please select your audio device:
   0. Silence
   1. Linux Voxware
1
Loading MEKA.NAM (games names)...
Loading MEKA.PAT (patches)...
Loading MEKA.FDB (filenames database)... File not found!
Loading MEKA.THM (interface themes)...
Loading MEKA.BLT (video modes / blitters)...
Loading MEKA.INP (inputs sources definition)...
Loading MEKA.DAT (resources)...
Initializing joystick... none found.
Initializing graphical user interface...
Initializing sound system...
 - Initializing sound card @ 44100 Hz
 - Error opening Audio system. Try a different card and/or sample rate.
```

it gives error message with the sound :( MEKA :(

---

### Post by FranMichaels on 2008-12-22
Use mednafen or sdlmess instead? 
Both support sms/gg games nicely.

---

### Post by frenchn00b on 2008-12-22
> **FranMichaels said:**
> Use mednafen or sdlmess instead? 
Both support sms/gg games nicely.

my mednafen, :( doesnt work with sms, hence:
```
~$ mednafen --version
Starting Mednafen 0.6.5

```

which version of mednafen do you use plz ?

---

### Post by mister_k81 on 2008-12-22
You definitely might want to try something newer than 0.6.5, the latest versions are 0.8.9 and 0.8.A. 

Sources here: [http://sourceforge.net/project/showfiles.php?group_id=150840&package_id=166686](http://sourceforge.net/project/showfiles.php?group_id=150840&package_id=166686)

Official website here: [http://mednafen.sourceforge.net/releases/](http://mednafen.sourceforge.net/releases/)

---

### Post by trlkly on 2008-12-23
> **frenchn00b said:**
> hmm hmm we are using linux here :) 
thanks anyhow

Your point? Last time I checked, Wine runs on Linux. It's kinda the whole point.

---

