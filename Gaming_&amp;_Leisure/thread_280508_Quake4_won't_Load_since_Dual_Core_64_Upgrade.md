---
title: "Quake4 won't Load since Dual Core 64 Upgrade"
date: 2006-10-19
forum: Gaming &amp; Leisure
---

### Post by LateNighter on 2006-10-19
I recently upgraded my PC to a Dual Core 64bit.
 From a Sempron 64bit Single Core.

 Specs are as follows.

 PcChips A33G Mainboard.                                                          XFX PCIe Nvidia GeForce 6200 128mb DDR with Turbocache Supporting 256mb
 512mb DDR2 PC3200 Memory
 AMD Athlon 64 3800+ X2 Socket AM2 Processor

 I can run DOOM3 fine.

 But Quake4 installs fine, but when I go to run it it hangs with the following message.

 bipolarpenguin@manicmess:~$ quake4
./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory
bipolarpenguin@manicmess:~$    

 It says No Such file or directory?
 But I went back and checked the file is there.

 On up above it also said I met minimal Support for the game.
 With a 1gig CPU.
 It's a Dual Core running at 2gig.
 
 Could it being a Dual Core be part of the problem?


 I've never had this problem before.

 Does anyone have any ideas on whats wrong?

 Or has anyone ever had this problem and fixed it?

 Any Help I'd be most Grateful....](*,)

---

### Post by Lord Illidan on 2006-10-19
Perhaps you need to run quake4-smp

---

### Post by LateNighter on 2006-10-19
> **Lord Illidan said:**
> Perhaps you need to run quake4-smp

 I just did and got the samething except the smp, readout.
 Here it is...

 bipolarpenguin@manicmess:~$ '/usr/local/games/quake4/quake4smp.x86'
/usr/local/games/quake4/quake4smp.x86: error while loading shared libraries: libSDL-1.2.id.so.0: cannot open shared object file: No such file or directory
bipolarpenguin@manicmess:~$

 I can't understand it for the life of me.

 I thought it might have been a sound issue at first.
 So I put Mepis on for a few to see if it made any difference.
 I tried all the different sound drivers avaliable, and they all worked.
 But thats under the 32bit realm.

 Because unless I set my Sound System to oss, I'll get the same reading.
 When trying to run DOOM3.

 But thats another Story. Anymore ideas anyone???  Thanks again.:KS

---

### Post by LateNighter on 2006-10-21
> **Lord Illidan said:**
> Perhaps you need to run quake4-smp

 OK you were part RIGHT....;) 

 I did need the Quake4smp.x86 BUT...

 I was focusing on the .exe and not the Shell Script.:-k 

 I went ahead and Copy/Paste the Shell Script in Terminal KICKED Up and runs fine...

 It even now detects my Dual Core CPU.8) 

 Only a couple of small glitches however. Which I can LIVE with.

 It has to be run in Gnome and not the KDE Desktop.
 I get Sound in Gnome, but no Sound in KDE.:rolleyes: 

 And for anyone out there who has been having a Problem with the same thing.
 There is a Patch out there for Quake4 in Linux, But don't use it.
 But as a LAST Resort.

 If you do and once it realizes you have a Dual Core it'll give you the BSOD real quick, and freeze you up real quick.
 You'll then have to Restart your machine.

 And then do a CLEAN Reinstall of Quake4.

 I figured this out about 3 reinstalls later...:oops: 8-[ 

 Anyway I'm off to FRAG me some STROGG... "ENJOY":twisted:

---

### Post by Lord Illidan on 2006-10-21
As for sound in KDE, maybe you need to disable artsd.
```

killall artsd
``` before running quake4.

---

### Post by LateNighter on 2006-10-22
> **Lord Illidan said:**
> As for sound in KDE, maybe you need to disable artsd.
```

killall artsd
``` before running quake4.

 Thanks for the Extra Imput I'll try it and let you know if it works..:D

---

### Post by LateNighter on 2006-10-22
> **Lord Illidan said:**
> As for sound in KDE, maybe you need to disable artsd.
```

killall artsd
``` before running quake4.

 Sorry NO SOAP....

 Oh Well THANKS for the suggestion it was worth a shot....:cool:

---

### Post by Lord Illidan on 2006-10-22
> **LateNighter said:**
> Sorry NO SOAP....

 Oh Well THANKS for the suggestion it was worth a shot....:cool:

strange :(

but does it work well in Gnome at least

---

### Post by LateNighter on 2006-10-22
> **Lord Illidan said:**
> strange :(

but does it work well in Gnome at least

 Yes it does runs "JUST FINE"

 The patch I'd mentioned was disigned to keep the game from getting a bit of lag, and allowing it to freeze for a couple of seconds, when you are heading into a area that has quite a bit of Graphics being loaded , but this doesn't happen always.
 Just at certain points.

 I tried the Patch but it it works Real Well if you like the BSOD:(  that is.

 But it is more then Playable...:mrgreen: 
 And everybit as fun.

 The patch was made for 32bit Dual Core I found out afterwards, and they are suppose to be working on one for 64bit Dual Core.

 Now DOOM3 runs "PERFECT" in both Gnome and KDE.

 All in all I can't complain one bit.
 I'll just have to wait for the updated patch I guess.:-k 

 All in all Thanks So Much for all your Help...

---

### Post by LateNighter on 2006-10-22
> **Lord Illidan said:**
> strange :(

but does it work well in Gnome at least

 As luck would have it.

 I went back and tried killall artsd again "STILL didn't work"#-o 

 So I started to Play Around with the different sound system types.
 Guess What Auto Detect didn't work, neither did OSS.](*,) 

 So I tried ALSA and it Worked.=D> 

 Lose my sound in KDE once I back out, But nothing that a Restart can't fix.

 I'll let you know how it runs in KDE. 
 But I expect it'll run just fine... Thanks again for everything...

 Well back as promised....

 Went back into KDE wouldn't work the same way TWICE....:twisted: 

 NNNNNNNNNOOOOOOOO....  Couldn't get sound again at all in KDE.

 But at least as I said before it PLAYS in Gnome so I really don't Care.

 This is exactly why I don't remove the Gnome Desktop after I get KDE installed, like I could.

 If something doesn't work in one, it usually does in the Other....:???: 

 My Floppy is another example...

 But that's another Story all together....:KS

---

