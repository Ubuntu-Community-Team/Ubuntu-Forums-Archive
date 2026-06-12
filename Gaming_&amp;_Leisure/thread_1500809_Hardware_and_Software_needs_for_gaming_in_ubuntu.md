---
title: "Hardware and Software needs for gaming in ubuntu"
date: 2010-06-03
forum: Gaming &amp; Leisure
---

### Post by Experimental on 2010-06-03
I have nvidia gt9600 and nvidia drivers are installed. What I want to know is;

How safe is to play a game in ubuntu. which needs high system requirements. Lets say the game needs dx9.0c etc. Can any damage come to my hardware ?

My mainboard has driver called easy-tune it auto arranges fan speed etc. Does linux have default things like this ? 

I hope you understand what I'm trying to say =)

Windows has all the pc's required drivers and linux doesn't. I'm afraid(maybe not afraid but anxious) that harm will come to my pc

---

### Post by Noraphalem on 2010-06-03
I am sure Ubuntu GNU/Linux will not harm your computer.

All the drivers for your hardware are - normally - located in the kernel.
The fan speed is normally controlled by the BIOS.

Your PC/OS should be ready for gaming. What game do you want to play?

---

### Post by u235sentinel on 2010-06-03
> **Experimental said:**
> I have nvidia gt9600 and nvidia drivers are installed. What I want to know is;

How safe is to play a game in ubuntu. which needs high system requirements. Lets say the game needs dx9.0c etc. Can any damage come to my hardware ?

My mainboard has driver called easy-tune it auto arranges fan speed etc. Does linux have default things like this ? 

I hope you understand what I'm trying to say =)

Windows has all the pc's required drivers and linux doesn't. I'm afraid(maybe not afraid but anxious) that harm will come to my pc

No harm will come to your pc, unless you run Windoze of course ;-)

I purchase hardware which is well supported under linux.  The only risk of installing linux is you could find hardware that no drivers have been created for that device, which means it simply won't work (or work well) under linux.

I've never heard of a case where a computer was damaged by running Linux (though I've heard plenty of stories of computers running Windoze which were harmed physically).  Not sure if there is any credence but I've heard of this stuff.

Your comment on the motherboard settings isn't handled by an operating system.  It's handled by the onboard BIOS chip which comes with your motherboard (yeah I know that was answered already.. reinforcement dude...)

 You have a good video card so it should be able to handle just about any linux games you throw at it.  If running Wine then probably any well supported games under wine will work as well.

Oh and I run a whole bunch of Windows and Linux games on my ubuntu 10.04 computer.  The only problem I've run into is kubuntu and dolphin every now and then.  It's really annoying for it to just die without an explanation.  but that's ok, it's easily fixed by running konqueur :D

Have fun!

---

### Post by Experimental on 2010-06-03
I see what you mean. I don't talk about any particular game. Grim Fandango or Batman Arkham Asylum. It doesn't matter which game I just wanted to know how that works under linux. I wanted to know will anything can overdose my computer and crash it and burn it into million pieces :P

---

### Post by cascade9 on 2010-06-03
> **u235sentinel said:**
> No harm will come to your pc, unless you run Windoze of course ;-)

I purchase hardware which is well supported under linux.  The only risk of installing linux is you could find hardware that no drivers have been created for that device, which means it simply won't work (or work well) under linux.

I've never heard of a case where a computer was damaged by running Linux (though I've heard plenty of stories of computers running Windoze which were harmed physically).  Not sure if there is any credence but I've heard of this stuff.

I actually have heard of hardware being fried under linux. To be fair, that was caused by the (early) 195 nVidia drivers, and it wasnt a linux only issue. A lot of windows users got burnt by the early 195 drivers as well. ;)

---

### Post by portets on 2010-06-03
> **cascade9 said:**
> I actually have heard of hardware being fried under linux. To be fair, that was caused by the (early) 195 nVidia drivers, and it wasnt a linux only issue. A lot of windows users got burnt by the early 195 drivers as well. ;)

i heard that it was a windows issue. but since the nvidia windows and linux drivers share a lot of code, nvidia advised against using certain drivers.

from what i know, there were no reported cases of those drivers affecting linux users, just some windows users.

---

### Post by cascade9 on 2010-06-03
> **portets said:**
> i heard that it was a windows issue. but since the nvidia windows and linux drivers share a lot of code, nvidia advised against using certain drivers.

from what i know, there were no reported cases of those drivers affecting linux users, just some windows users.

There was actually someone on this forum who had card death after using the 195.36.03/08 drivers (gah, to braindead to find that post now), and there is also somebody on the arch forums (post 18 )- 

[http://bbs.archlinux.org/viewtopic.php?id=92619](http://bbs.archlinux.org/viewtopic.php?id=92619)

There was a lot less linux users afected than windows users, but that IMO is because of 2 reasons, aside from the number of users. 1- the repos that most linux users use, 2- (connected to 1) driver discs tend to come with ancient driver versions, windows users normally have the choice between uning very old drivers or the newest, and 3- the hardcore gamers 'upgrading my drivers now for an extra 0.1% increase in framerates' users tend to be on windows.

---

### Post by hikaricore on 2010-06-04
Keep in mind if you intend to play windows games on linux you'll need to use wine as many of these games do not have native binaries and will not run directly on linux.
Our wine forum is located here: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)
Be sure to read the stickies and check the appdb before posting.

---

### Post by Experimental on 2010-06-05
I know wine and what I was trying to ask is playing high requirement games on wine in ubuntu

---

### Post by Artemis3 on 2010-06-05
Hmm you card is a little too weak (Batman needs 9800) for you to worry about such things. But note what wine DirectX support can be a little different, ie, up to dx9 but not ALL of it. They are also starting to support some dx10 features.

Native games are best, this usually means OpenGL, since dx is a microsoft thing.., but OpenGL is an open standard. Soon we might see source engine games (ie HalfLife, CounterStrike, Team Fortress, etc) working since they already have it running on MacOSX (OpenGL), and a steam port seems on the way as well.

As for Phyx games (ie. Batman), is nvidia even supporting that on their linux drivers? I would stick to dx9/opengl games, and search appdb.winehq for status (working, garbage, etc). In any case the 9600 is a weak puny card :)

---

### Post by cascade9 on 2010-06-06
> **Artemis3 said:**
> Hmm you card is a little too weak (Batman needs 9800) for you to worry about such things. But note what wine DirectX support can be a little different, ie, up to dx9 but not ALL of it. They are also starting to support some dx10 features.

Where did you hear that? 

> ** [Batman Arkham Asylum System Requirements]("http://www.gamesrequirements.com/2009/01/minimum-system-requirements-os-windows.html") **

        [FONT=times new roman][COLOR=#00cccc]Minimum System Requirements[/COLOR]
OS: Windows XP Sp2/Vista Sp1
Processor:P4 2.8GHz (3.2GHz Vista)/Athlon 64 3000+ (3200+ Vista)
Memory:1GB (1.5GB Vista)
Hard Drive:12GB
Video Memory: graphics card with 256MB (SM 2.0b). NVidia 6800 or ATI X700.
Sound Card:DX9.0c compliant
DirectX:9.0C
Keyboard & Mouse
DVD Rom Drive

[COLOR=#00cccc]Recommended System Requirements[/COLOR]
OS: Windows XP Sp2/Vista Sp1
Processor:Core 2 Duo 2.2GHz processor family/Athlon 64 X2 4400+ (required for MP host)
Memory: 2 GB RAM
Hard Drive:12 GB
Video Memory: graphics card with 512MB (SM 3.0). NVidia 8600 GTS or ATI HD 2900 XT.
Sound Card:DX9.0c compliant
DirectX:9.0C [/FONT]It *might* 'need' a 9800 to run in WINE, but it sure doesnt on windows. 

Good advice on checking WINEhq, and heres the link to the 1.1 (steam) version- 

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19065](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19065)

---

