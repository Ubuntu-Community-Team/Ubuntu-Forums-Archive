---
title: "Mech/FPS fans, look here"
date: 2008-03-13
forum: Gaming &amp; Leisure
---

### Post by ShodanjoDM on 2008-03-13
I don't see this one mentioned quite often:

[URL="http://www.garagegames.com/products/29/"]
Dark Horizon: Lore Invasion[/URL]

---

### Post by compiledkernel on 2008-03-13
Released to the community by Garage Games. 

See the /opt/game/opinion link in my sig to hear all about garage games.

---

### Post by Perfect Storm on 2008-03-14
Good read CK. It would be a good idea to forward it to GG :popcorn:

---

### Post by GSZX1337 on 2008-03-14
Is this game like Mechwarrior? I'm still going to DL it, but I'd like to know if it'slike MW. (it's going to be awhile before I can play it, I'm messing around with my lappy)

---

### Post by compiledkernel on 2008-03-14
I guess you could call it similar to mechwarrior, yes.

---

### Post by ShodanjoDM on 2008-03-14
> **compiledkernel said:**
> Released to the community by Garage Games. 

See the /opt/game/opinion link in my sig to hear all about garage games.

Hmm, never thought about it before... :confused:
Seemed a good game at first, but then, oh well...

> Honestly Id rather have ID software's known good native support over anything else.

+1 Can't buy the ETQW from here though, so I'll stick with Wolfenstein ET instead :lolflag:

Anyway, thx for a good read :)

---

### Post by Vadi on 2008-03-14
I like DHLore, but practically nobody plays online now.

---

### Post by Blue Heron on 2008-04-27
> **ShodanjoDM said:**
> I don't see this one mentioned quite often:

[URL="http://www.garagegames.com/products/29/"]
Dark Horizon: Lore Invasion[/URL]

This looks good, I will try it. :)

---

### Post by Aeph on 2008-04-28
I tried installing this game using the guide [here]("http://gaming.gwos.org/doku.php/guides:32bit:dark_horizons_lore_invasion").
I got as far as the fourth line of the installation section, where I got the following error:

```

aeph@ubuntu:~$ linux32 sh ~/Desktop/dhli_v2_0_2.sh.bin
Verifying archive integrity...tail: cannot open `+266' for reading: No such file or directory
Error in checksums: 2877436053 is different from 609708321

```
Any thoughts?

---

### Post by Vadi on 2008-04-28
Re-download, could be a corrupted archive.

---

### Post by nutpants on 2008-04-28
i hate "free" downloads that are demos..

but i like mech style games.

and i loved tribes they made ten years agao
and i like legends that is FREE now from them (tribes clone)

thanks for the pointer.

nutz

---

### Post by Aeph on 2008-04-28
> **Vadi said:**
> Re-download, could be a corrupted archive.

No, that didn't help. Anyone install it differently?

---

### Post by SlackerTD on 2008-04-29
> **Aeph said:**
> No, that didn't help. Anyone install it differently?
The old Loki installer has problems on some distros. If you still want to use this installer, type in this before running the installer:

export _POSIX2_VERSION=199209

If there are still issues with that, head on over to the lore site where MGT has a new Bitrock installer for Lore:

[http://www.darkhorizons-lore.com/download.php?view.78](http://www.darkhorizons-lore.com/download.php?view.78)

The old Loki installer can also be found there:

[http://www.darkhorizons-lore.com/download.php?view.75](http://www.darkhorizons-lore.com/download.php?view.75)

Hope that helps Aeph. :)

> **nutpants said:**
> i hate "free" downloads that are demos..
Actually, it may say demo on the GG site, but it is the full version. I didn't like it saying that either, it looks confusing.

> **compiledkernel said:**
> Released to the community by Garage Games. 
GG did NOT make Lore. While I agree with much of what you posted about GG & linux support (yes, they do suck), I need to correct you on that point. Max Gaming Technologies are the people who made Lore. GG is just one of the places that used to sell Lore (yes, Lore is made with the Torque Game Engine). BTW, Lore costs nothing in CNR anymore either... we've got that fixed up with them as well.

The community is small unfortunately :(

However, there is an active group within that community though working on a patch that will provide some new weapons & new maps that will be out soon.

---

### Post by nutpants on 2008-04-30
#10 ./DHLore.bin [0x828867e]
#11 ./DHLore.bin [0x833cc95]
#12 ./DHLore.bin [0x8342afd]
#13 ./DHLore.bin [0x818b35d]
#14 ./DHLore.bin [0x808fc69]
#15 ./DHLore.bin [0x808f872]
#16 ./DHLore.bin [0x808f872]
#17 ./DHLore.bin [0x808f872]
#18 ./DHLore.bin [0x808f872]
#19 ./DHLore.bin [0x808f872]
DHLore.bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

any ideas?

nutz

---

### Post by warbread on 2008-04-30
Holy cats, that game looks good!  It should be fun for a quick skirmish now and again.  I love the blue cockpits, too.

---

### Post by ELD on 2008-04-30
Thanks downloading now, also added to gaming4linux.com

---

### Post by SlackerTD on 2008-04-30
> **nutpants said:**
> #10 ./DHLore.bin [0x828867e]
#11 ./DHLore.bin [0x833cc95]
#12 ./DHLore.bin [0x8342afd]
#13 ./DHLore.bin [0x818b35d]
#14 ./DHLore.bin [0x808fc69]
#15 ./DHLore.bin [0x808f872]
#16 ./DHLore.bin [0x808f872]
#17 ./DHLore.bin [0x808f872]
#18 ./DHLore.bin [0x808f872]
#19 ./DHLore.bin [0x808f872]
DHLore.bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

any ideas?

nutz
Yes, I will have a fix posted for that in a couple days. I've seen the issue myself after installing Arch, Slackware 12 & Fedora 8 the other day. It's nice that I have an older system I can play around with for issues like this now. :)

Apparently, the SDL library included with the game doesn't like those distros. The SDL lib from my Kubuntu 7.10 (& a couple others SDL in Kubuntu seems to be linked to) did the trick.

I'll reply back here once the tarball is up.

*edit* I'll also be installing Kubuntu 8.04 now that I have it downloaded & test out that fix as well.

---

### Post by SlackerTD on 2008-04-30
Of possible interest for those who have IRC clients, the main lobby for the game when you join is an IRC channel. You can point your client to irc.maxgaming.net & the channel of #darkhorizons. My nick there is Keith-MGT.

---

### Post by Vadi on 2008-04-30
Hm, I wonder if it can be included in Ubuntu's repositories. Anyone got the EULA for that game handy?

---

### Post by Ripfox on 2008-05-01
> **Vadi said:**
> Hm, I wonder if it can be included in Ubuntu's repositories. Anyone got the EULA for that game handy?

There ya go

---

### Post by Ripfox on 2008-05-01
Hey, does anyone know where the config file is to change screen rez...I keep hitting "video mode not supported" when running DHLore.bin

---

### Post by vghp on 2008-05-01
Here is deserted&#65311;
Popularity poor

---

### Post by Ripfox on 2008-05-01
bump

---

### Post by Vadi on 2008-05-01
I think it can be, since the demo is now the full game and you're allowed to redistribute that. I'll file a report about that on launchpad.

---

### Post by SlackerTD on 2008-05-01
> **Vadi said:**
> I think it can be, since the demo is now the full game and you're allowed to redistribute that. I'll file a report about that on launchpad.Hold off on that... something is in the works. ;-)

ripfox: All the settings are stored in ~/.maxgaming/lore. Take a look at the file in there under fps/client/prefs.cs. The same file is located in a couple other directories as well, but give that one a try first. If this doesn't help, let me know & I will experiment with it on my own system to give you a definitive solution.

nutz: I'll have a patch posted tonight for that error. I have confirmed it doing the same for me in Kubuntu 8.04 & the patch I have worked for it as well (woot! 4 for 4 distros, looks to be good for anyone with that error).

---

### Post by Vadi on 2008-05-01
> **SlackerTD said:**
> Hold off on that... something is in the works. ;-)


What exactly, if it's not a secret?

(and do you happen to be the same Slacker as from Savage 2? Awful lot of linux-gaming-related slackers about)

---

### Post by Ripfox on 2008-05-01
prefs.cs.dso is all I can find, and I don't seem to be able to edit that file with a text editor...what is a .dso anyways (some kind of config file I assume)

---

### Post by SlackerTD on 2008-05-01
> **nutpants said:**
> DHLore.bin: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

any ideas?

nutz
Head on over to here nutz:

[http://www.darkhorizons-lore.com/download.php?view.79](http://www.darkhorizons-lore.com/download.php?view.79)

> **Vadi said:**
> What exactly, if it's not a secret?

(and do you happen to be the same Slacker as from Savage 2? Awful lot of linux-gaming-related slackers about)
There will be something officially said within a day or so. :)

I'm not Slacker from Savage 2... that's the first game that my system can't handle... I have to buy another 1 GB of memory to make it happy... 512 just don't cut it. I'm Slacker in Orbz, Lore & occasionally Galcon.

> **ripfox said:**
> prefs.cs.dso is all I can find, and I don't seem to be able to edit that file with a text editor...what is a .dso anyways (some kind of config file I assume)
The .dso files are the .cs files compiled. Not really meant to be readable. I find it strange that the .dso file would be in the ~/.maxgaming/lore folder, but not the .cs file itself. When I wiped my settings, it opened up the game full screen in 800x600. I need to do more digging tomorrow as to how to change the default with no file like that (gotta talk to some of the lore coders who know more about this than myself). The console.log file in the main lore dir might give you more info about the mode it is trying to set... not sure.

---

### Post by SlackerTD on 2008-05-05
> **ripfox said:**
> Hey, does anyone know where the config file is to change screen rez...I keep hitting "video mode not supported" when running DHLore.bin
Sorry for the delay ripfox... toss this file into the DHLore/fps/client folder (renaming it to defaults.cs). You may need to get rid of the defaults.cs.dso file... not sure. Of interest in this file are the lines that say:

$pref::Video::windowedRes = "800 600";
$pref::Video::fullScreen = "1";

The default the game will start off with is that in full screen mode. Change it to a mode that is compatible with your system. Once the game starts, you can then change it to other resolutions as it should bring up those that your system is capable of running.

Hope this helps.

[ATTACH]68937[/ATTACH]

---

### Post by Ripfox on 2008-05-06
Thanks I will give it a try when I get home. :)

---

### Post by Sifilis on 2008-12-09
Anyone knows what to do if we encounter this > "The program returned an error code (127)", after the setup said the installation was a success and asks if we want to start playing?

edit:found a way to solve that after a bit googling.. now that default.cs isn't working right, stil get "no signal" on my screen..

---

### Post by RaiCoss on 2008-12-12
sweet, thanks!

---

