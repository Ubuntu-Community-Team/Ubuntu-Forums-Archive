---
title: "UT99 loki installer"
date: 2010-10-30
forum: Gaming &amp; Leisure
---

### Post by GhostC10 on 2010-10-30
I've been working for almost 3 days to find a working copy of the loki installer for UT99, to no avail. The only working link on Loki's site (the atomicgamer one) gives me a file that appears to be missing a considerable amount of data. I saw on another site that the script only runs reliably from root, so I tried that and got this result:

root@ghost-1201HA:/home/richard/Downloads# sh ut-install-436.run 
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 889744922 2341625838

Which appears to mean that the file is missing a whole bunch of data. This si supported by the liflg wite saying that the installer is supposed to be ~7.15mb, while any working link I find is only ~5.9mb.

I tried DLing it from [http://www.liflg.org/?catid=6&gameid=51](http://www.liflg.org/?catid=6&gameid=51) first, but the direct download is broken and the torrent has no seeds (I'd hardly expect any, how old is this game again?) There seem to be plenty of other people who've got it to work, I must be doing something wrong...

---

### Post by R33D3M33R on 2010-10-30
You should check again as both files have 5+ seeds.
The GOTY and normal installer differ, so be sure to pick the correct one.
For more info see: [https://help.ubuntu.com/community/Games/Native/UnrealTournament](https://help.ubuntu.com/community/Games/Native/UnrealTournament)

If something doesn't work and it's not written on the wiki, please post it here, so I can update the wiki.

---

### Post by GhostC10 on 2010-10-31
I've had that exact page up in the adjacent tab, and I see no seeds in Transmission. That's probably on account of the time. I'll leave my laptop plugged in for as long as it takes, I suppose. I'll keep this thread open until I get it installed or give up, one of the two.

---

### Post by GhostC10 on 2010-11-01
I am pleased to report that some kind soul seeded the torrent and I've got it mostly working now. It threw up a bunch of error messages about the old GTK not being able to install, but I tried running it anyway and it worked. Now the only problem is that even after I used cpufreq-set to 400mhz, the game is impossibly fast. Any advice? This POS poulsbo isn't exactly bleeding edge, so I'm surprised that *this* is the problem that is bringing me down.

---

### Post by R33D3M33R on 2010-11-01
Try to use this:

```
cpufreq-set -g performance
```

---

### Post by GhostC10 on 2010-11-02
That's what I tried first, when it didn't work I tried setting it to a fixed frequency (400mhz in this case) and that didn't work either. I didn't even expect it to run with the clock speed so low, but did it ever... Just tried it again, just to be sure I didn't mess it up. Still unplayably fast. Console output doesn't show anything out of the ordinary except the /dev/dsp (the sound, I think) is broken, probably on account of PulseAudio:

/dev/dsp: No such file or directory

But since I typically play games without sound (people in public places don't appreciate gunfire sounds for some reason...) I didn't think twice about it.

Any advice? I'm annoyed that I got this far, only to be brought down by this *snicker* screaming-fast poulsbo.

---

### Post by R33D3M33R on 2010-11-02
You could enable vsync, limit framerate (in the ~./loki/ut/System/UnrealTournament.ini and run with command-line -cpuspeed=XXX. XXX is the speed in MHz. As for audio, run it with "padsp ./ut".

---

### Post by GhostC10 on 2010-11-02
Does the -cpuspeed command go after the ut command (as in ut -cpuspeed=xxx)? Or is that something else? And yeah, I saw that bit on the wiki page, I just wasn't too bothered by it. Thought that someone else more experienced than I might know if that was causing any problems for me.

A bit more research has shown that my laptop's pouslbo chipset is capable of a minimum of 800mhz. Is that just too fast? And I can't figure out where that vsync option is... Could you post the line where it is? Also, is it worth noting that while the in-game graphics display perfectly, the character creator displays only a black box with no graphics?

This is the shell script I use to automate the launch except for having to enter my root pw, sorry for the fake bbcode tags:

[Code]

#!/bin/bash

sudo cpufreq-set -g performance

# Sets the CPU to minimum speed

cdemu load 0 /home/richard/UTCD1.iso

# Loads the disk image into emulated drive 0

sh /home/richard/ut/ut -cpuspeed=800

# Executes the binary

cdemu unload 0

# Unloads the disk image from enumlated drive 0, cleaning up the /media folder 

exit

[End Code]

---

### Post by GhostC10 on 2010-11-04
I have not found a workable solution on these forums or any other. Am I to assume that this problem cannot be solved? I lack the expertise to attempt anything more without guidance.

---

### Post by Butthead on 2010-11-04
Hmm, did you try going into the "Preferences" tab in the game and turning down the game speed to 50%? :confused:

---

### Post by GhostC10 on 2010-11-04
That made it almost playable... Still not quite there yet, but very close. Is there anything that I'm doing wrong with the script? I can't turn the cpu speed down any lower than 800, which (I think) the script handles...

---

### Post by Butthead on 2010-11-05
Well, I personally run GOTY Unreal Tournament under Wine on my dual-core x64 bit system (only way I could get it to install on this rig).  Wine must have some kind of built in processor throttling code in it somewhere, because when I start it sometimes, it runs like mad too, but exiting out of Wine and then restarting it, it runs at a very playable frame rate then.

That is, before I remembered the game speed slider in the game.

---

### Post by GhostC10 on 2010-11-06
The poulsbo chipset in my laptop's hardware is so badly supported wine just flat refuses to do it's thing with openGL, led to some terrifying stability issues and an eventual nuke-n-pave. So I'll be waiting until I can afford a laptop with decent driver support. Thank you for dealing with my whining. I guess I can try again to get it working in the winXP partition I've got, but I couldn't even get it to start up after quite some time of trying. I shall simply be nostalgic until I can save up the funds.

Just seems like a shame that you all and I went to all this effort for naught.

---

### Post by disabledaccount on 2010-11-12
I strongly recommend  using windows version with originall installer. The only setting that have to be changed is renderer engine = opengl. DirectX renderer works flawlessly under wine but is much slower.
Additional steps:
You must force usage of one cpu core only - otherwise you'll get Negative Delta Time errors. You can use schedtool.
The game calibrates its internal timers during startup - dynamic frequency switching will cause problems.
On my machine: HD5670, x2 toledo @forced 1.8GHz, one core used I have 150 - 250FPS with high to very high settings, latest wine.

---

### Post by satyanash on 2010-11-30
What did you exactly do to get it to atleast work? 
i tried the direct download link on liflg.org and when i run the script it gives me this error:

```

Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage.goty Installer....................................................................................
/home/sattu/.setup1978: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

```
I tried searching for a package with that name but did not find any.. Help ?
Satyajeet

---

### Post by Perfect Storm on 2010-11-30
libgtk1.2 is an old obsolete library, so you can't find it in newer release of ubuntu. 

Though you can find it in earlier release, search for it here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by R33D3M33R on 2010-11-30
Everything is covered in the Ubuntu wiki: [https://help.ubuntu.com/community/Games/Native/UnrealTournament](https://help.ubuntu.com/community/Games/Native/UnrealTournament)

---

### Post by rizzeh on 2010-11-30
Getting UT to run native isn't the biggest obstacle. Most servers run anticheat software that creates whole host of new problems when trying to connect with native linux ut client.To save the hassle i play ut on wine or dual boot to winxp. Old original Unreal runs well on new linux binaries though.  [www.oldunreal.com]("http://www.oldunreal.com/downloads.html")

---

### Post by R33D3M33R on 2010-12-01
If ACE is used, here are the binaries: [http://utgl.unrealadmin.org/ace/](http://utgl.unrealadmin.org/ace/)

---

### Post by Sylos on 2010-12-02
Sorry to tread on you thread but I have a quick question....
I have GOTY edition that I have installed. Do I gain anything by installing the official bonus pack that is shown on loki's site? Cant remember if GOTY has all the bonus stuff or just some of it.

Cheers

---

### Post by Butthead on 2010-12-02
I'd (personally) install any bonus pack that was available to me.  Never know when you might need a certain texture that's found in it, especially if you download a lot of external user created maps for the game. :-k

---

### Post by Sylos on 2010-12-03
I have tried to install it since I posted but the loki installer says I have to install Unreal Tournament first - which I have! Very odd.

I was wondering if this was the reason I cant get onto any internet games - all I get is 'master server failed' error and no servers show up. It could just be the master server down last night but I wondered if I was missing something.

Any Thoughts?

---

### Post by Sylos on 2010-12-03
EDIT:Previous spam removed so this comment redundant.

---

