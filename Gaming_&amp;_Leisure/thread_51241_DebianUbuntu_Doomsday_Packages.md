---
title: "Debian/Ubuntu Doomsday Packages"
date: 2005-07-23
forum: Gaming &amp; Leisure
---

### Post by Yagisan on 2005-07-23
** Please note this a a copy of a post I placed in the offcial doomsday forums **

G'day.

I'm please to announce the availablity of new Doomsday packages for Debian Sarge and for Ubuntu Hoary. More information on what has been packaged is available here [http://eyagi.bpa.nu/~jamie/doomsday.html](http://eyagi.bpa.nu/~jamie/doomsday.html). Please note that the repository HAS moved, and updated details are on that page.

What's new in this release: I have done some packaging cleanups, I've added .desktop files, and I've fixed an annoying typo that actually prevented the deng-jdoom-ep pack from actually working (I can't believe no one noticed it ?). At the time of writing the engine, support files, iwad installers and all the jpacks have finished autobuilding and are available for download. The pwads are currently queued and will autobuild over the next few days.

Currently only i386 packages are working. I built amd64 but due to some issues it segfaults on startup. powerpc and other Debian arch users, feel free to apt-get source deng and build it yourself, or show me how to get Debian/Ubuntu installed in an emulator for your arch, and I'll build them myself.

Those of you who have downloaded this before have probally realised I actually host this on my home ADSL line. So in advance, big packs are likely to be slow. I strongly recommend to start with you download the iwad installers, and deng first, and download the jpacks overnight.

amd64 users:
* I have tested this in an Ubuntu Hoary i386 chroot on an Ubuntu Hoary amd64 system with nvidia binary drivers and it works fine for me.
* I have tested this in an Debian Sarge i386 chroot on an Ubuntu Hoary amd64 system with nvidia binary drivers. It can not find openGL drivers and isn't really playable because of graphics corruption.
* If you run this on an amd64 system, in an i386 chroot, with nvidia drivers, and have graphics corruption caused by deng not finding you drivers, this can be fixed by copying 32bit versions of your nvidia drivers to your chroot and running ```
export LD_PRELOAD="/home/jamie/libGL.so.1.0.7174 /home/jamie/libGLcore.so.1.0.7174 /home/jamie/libnvidia-tls.so.1.0.7174"
```to load 32 nvidia drivers. Make sure you bind mount /dev in your chroot. It's a kludge.
*** If you run this in a chroot, you don't get a nice menu to load deng. To load deng you can look in usr/share/applications for any desktop file starting with deng, eg doom2 is deng-iwad-doom2-installer.desktop. If you open that file you will see a line starting Exec= copy and paste everything after the Exec= into a new terminal to load doomsday. Anyone care to supply a script to automatically do this ?

---

### Post by nickless on 2005-07-23
Whats that? :)

---

### Post by Yagisan on 2005-07-23
[QUOTE=nickless]Whats that? :)[/QUOTE]It's a very nice Doom sourceport. You may know it as JDoom, JHexen or JHeretic. The upstream website is [http://www.doomsdayhq.com/](http://www.doomsdayhq.com/) and the support forums are [http://forums.newdoom.com/forumdisplay.php?forumid=57](http://forums.newdoom.com/forumdisplay.php?forumid=57)

---

### Post by Mr_Smiley on 2005-07-23
I don't own DOOM but can I still play using the demo pak files? If I can where can I get the pak files from?

Thanks.

---

### Post by Yagisan on 2005-07-23
[QUOTE=Mr_Smiley]I don't own DOOM but can I still play using the demo pak files? If I can where can I get the pak files from?

Thanks.[/QUOTE] I will make an installer package for the shareware doom episode some time in the future, there is a doom-wad-shareware package in Debian's non-free section which will need to be ported to multiverse as my installer will depend on it.

You can still buy Doom at EB games if your near one, Id released a Doom Collectors pack, it's about $20AU from memory.

---

### Post by Mr_Smiley on 2005-07-23
[QUOTE=Yagisan]
You can still buy Doom at EB games if your near one, Id released a Doom Collectors pack, it's about $20AU from memory.[/QUOTE]

I'll see if I can find it at EB. 
Thanks! :)

---

### Post by Burgundavia on 2005-07-23
If the game can be redistributed, the packages can make their way into Ubuntu. You would need to talk to the Masters of the Universe in #ubuntu-motu on Freenode.

Corey

---

### Post by Yagisan on 2005-07-23
[QUOTE=Burgundavia]If the game can be redistributed, the packages can make their way into Ubuntu. You would need to talk to the Masters of the Universe in #ubuntu-motu on Freenode.

Corey[/QUOTE]
Thanks Corey, but with this package there are some DFSG issues to be fixed. When they are fixed I will apply to have it go into Debian proper with me as the DD. To be honest I haven't checked the MOTU criteria yet, but it's on my list of todo things.

People, give me your feedback on these packages. If you like it and want it to be in Ubuntu tell me, and I'll start the process.

---

### Post by manny on 2005-07-23
Thank you very much Yagisan! This is an amazing port of a true classic and much loved game. I was as impressed with this port as i was with doom3 graphics. I even installed Sarge to use your packages. They would be a great addition to Ubuntu. Anybody who played and enjoyed doom I & II shouldn't miss this one. Thx again
People interested in buying original doom can get it here: [http://www.idsoftware.com/games/doom/doom-collectors/index.php?game_section=buy](http://www.idsoftware.com/games/doom/doom-collectors/index.php?game_section=buy)
and it's worth every penny imo.

---

### Post by Yagisan on 2005-07-24
Cool. I currently have packages for Debian Sarge and Ubuntu Hoary built, there are instructions for Hoary, Breezy, Sarge and Etch on my website, so you can install the Ubuntu versions (honestly the only difference is multiverse/non-free and that hoarys sdl is older then sarge, which made sarge packages not install)

---

### Post by Mr_Smiley on 2005-07-24
I just got DOOM from EB and I'm trying to install the iwad file for ultimate doom, the installer wants doomu.wad but its actually doom.wad on my cd.

---

### Post by DemiUrge8 on 2005-07-24
[QUOTE=Mr_Smiley]I just got DOOM from EB and I'm trying to install the iwad file for ultimate doom, the installer wants doomu.wad but its actually doom.wad on my cd.[/QUOTE]
 Copy the doom.wad file to your home directory and rename it doomu.wad. Then point the installer toward ~/doomu.wad and you'll be in business.

Unless I'm wrong. In which case I'm going to look silly.

---

### Post by Mr_Smiley on 2005-07-24
Yeah I'm pretty sure thats going to work but I just wanted to point that out.

---

### Post by NeoChaosX on 2005-07-24
Is there a way to install the high-res packs for the Doomsday games in Linux, or will have to do that manually? I really want to play jHexen again.

---

### Post by Yagisan on 2005-07-24
[QUOTE=Mr_Smiley]Yeah I'm pretty sure thats going to work but I just wanted to point that out.[/QUOTE] It's done by design. If you name doom.wad to doomu.wad Deng will look for 4 episodes, not 3. (if your doom.wad only has 3 episodes, let me know, and I make a clasic doom installer and fix the menu entry for ultimate doom, most people seem to have Ultimate Doom now, even if the box says doom.)

If you need to report bugs, in an terminal prompt, just type ```
reportbug deng
``` and it will send me the information needed to help you.

[QUOTE=NeoChaosX]Is there a way to install the high-res packs for the Doomsday games in Linux, or will have to do that manually? I really want to play jHexen again.[/quote]Yes, the packs are included already set up. However for hexen and heretic, you will need to be a little patient as they are a bit further down the queue at the moment, but they are coming.

---

### Post by Mr_Smiley on 2005-07-24
Ah ok, thanks for clearing that up :)

---

### Post by Mr_Smiley on 2005-07-24
Well I just installed it and started playing Doom, it seems to be working great except there is no music. Is there any reason why its not playing?

Thanks. :)

---

### Post by Yagisan on 2005-07-24
[QUOTE=Mr_Smiley]Well I just installed it and started playing Doom, it seems to be working great except there is no music. Is there any reason why its not playing?

Thanks. :)[/QUOTE]Did you install timidity and freepats ? they are listed as recommends on the deng package.

---

### Post by Mr_Smiley on 2005-07-24
[QUOTE=Yagisan]Did you install timidity and freepats ? they are listed as recommends on the deng package.[/QUOTE]

No, I didn't. Thanks, now its all working great.

---

### Post by manny on 2005-07-24
Using etch now but apt can't see anything at deb [http://eyagi.bpa.nu/~jamie/debian](http://eyagi.bpa.nu/~jamie/debian) etch main contrib non-free, however if i use sarge it works. I'm gonna wait a little to see what's up. I know this may not be the place to ask this, but, if i go sid should i use etch repos?
Thanks

---

### Post by Yagisan on 2005-07-24
[QUOTE=manny]Using etch now but apt can't see anything at deb [http://eyagi.bpa.nu/~jamie/debian](http://eyagi.bpa.nu/~jamie/debian) etch main contrib non-free, however if i use sarge it works. I'm gonna wait a little to see what's up. I know this may not be the place to ask this, but, if i go sid should i use etch repos?
Thanks[/QUOTE] Etch, and Breezy are currently placeholders, as I haven't setup autobuilders for them yet, because they are currently unstable. Debian users, use the Sarge repo, Ubunty users, use the Hoary repo.

---

### Post by NeoChaosX on 2005-07-24
Added your repos to my sources.list, but when I do an apt-get update, this error message comes up:

```
W: GPG error: http://eyagi.bpa.nu hoary Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0027CEFA4B6E7209
```
Any way to fix this?

---

### Post by Yagisan on 2005-07-25
[QUOTE=NeoChaosX]Added your repos to my sources.list, but when I do an apt-get update, this error message comes up:

```
W: GPG error: http://eyagi.bpa.nu hoary Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0027CEFA4B6E7209
```
Any way to fix this?[/QUOTE]
In a terminal,
```
gpg --recv-keys 0x4B6E7209
gpg --export -a  0x4B6E7209 > Yasgisan.asc
sudo apt-key add Yagisan.asc
```

---

### Post by manny on 2005-07-25
Thank you Yagisan, working fine on etch :)

---

### Post by Mishura on 2005-07-25
This is nice.  My previous install of Doomsday worked, yet no matter what I did, I couldn't get the jPacks to work at all, even when installed in /Auto.  *This* works!

Looking forward to the Heretic/Hexen packs too.  Any extras you can find as well would be nice too.

---

### Post by Yagisan on 2005-07-26
[QUOTE=Mishura]This is nice.  My previous install of Doomsday worked, yet no matter what I did, I couldn't get the jPacks to work at all, even when installed in /Auto.  *This* works!

Looking forward to the Heretic/Hexen packs too.  Any extras you can find as well would be nice too.[/QUOTE]Thank You. It's nice to be appreciated.
You may have noticed that a selection of pwads and Megawads for doom/doom2 have appeared in the repo over the last few days, the heretec stuff will come after that followed by hexen (at least thats the plan).

It would be nice if we could organise some online games (I'm in GMT+10), as no one seems to be playing online.

---

### Post by Mishura on 2005-07-26
> It would be nice if we could organise some online games (I'm in GMT+10), as no one seems to be playing online.

Indeed, there is never any Doomsday servers up, and I've been itching for some Classic gaming.  However, I'm GMT-6 (Central US Time).. so that may complicate things a tad--but I have a wierd sleep schedule anyways so it may not matter anyways.  :wink:

---

### Post by Yagisan on 2005-07-26
Initial heretic and hexen packages have been prepared. Models and textures to be packaged as time allows. Enjoy.

---

### Post by Mishura on 2005-07-27
I'd like to point out that with jHeretic, every time I try to load a save game it crashes.  No matter what.  Happens 100% of the time.  Note that this doesn't happen with any of the Doom Games.  (Haven't tried it with Hexen yet.)

Error message resembles:  "Segmentation Fault:  SDL Parachute Deployed"

---

### Post by Yagisan on 2005-07-27
[QUOTE=Mishura]I'd like to point out that with jHeretic, every time I try to load a save game it crashes.  No matter what.  Happens 100% of the time.  Note that this doesn't happen with any of the Doom Games.  (Haven't tried it with Hexen yet.)

Error message resembles:  "Segmentation Fault:  SDL Parachute Deployed"[/QUOTE]Next time it crashes please run in that terminal ```
reportbug deng
```, type a description of the error as best as you can, and send it to me. I will see if I can fix it, and if not I will forward it upstream. It is important to run reportbug right after it crashes, because doomsday deletes it's logs on startup.

---

### Post by Mishura on 2005-07-27
Bug report sent.

---

### Post by dolny on 2005-09-30
Thank you very much!

---

### Post by jadugarr on 2005-10-11
Looks like this repo is down.  It's a shame because it made it real easy to install everything.

---

### Post by Yagisan on 2005-10-11
[QUOTE=jadugarr]Looks like this repo is down.  It's a shame because it made it real easy to install everything.[/QUOTE] The machine had an "accident" some time ago. The repository is still up, but I am moving the webpage in future. Repository details can be found here temporarily [http://users.tpg.com.au/yagisan/community/doomsday.html](http://users.tpg.com.au/yagisan/community/doomsday.html)

---

### Post by jadugarr on 2005-10-11
[QUOTE=Yagisan]The machine had an "accident" some time ago. The repository is still up, but I am moving the webpage in future. Repository details can be found here temporarily [http://users.tpg.com.au/yagisan/community/doomsday.html](http://users.tpg.com.au/yagisan/community/doomsday.html)[/QUOTE]

Thank you very much.  I forgot to backup my jDoom install when I upgraded my system and I was going to have to compile everything from source.  Your work is much appreciated.

---

### Post by Yagisan on 2005-10-11
[QUOTE=jadugarr]Thank you very much.  I forgot to backup my jDoom install when I upgraded my system and I was going to have to compile everything from source.  Your work is much appreciated.[/QUOTE]
Your quite welcome, breezy packages will be released soon, and a reorganisiation of the data packages are planned (inclusion of new jpacks, removal of superceeded jpacks).

---

### Post by StormBlast on 2005-10-13
[QUOTE=Yagisan]The repository is still up[/QUOTE]
It's still down for me. Site's not pinging, domain name's not resolving. Maybe the problem is your ddns provider?

---

### Post by jadugarr on 2005-10-13
[QUOTE=StormBlast]It's still down for me. Site's not pinging, domain name's not resolving. Maybe the problem is your ddns provider?[/QUOTE]

Same here.  I tried to download it yesterday, and it couldn't find the server.

---

### Post by Yagisan on 2005-10-13
Sorry guys - yesterday was a bad time to be checking - I replaced the NIC and upgraded the box to breezy. It is there - but the www page is at the temp location a bit further up. Ddns is ok - I tuned the settings a bit so it should get a faster update when my ip changes.```
(amd64)jamie@doomguy:~$ ping eyagi.bpa.nu -c 3
PING eyagi.bpa.nu (60.240.8.226) 56(84) bytes of data.
64 bytes from 60-240-8-226-nsw-pppoe.tpgi.com.au (60.240.8.226): icmp_seq=1 ttl=64 time=0.276 ms
64 bytes from 60-240-8-226-nsw-pppoe.tpgi.com.au (60.240.8.226): icmp_seq=2 ttl=64 time=0.311 ms
64 bytes from 60-240-8-226-nsw-pppoe.tpgi.com.au (60.240.8.226): icmp_seq=3 ttl=64 time=0.293 ms

--- eyagi.bpa.nu ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.276/0.293/0.311/0.020 ms

```

---

### Post by fakie_flip on 2005-10-14
Will any good games run on a machine with a p2 350mhz and 176mb of ram with a nVidia Vanta card and Ubuntu 5.04 Hoary?

---

### Post by jadugarr on 2005-10-14
jDoom when the repo is up it should run on that machine.  It is probably to slow to run using the 3D models and some of the effects though.

---

### Post by StormBlast on 2005-10-14
[QUOTE=Yagisan]Sorry guys - yesterday was a bad time to be checking - I replaced the NIC and upgraded the box to breezy. It is there - but the www page is at the temp location a bit further up. Ddns is ok - I tuned the settings a bit so it should get a faster update when my ip changes.[/QUOTE]
Ok, now it's resolving and pinging - just waiting for repos :)
And MEGAthanks to you for providing packages!
PS. Done with Ultimate Doom tonight :)

---

### Post by manny on 2005-10-17
Thank you very much Yagisan! Glad it's up again. I hope you don't mind me posting a link on the doom2.net forums here: [http://www.doom2.net/~forum/viewtopic.php?t=26](http://www.doom2.net/~forum/viewtopic.php?t=26)
(I will edit post soon) Well, thanks so much again for your great work and please keep up the debian repos, it runs great on etch - testing.

---

### Post by mortong on 2005-10-25
I noticed that the server is still down for getting this package.  Does anyone else have a working link for the download -- or does anyone have it that could email it to me?

Thanks.

---

### Post by Yagisan on 2005-10-25
[QUOTE=mortong]I noticed that the server is still down for getting this package.  Does anyone else have a working link for the download -- or does anyone have it that could email it to me?

Thanks.[/QUOTE]
I just checked - that server is still up. The original page link has been restored.

There will be a new version for breezy released within a few days - beta3. There will be no more updates for hoary from now on. Still no amd64 packages, and as I don't have a ppc, I can't build ppc to test it.

The webpage will update when breezy packages are available.

---

### Post by jadugarr on 2005-10-25
How are you testing if the server is still up?  I haven't been able to load the main webpage or the ping repo since it went down.

---

### Post by Yagisan on 2005-10-26
[QUOTE=jadugarr]How are you testing if the server is still up?  I haven't been able to load the main webpage or the ping repo since it went down.[/QUOTE]
heh - my isp has been a bit funny lately - they cycle me more often. the was a bug on the system where it wouldn't open the www site after a ip cylcle, but it would work on first powerup.

I believe it is fixed now. Please try again.

---

### Post by jadugarr on 2005-10-26
Nope still down for me.  Maybe your isp is blocking certain people, say those outside of australia because your using too much bandwidth.

---

### Post by Yagisan on 2005-10-26
[QUOTE=jadugarr]Nope still down for me.  Maybe your isp is blocking certain people, say those outside of australia because your using too much bandwidth.[/QUOTE]

I just had a few checks done from europe and the usa - they report that they can also access my site now, but not eairlier.

---

### Post by jadugarr on 2005-10-26
I just tried again and now it loads.  If other people were able to access it I was starting to worry that it was a problem with my ISP :).

---

### Post by StormBlast on 2005-10-26
Yeah! Finally, it works for me too!

---

### Post by Yagisan on 2005-10-26
[QUOTE=StormBlast]Yeah! Finally, it works for me too![/QUOTE]
Yay!!!

Remember, hoary only for now. Breezy later this week after I have done some testing.

---

### Post by Yagisan on 2005-11-02
Breezy Repo is now open. Hoary Repo is now closed.
Update your repository info from here [http://eyagi.bpa.nu/~jamie/doomsday.html](http://eyagi.bpa.nu/~jamie/doomsday.html)

---

### Post by jadugarr on 2005-11-02
Thanks Yagisan.  I'll try it out in a couple of days, or as soon as I can tear myself away from Civ4.  
Totally unlrelated, but I hope winex/cedega supports Civ4 soon because constantly booting between Linux and windows is getting annoying ... but trying to use windows to do anything but play games is even more annoying :-).

---

### Post by penno on 2007-04-25
Hmm, might be a bit of a blast from the past judging my the age of this thread. Anyways, anyone got Doomsday working on Feisty? Are there repositories around? (Seems that eyagi.bpa.nu is no longer with us.)

THanks! :KS

---

### Post by Yagisan on 2007-04-26
> **penno said:**
> Hmm, might be a bit of a blast from the past judging my the age of this thread. Anyways, anyone got Doomsday working on Feisty? Are there repositories around? (Seems that eyagi.bpa.nu is no longer with us.)

THanks! :KS

I need to do some work to get them ready for Feisty, the game has had some changes - but first, the router and server that I was hosting on need to be replaced, as they are currently two rather heavy bricks :(

---

### Post by penno on 2007-04-26
Ah. Okey dokey. No hurry, but if / when they're ready you got one downloader here who's looking forward to it! :KS

---

### Post by AZzKikR on 2007-05-17
Yeah, I am looking forward to it as well for Feisty :D

---

### Post by hikaricore on 2007-05-17
I snagged all the packages last time the server was up.  ^_^

I've still got them installed from months ago when I set them up on Edgy, working fine still in Feisty though.

I honestly wish I could provide some type of mirror but I don't have the means to do so.

---

### Post by stinger30au on 2007-07-22
i have installed Doomsday from the repo and even got it to build the data it needs form my original doom 2 wad files and got this


**** GL BSP Node Builder 2.20 (C) 2005 Andrew Apted ****

* No output file specified. Using: /usr/share/games/doom/iwad/doom2/doom2.gwa

Opened IWAD file : /usr/share/games/doom/iwad/doom2/doom2.wad
                
Building GL nodes on MAP01
Building GL nodes on MAP02
Building GL nodes on MAP03
Building GL nodes on MAP04
Building GL nodes on MAP05
Building GL nodes on MAP06
Building GL nodes on MAP07
Building GL nodes on MAP08
Building GL nodes on MAP09
Building GL nodes on MAP10
Building GL nodes on MAP11
Building GL nodes on MAP12
Building GL nodes on MAP13
Building GL nodes on MAP14
Building GL nodes on MAP15
Building GL nodes on MAP16
Building GL nodes on MAP17
Building GL nodes on MAP18
Building GL nodes on MAP19
Building GL nodes on MAP20
Building GL nodes on MAP21
Building GL nodes on MAP22
Building GL nodes on MAP23
Building GL nodes on MAP24
Building GL nodes on MAP25
Building GL nodes on MAP26
Building GL nodes on MAP27
Building GL nodes on MAP28
Building GL nodes on MAP29
Building GL nodes on MAP30
Building GL nodes on MAP31
Building GL nodes on MAP32
                
Saving WAD as /usr/share/games/doom/iwad/doom2/doom2.gwa
                
Total serious warnings: 0
Total minor warnings: 40

All levels were built successfully.


when i ran it from cli i got this
 /usr/games/doomsday -anifilter -texcomp -game jdoom -iwad  /usr/share/games/doom/iwad/doom2/doom2.gwa
LoadPlugin: libdpdehread.so
LoadPlugin: libdpmapload.so
Z_Create: New 32.0 MB memory volume.
Con_Init: Initializing the console.
SW_Init: Startup message window opened.
Executable: Version 1.9.svn-trunk-devel +R Oct 31 2006 (DGL).
G_PreInit: Registering Bind Classes...
Parsing configuration files.
W_Init: Init WADfiles.
W_AddFile: data/doomsday.pk3
W_AddFile: data/jdoom/jdoom.pk3
W_AddFile: data/jdoom/auto/.basedata/fonta033.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta034.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta035.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta036.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta037.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta038.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta039.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta040.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta041.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta042.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta043.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta044.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta045.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta046.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta047.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta048.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta049.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta050.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta051.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta052.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta053.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta054.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta055.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta056.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta057.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta058.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta059.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta060.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta061.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta062.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta063.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta064.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta065.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta066.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta067.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta068.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta069.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta070.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta071.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta072.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta073.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta074.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta075.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta076.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta077.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta078.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta079.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta080.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta081.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta082.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta083.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta084.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta085.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta086.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta087.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta088.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta089.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta090.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta091.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta092.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta093.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta094.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta095.lmp
W_AddFile: data/jdoom/auto/.basedata/fonta121.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb033.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb034.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb035.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb036.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb037.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb038.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb039.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb040.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb041.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb042.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb043.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb044.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb045.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb046.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb047.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb048.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb049.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb050.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb051.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb052.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb053.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb054.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb055.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb056.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb057.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb058.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb059.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb060.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb061.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb062.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb063.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb064.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb065.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb066.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb067.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb068.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb069.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb070.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb071.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb072.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb073.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb074.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb075.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb076.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb077.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb078.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb079.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb080.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb081.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb082.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb083.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb084.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb085.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb086.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb087.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb088.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb089.lmp
W_AddFile: data/jdoom/auto/.basedata/fontb090.lmp
W_AddFile: data/jdoom/auto/.basedata/m_therm2.lmp
W_AddFile: data/jdoom/auto/.basedata/menufog.lmp
W_AddFile: data/jdoom/auto/.basedata/pal18to8.lmp
W_AddFile: data/jdoom/auto/.basedata/sndcurve.lmp
--- No IWAD has been specified! Important data might be missing. Are you sure you want to continue?
**ERROR** W_AddFile: data/jdoom/auto/.basedata/m_therm2.lmp
W_AddFile: data/jdoom/auto/.basedata/menufog.lmp
W_AddFile: data/jdoom/auto/.basedata/pal18to8.lmp
W_AddFile: data/jdoom/auto/.basedata/sndcurve.lmp

W_CheckIWAD: Init aborted.

Z_Shutdown: Used 1 volumes, total 33554432 bytes.

what have i done wrong???
i have tried these was under XP Pro using doomsday and they work fine

this thread also has some very handy info on doomsday
[http://ubuntuforums.org/showthread.php?t=500706&highlight=doomsday](http://ubuntuforums.org/showthread.php?t=500706&highlight=doomsday)

---

### Post by CowzRule on 2007-08-04
> **penno said:**
> Hmm, might be a bit of a blast from the past judging my the age of this thread. Anyways, anyone got Doomsday working on Feisty? Are there repositories around? (Seems that eyagi.bpa.nu is no longer with us.)

THanks! :KS

> **Yagisan said:**
> I need to do some work to get them ready for Feisty, the game has had some changes - but first, the router and server that I was hosting on need to be replaced, as they are currently two rather heavy bricks :(

Any updates as to when/if the repos will be back up?

---

### Post by CowzRule on 2007-08-09
bump

---

### Post by GFree678 on 2007-08-12
For anyone wondering what happened to the repositories:

[http://forums.newdoom.com/showthread.php?t=33586](http://forums.newdoom.com/showthread.php?t=33586)

If you want to play Doomsday, get the source code from [http://sourceforge.net/project/showfiles.php?group_id=74815](http://sourceforge.net/project/showfiles.php?group_id=74815) and build it yourself from now on.

---

### Post by CowzRule on 2007-08-13
> **GFree678 said:**
> For anyone wondering what happened to the repositories:

[http://forums.newdoom.com/showthread.php?t=33586](http://forums.newdoom.com/showthread.php?t=33586)

If you want to play Doomsday, get the source code from [http://sourceforge.net/project/showfiles.php?group_id=74815](http://sourceforge.net/project/showfiles.php?group_id=74815) and build it yourself from now on.

Thanks for the update.

---

### Post by emwine on 2007-11-01
> If you want to play Doomsday, get the source code from [http://sourceforge.net/project/showfiles.php?group_id=74815](http://sourceforge.net/project/showfiles.php?group_id=74815) and build it yourself from now on.

I did that, got it to compile and it segfaulted after:
```
R_Init: Init the refresh daemon.
```
Hard to say the problem-- everything seemed routine until it wouldn't run.  Running Gutsy AMD64 using 1.9.0-beta5.2 sources.

---

### Post by SatanClaus on 2007-11-15
> **emwine said:**
> I did that, got it to compile and it segfaulted after:
```
R_Init: Init the refresh daemon.
```
Hard to say the problem-- everything seemed routine until it wouldn't run.  Running Gutsy AMD64 using 1.9.0-beta5.2 sources.

I have same result on Feisty amd64

---

### Post by FG123 on 2007-11-15
Umm... ehh...

It won't run, because you're trying to compile the engine on 64-bit distros. Put simply; the code is not designed to work on anything but 32-bit. At least... the source code available for download in those nice little sourceforge directories.

Now, if you're very knowledgeable about such things, you can find the subversion repository for DD and pull down the latest internal build of the engine. I've done so and confirmed - this is the ONLY way you can compile and run doomsday for 64-bit Linux distros. They finally managed to make it work in 64-bit, but only if you use the internal version and not the publically available stuff.

So, if you're up for a little workout: [http://sourceforge.net/svn/?group_id=74815](http://sourceforge.net/svn/?group_id=74815)

---

### Post by yizuman on 2008-02-19
So no deb installers for doomsday, doom legacy, jdoom? None? Man, I love deb installers and it makes things so much easier. :(

---

