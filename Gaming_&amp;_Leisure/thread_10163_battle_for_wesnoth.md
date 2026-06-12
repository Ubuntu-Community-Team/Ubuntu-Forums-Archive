---
title: "battle for wesnoth"
date: 2005-01-05
forum: Gaming &amp; Leisure
---

### Post by jdodson on 2005-01-05
i installed the battle for wesnoth from universe last night and spent an hour or so playing it.  it was very well done, graphics, music, play was a bit jumpy but not too bad.  i was wondering if anyone else had played it and what they thought.

i think it is a very well done GPL game.

[http://www.wesnoth.org](http://www.wesnoth.org)

---

### Post by jdodson on 2005-01-05
if you havent played it i would recommend checking it out.  its a bit steep to learn, however it is pretty fun to play.

---

### Post by Perfect Storm on 2005-01-06
Played it for awhile and I'm sure it will turn out to be hitter!!!
Great game!

---

### Post by dkitty on 2005-01-06
I agree. It's a fabulous game. I've started messing around with the editor too.

---

### Post by fng on 2005-01-06
When you install the wesnoth server, its automaticly symlinked in /etc/init.d.  I'ts silly to run that server everytime i boot!  That shoudn't be default imo.

---

### Post by dkitty on 2005-01-06
To be honest, I hadn't noticed that fng. Though if that is indeed the case then I imagine it's because the game is built around the network code as opposed to the networking being more of an addition or plug-in. It doesn't bother me. Everything seems to run just fine for me with the exception of sound.

Does anyone else have sound problems? I haven't looked into it much. Perhaps Wesnoth uses a sound library that I don't have installed yet. *shrug* Not that I simply *must* have sound. I've nearly finished the primary campaign and haven't missed it much.

I'm running 0.8.8 as of this afternoon. It's a huge leap in functionality, gameplay types, terrain types, and some of the graphics are improved too. I highly recommend  compiling the latest release. It might be on universe in the hoary repository too.

---

### Post by fng on 2005-01-07
When you kill wesnothd, the game still runs fine.

---

### Post by jdodson on 2005-01-07
[QUOTE=dkitty]To be honest, I hadn't noticed that fng. Though if that is indeed the case then I imagine it's because the game is built around the network code as opposed to the networking being more of an addition or plug-in. It doesn't bother me. Everything seems to run just fine for me with the exception of sound.

Does anyone else have sound problems? I haven't looked into it much. Perhaps Wesnoth uses a sound library that I don't have installed yet. *shrug* Not that I simply *must* have sound. I've nearly finished the primary campaign and haven't missed it much.

I'm running 0.8.8 as of this afternoon. It's a huge leap in functionality, gameplay types, terrain types, and some of the graphics are improved too. I highly recommend  compiling the latest release. It might be on universe in the hoary repository too.[/QUOTE]

i got .8.8 by upgrading off the wesnoth apt-get server, the functionality is much better!  the game is way cool, though difficult, which is not a bad thing.

as for the sound problem, i have not had it.  sometimes for me killing esd brings it back, sometimes it doesnt.

i have a firestarter up so if any services open, they are not available to the public, however i did not notice that wesnothd was open by default :mrgreen:

i posted on the wesnoth forums and was responded by the lead developer(inventor) of wesnoth david whittle, if you are interested:

[http://www.wesnoth.org/forum/viewtopic.php?t=4206](http://www.wesnoth.org/forum/viewtopic.php?t=4206)

---

### Post by Uuranor on 2005-01-08
If I have the xcompmgr running, Wesnoth has some problem @_@

---

### Post by Perfect Storm on 2005-01-08
Funny, I've no problem with Wesnoth whatsoever.  Could it be that the problem lies somewhere else than the game itself?

---

### Post by Tapeworm on 2005-01-12
I found it to be very well done but also very difficult. 

The campaign scenarios don't have enough turns to build up numerically superior forces

The whole "time of day combat skill modifier" eludes me. I understand what the effect is but how do you base a strategy around it? I primarily use elves just to eliminate *some* of the detrimental effects of nighttime...

Ideas?

Tapeworm

---

### Post by jdodson on 2005-01-14
[QUOTE=Tapeworm]I found it to be very well done but also very difficult. 

The campaign scenarios don't have enough turns to build up numerically superior forces

The whole "time of day combat skill modifier" eludes me. I understand what the effect is but how do you base a strategy around it? I primarily use elves just to eliminate *some* of the detrimental effects of nighttime...

Ideas?

Tapeworm[/QUOTE]


well you could always "bunker in" to a town for the night and replentish your health.  

i also had a problem with not having enough time to finish the missions.  i talked to the lead developer and he said they would look at making it easier.  he also mentioned that in a article someone wrote up about wesnoth.

---

### Post by Stefan Koopmanschap on 2005-01-15
it seems their site is currently down though, or is that just my connection?

---

### Post by Dylanby on 2005-01-15
Site's up for me.

---

### Post by Stefan Koopmanschap on 2005-01-15
darn, must be my connection then

---

### Post by mendicant on 2005-01-19
You can 'edit' the difficulty by changing the config files it uses; for instance, look at:
/usr/share/games/wesnoth/data/scenarios/Eastern_Invasion/Approaching_Weldyn.cfg (this is from my Debian box, presumably the same on Ubuntu).  You can edit the # of turns, and even the starting gold.
You can edit units by editing their files, etc.  Of course, you should probably back up the files you change.

---

### Post by hazza96 on 2005-01-26
[QUOTE=jdodson]i got .8.8 by upgrading off the wesnoth apt-get server[/QUOTE]
How did you do that? I get a heap of conflict errors if I try.

---

### Post by Buffalo Soldier on 2005-01-26
[QUOTE=dkitty]Does anyone else have sound problems? I haven't looked into it much. Perhaps Wesnoth uses a sound library that I don't have installed yet. *shrug* Not that I simply *must* have sound. I've nearly finished the primary campaign and haven't missed it much.[/QUOTE]

Have you?

```
sudo apt-get wesnoth-music
```

---

### Post by jdodson on 2005-01-26
[QUOTE=hazza96]How did you do that? I get a heap of conflict errors if I try.[/QUOTE]

hmmm well all i really did was put the servers in my apt-get list and ran an update.  worked like a charm.

---

### Post by TravisNewman on 2005-01-27
Aw hell, why'd you mention this? I can tell I'm going to get addicted if I don't forget I ever played it.

Damn nice though, I've never played a GPL game that good.

---

### Post by Buffalo Soldier on 2005-01-27
[QUOTE=panickedthumb]Damn nice though, I've never played a GPL game that good.[/QUOTE]

Wondering is there any real time strategy (RTS) game under GPL out there.

---

### Post by fng on 2005-01-27
Globulation2
freecraft
...

---

### Post by Perfect Storm on 2005-01-27
[QUOTE=panickedthumb]Aw hell, why'd you mention this? I can tell I'm going to get addicted if I don't forget I ever played it.

Damn nice though, I've never played a GPL game that good.[/QUOTE]


Then you should try Vega Strike though it's a completly diffrent genre. If you are into Space simulator games like Elite, frontier, wing commander, privateer etc. etc.

---

### Post by TravisNewman on 2005-01-28
Trying it, but if I lose my job you have to support me for a while. ;)

---

### Post by hazza96 on 2005-01-30
[QUOTE=jdodson]hmmm well all i really did was put the servers in my apt-get list and ran an update.  worked like a charm.[/QUOTE]
Which source did you use?

---

### Post by alainhenry on 2005-01-31
After a few scenarios, Westnoth seems a very good game.  Well balanced scenarios (intermediate level).  I was afraid it would be a bit simplistic to begin with (I did a lot of tabletop wargaming before), but I am now favourably impressed.  

I would like to install the latest version 0.8.9, which is the one used on the westnoth game server.  Is there a debian package for it ?  

Ubuntu repositories have 0.7.x., and I upgraded to 0.8.8 from a debian repository.  I also had to upgrade libsdl1.2debian, but it did not cause any problem.  

Alain

---

### Post by jdodson on 2005-01-31
[QUOTE=hazza96]Which source did you use?[/QUOTE]

the source off the wesnoth site for debian packages.

i pretty much just added the sources to my apt list and ran an upgrade.  worked like a charm.

---

### Post by fng on 2005-01-31
[QUOTE=Buffalo Soldier]Wondering is there any real time strategy (RTS) game under GPL out there.[/QUOTE]

craft - Warcraft 2-like multi-player real-time strategy game

---

### Post by alainhenry on 2005-02-03
I have BfWesnoth 0.8.8 installed, and working fine.  I tried to install 0.8.9 from debian.wesnoth.org, but it requires 
- libsdlmixer1.2 
while I have
- libsdlmixer1.2.5ubuntu1 
on my system.  
I assume this means 0.8.9 is not compatible with the latest update of libsdlmixer1.2.  This library is not used by  any other package, so maybe the best would be to de-install 1.2.5 and put back the older version (1.2).  Where could I find it?  Is this the right course.  DId anyone step over the same question ?

Thanks

Alain

---

### Post by jdodson on 2005-02-03
[QUOTE=alainhenry]I have BfWesnoth 0.8.8 installed, and working fine.  I tried to install 0.8.9 from debian.wesnoth.org, but it requires 
- libsdlmixer1.2 
while I have
- libsdlmixer1.2.5ubuntu1 
on my system.  
I assume this means 0.8.9 is not compatible with the latest update of libsdlmixer1.2.  This library is not used by  any other package, so maybe the best would be to de-install 1.2.5 and put back the older version (1.2).  Where could I find it?  Is this the right course.  DId anyone step over the same question ?

Thanks

Alain[/QUOTE]

yeah i had the same problems.  i would "assume" it will work with the next version of ubuntu.  its a bummer too, i wanted the new version of wesnoth.  though, i think that hoary will seed with the latest wesnoth anyway.

---

### Post by alainhenry on 2005-02-04
The problem is that the official gameserver works on the latest version only.  Are there other servers that host 0.8.8 (or older verisons) games ?

Alain

---

### Post by alainhenry on 2005-02-05
I managed to have 0.8.9 running.  I added debian unstable to my repositories in synaptic, and it upgrade libsdlmixer to 1.2.6, which allowed to update to 0.8.9, also present in unstable.  

This is what I inputed to include the repository:

url: [ftp://ftp.debian.org/debian/](ftp://ftp.debian.org/debian/)
distribution: unstable
section(s): main contrib non-free

Alain

---

### Post by faruk on 2005-02-12
Thanks, I installed the game and it worked fine but just after that there is no sound except the game! The game has sounds but I can't hear any more sound (from the app.s or xmms). 

Btw xmms gives this message: "please check that your soundcard is configured properly, you have the correct output plugin selected, no other program is blocking the soundcard"

Before installing the game everything was okay with the sound  :?  (I guess the problem is about the libsdl-mixer)
What should I do to have both the game sound and other sounds?


EDIT: Problem solved. 

Faruk

---

### Post by Perfect Storm on 2005-02-12
Version 0.8.10 is released.

---

### Post by alainhenry on 2005-02-12
[QUOTE=faruk]Thanks, I installed the game and it worked fine but just after that there is no sound except the game! The game has sounds but I can't hear any more sound (from the app.s or xmms). 

Btw xmms gives this message: "please check that your soundcard is configured properly, you have the correct output plugin selected, no other program is blocking the soundcard"

Before installing the game everything was okay with the sound  :?  (I guess the problem is about the libsdl-mixer)
What should I do to have both the game sound and other sounds?[/QUOTE]
There are threads in this forum that discuss the issues of how Ubuntu manages several sounds from different sources.  I don't have the link handy, unfortunately.  
Alain

---

### Post by faruk on 2005-02-12
[QUOTE=alainhenry]There are threads in this forum that discuss the issues of how Ubuntu manages several sounds from different sources.  I don't have the link handy, unfortunately.  
Alain[/QUOTE]

It's solved (problem is related with linux686 kernel)  8-[  Thanks anyway. 

Faruk

---

### Post by alainhenry on 2005-02-24
[QUOTE=Artificial Intelligence]Version 0.8.10 is released.[/QUOTE]
And 0.8.11 since a few days ago

Alain

---

### Post by isak on 2005-04-23
I solved the sound issue by installing libsdl1.2debian-esd instead of -oss. Probably, esd locks all sound resources and sdl must be told to send the sound through esound (which is used by gnome to play different sound events).

Note: This was on ubuntu hoary, but it may be the same for warty...

---

### Post by alainhenry on 2005-04-24
Because of another application, I installed libsdl1.2debian-all instead of libsdl1.2debian-oss.  I had no no problem with sound on Hoary when I tried 0.9.0 and Hoary

Alain

---

### Post by ginderhulk on 2008-06-25
where can i download it from

---

### Post by eragon100 on 2008-06-25
go to "applications -> Add/remove"

type wesnoth in the search box, and place a mark in the box before "the battle for wesnoth" program. Click apply. It will ask your password and install the latest stable release, 1.4 :popcorn:

---

### Post by Xbehave on 2008-06-25
> **Artificial Intelligence said:**
> Played it for awhile and I'm sure it will turn out to be hitter!!!
Great game!
Spot on, the game is pretty awesome.

---

### Post by cgroza on 2010-10-17
From the future here. THE GAME SIMPLY ROCKS. I AM AN ADDICT!

---

