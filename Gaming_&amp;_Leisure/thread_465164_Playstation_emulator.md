---
title: "Playstation emulator"
date: 2007-06-05
forum: Gaming &amp; Leisure
---

### Post by kaisho on 2007-06-05
i am having a problem setting up the playstation emulator (PCSX)  i am not sure if some one has already did a similar post but i would like a step by step guide on how to set it up, i just want to make sure i didn't screw up

---

### Post by acoustibop on 2007-06-05
PCSX, although a ground-breaking emulator in its day, is now long out of development, kaisho.  The two Playstation emulators for Linux now are [ePSXe]("http://www.epsxe.com/news.php") and [pSX]("http://psxemulator.gazaxian.com/").

ePSXe is also getting a little long in the tooth, although it still holds its own.  It hasn't been updated in nearly four years; even the PSEmu plugins are rarely updated now.

The newcomer and, I think, certainly the premier Playstation emulator ATM (it's less than 1 1/2 years old, and still in active development.  I've just come from the [pSX forum]("http://psxemulator.proboards54.com/")) is pSX.  The developer, pSX Author, posted the first (and so far only) Linux version about three months back, and it's superb.

It aims at accuracy of emulation rather than enhancement, unlike emulators such as ePSXe and PCSX, which can be a revelation in itself.  What I really like about it, though, is its 'transparency' - in other words, as happens when you're playing on a Playstation, it doesn't interpose itself between you and the game.  You just play.

In addition, it's very easy to install - just untar it to a folder, add a BIOS to taste - and games , images or CDs of course, and go.  You do want to install libgtkglext1 first, though.  Apart from controller setup, you can run it pretty much 'out of the box.'

There's also a very useful adjunct to it available on pSX forum too; one of the admins there has produced his [Ultima's pSX Frontend]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263").  Needs Python 2.5 and Python-GTK2.  Again, just untar it into the pSX folder and go.

Incidentally, a member here, dfreer, has started [maintaining installation packages]("http://ubuntuforums.org/showthread.php?t=394097") for pSX and Ultima's pSX Frontend.

---

### Post by Sockerdrickan on 2007-06-05
pSX is the best

---

### Post by DoktorSeven on 2007-06-05
> **acoustibop said:**
> 
It aims at accuracy of emulation rather than enhancement, unlike emulators such as ePSXe and PCSX, which can be a revelation in itself.  

What's funny about this is that I hear that said so much about pSX, yet half of the games I've tested on it just do not work, while a large majority of the games for ePSXe play perfectly or nearly so.

I'm not putting down pSX, really, it's a fine emulator, but it seems to me that the compatibility level of ePSXe is still higher.

---

### Post by acoustibop on 2007-06-05
That's strange, DoktorSeven - when pSX first started, yes, compatibility was way worse than ePSXe.  But compatibility, of course, has improved considerably - of the games I have, all run more or less in both emulators, but pSX is the one that generally runs them without problems.

Perhaps someone needs to do a survey on this.  My impression is about 50/50 ATM - between the two emulators, that is.

---

### Post by po0f on 2007-06-05
pSX++

The only game I've ever had a problem with is Bust A Groove.  I can't get this game to work with *any* emulator.  :(

As far as compatibility goes, I haven't had a problem with ePSXe, PCSX, or pSX (besides the aforementioned Bust A Groove).  I guess it just depends on the games you wish to play.


DoktorSeven,

I'm curious, which games are giving you problems?  I mainly play the Final Fantasies, Parasite Eve, Xenogears (NO I am not a Squaresoft fanboy!  ;)), the Breath of Fires, and Symphony of the Night.  If you didn't know, those are all RPGs.  Is it a particular genre of games that is giving you a problem?

---

### Post by disturbedite on 2007-06-05
> **Tux0r said:**
> pSX is the best
i have tried them all for linux & i will second that.  besides, most others are not being developed any more & psx is, so why not use it?

---

### Post by DoktorSeven on 2007-06-05
Well, I'm trying it again and it's actually better than I thought, though I have to rerun the emulator -- just  restarting (from the emulator menu) and changing the CD actually creates problems for some reason (sometimes it works fine doing that, sometimes it won't -- and I never had that problem on ePSXe).  However, there seems to still be more games I can play on ePSXe that give pSX problems.

The only other major problem -- sound.  pSX has problems with sounds (skipping, scratchy, etc).  I get sound-related messages from the console occasionally (mostly "buffer underrun").  And this is from both physical media and CD images, so it's not the media or anything like that.

ePSXe still seems to be the better emulator for me, but at least pSX isn't as bad as as I thought.

---

### Post by disturbedite on 2007-06-06
@DoktorSeven
i have lots of actual discs, copies, & disc images i've made and i've never experienced the problems you have with psx...

---

### Post by acoustibop on 2007-06-06
It's a good idea to do File -> Eject CD before loading a new image or CD.

FWIW I've had problems doing this with a completely different game (i.e. play one game, eject it and start another), but no problems changing discs within a game.  It's no more hassle to exit the emulator and restart it for a new game than to change discs - since you'll probably want to change memory cards as well, possibly BIOS (in which case you'd have to restart anyway) and controller type, the easiest way is to set them up in Ultima's pSX Frontend.  Exit the emulator, start a new game from the Frontend.  Three clicks.

Increase the latency in the Sound tab; that may not make the 'sound: underrun' messages go away, but generally fixes the sound problems.

Don't forget that 1.11 is actually the first Linux release of pSX, and that was released after less than a month of WIP testing by pSX forum members.  There are a number of bugs in it, most of which will hopefully be corrected in the second release.  I don't know what ePSXe's first Linux release was like, since I wasn't using Linux then, but was that better than pSX' first release?

---

### Post by dfreer on 2007-06-18
As for the sound skipping, try increasing the latency by about 10 ms or so, that should help some. Also, although it seems pSX doesn't support as many CD images as ePSXe, it seems that any original playstation game or plain .iso files work just great, I haven't had a single one mess up so far. Could you post the games you are having problems with, and what format they are in (original CD, .iso, .bin/.cue, .ccd, etc)?

---

### Post by Luksion Knight on 2007-06-26
perhaps your problems lie within the hardware within your computers. some emulators may utilize aspects such as memory and processor power differently, just like the the various linux kernels.

---

### Post by Sockerdrickan on 2007-06-27
Wonder when a new pSX version is coming...

---

### Post by RAH66 on 2007-06-27
you know you need a bios file??? right so if I have PS2 bios file will it work?

---

### Post by dfreer on 2007-06-27
> **RAH66 said:**
> you know you need a bios file??? right so if I have PS2 bios file will it work?

the PS2 bios would only work on a PS2 emulator, which so far the only one appears to be PCSX2.

---

### Post by acoustibop on 2007-06-27
> **Tux0r said:**
> Wonder when a new pSX version is coming...

pSX Author hasn't been posting much for a while; however, he has made a few posts recently.  From one of them (see the [pSX forum]("http://psxemulator.proboards54.com/index.cgi?board=general&action=display&thread=1182377460")):
> Since then I've been working on PS2 emulation (I may have some news about that soon). I will try to work on getting a new release of pSX together soon - I have fixed a couple of bugs (some to do with FF8)
which hopefully answers Tux0r's question and sheds a different light on dfreer's comment. ;)

---

### Post by dfreer on 2007-06-27
Thanks for the link! Yeah, it would be sweet if a new release of psx included PS2 support, cuz mine just broke recently :(

---

### Post by RAH66 on 2007-06-29
lol naughty me stumbled accross every bios made by sony lol:twisted:

---

### Post by Depressed Man on 2007-06-29
> **dfreer said:**
> Thanks for the link! Yeah, it would be sweet if a new release of psx included PS2 support, cuz mine just broke recently :(

Dunno about Linux, but I know there is a working PS2 emulator in Windows. Can't play all the games though, but Disgaea 1 and 2 works on it. :)

---

### Post by acoustibop on 2007-06-29
You're probably thinking of [PCSX2]("http://www.pcsx2.net/"), which is the Playstation 2 emulator dfreer referred to above.  There's a Linux version available, too.

---

### Post by gruffy-06 on 2007-10-15
I find that epsxe has the highest performance, since I can force games to run at custom frame rates. For example, I can play my PAL games at 60FPS, rather than have them run at a slower 50FPS.

---

### Post by acoustibop on 2007-10-15
That's fine if you want to emulate the game differently to how a Playstation would play it.  Personally, I prefer the accuracy of pSX over the enhancement abilities of ePSXe and other enhancing emulators.  It has a much greater quality of 'transparency' - that is, it interferes much less with actually getting into playing the game.

I can't help but feel that people who prefer the enhancing emulators may be more involved with playing with the emulator rather than with playing games.  Certainly, getting involved with getting your emulator working optimally can be fun but, for me, the whole thing is about playing the games.

---

### Post by Sarteck on 2007-11-21
acousticbop, I disagree.  First, there's gruffy's example--playing his PAL games at 60FPS, rather than 50, is less of what you call an "enhancement" and more of what you call "accuracy" (getting it to play at the frame rate it would normally have played at, had it been released in the USA or Japan).  There are many other instances, I am sure, that enhancing emulators might be and are chosen over transparent ones (pSX).

Personally, I chose pSX because I don't want to waste time mucking around finding which plugins go where and what will work best with my hardware, yadda yadda.  I actually do have some minor beefs with pSX (though some may be my computer and not pSX itself--one I am fairly sure is neither my computer nor pSX, but my keyboard).  FOr instance, resizing the screen.  When I play my games, I sometimes like to have another window or two open for chat and various other things, and place the windows side-by-side (I got my very first widescreen monitor not too long ago, and I love the hell out of it for thsi very reason).  However, if I want to resize the pSX screen, it doesn't keep the aspect ration, instead stretching the display horizontally or vertically.  It's just a minor annoyance, yes, but I wish I -could- keep the aspect ratio.

Next would be the sound controls.  When I am not in Full-Screen mode, it seems that the volume controls don't work at all, and I have to use the physical knob on my speakers to turn up or down the volume.  Again, not a huge deal, but sometimes I like to have my pSX volume down in comparison to the volume of other applications (so that I can hear, for instance, if someone messages me over IM, or whatever).

Still, these minor annoyances are much easier to put up with than the major ones I had to worry about with ePSXe when I was a Windows user.  To boot, the folks at the pSX forums seem a much friendlier bunch than other emulation forums--I guess it comes from not feeling like they're Gods because they know more about whichever plugins are hot. XD

---

### Post by acoustibop on 2007-11-21
But playing a game differently to the way it was meant to play on an emulator is enhancement, not accuracy, Sarteck.  A PAL game is meant to play at 50 fps.  If you want to play a game accurately at 60 fps, get an NTSC version.

Actually, I always rather enjoyed messing about with finding plugins for ePSXe and configuring them.  The reason I changed to pSX wasn't because it was easy to configure, but because of its transparency.  I've never played on another emulator where you get into playing the game so much, rather than into playing the emulator.

Are you using a monitor with a different aspect ratio than 4:3?  Because pSX has always kept its aspect ratio to 4:3 for me, full screen or windowed.

---

### Post by disturbedite on 2007-11-21
i agree whole-heartedly with acousticbop on this one about accuracy or luxurious features.

i however disagree with him on hunting around for plugins, hence one of the main reasons i prefer pSX.  :)

---

### Post by Sarteck on 2007-11-21
> **acoustibop said:**
> But playing a game differently to the way it was meant to play on an emulator is enhancement, not accuracy, Sarteck.  A PAL game is meant to play at 50 fps.  If you want to play a game accurately at 60 fps, get an NTSC version.

Actually, I always rather enjoyed messing about with finding plugins for ePSXe and configuring them.  The reason I changed to pSX wasn't because it was easy to configure, but because of its transparency.  I've never played on another emulator where you get into playing the game so much, rather than into playing the emulator.

Are you using a monitor with a different aspect ratio than 4:3?  Because pSX has always kept its aspect ratio to 4:3 for me, full screen or windowed.

Hey, some of my friends have games that are just hard to find anymore, PAL or NTSC.  So, unless we want to pirate them, then we would otherwise have no choice in our framerate.  "Enhancement" emulators give us the option to play those games at the "correct" FPS.

I don't know where the "playing the emulator" kick came from, but it's something I just don't agree with.  Sure, there are a few individuals out there who are obsessive over their emulators (and I really don't see anythign particularly wrong with that, it's just different).  By and large though, most people using emulators do so because they want to play the game.  NOT because the emulator can do this extra bit, or because it can do that extra bit, or whatever.  They're just happy that they can play their old games.

Continuing in that vein, when some of these people find out that they can make the game look better, play faster, sound nicer, etc., how can anyone fault them for wanting to do so?  I know I'd like to make MY gameplay experience as comfortable as possible (I wrap up in a blanket and shout for my girlfriend to bring me cup after cup of coffee, though, instead of fiddling with plugins).

You're thinking that such is "playing the emulator," but it's not.  Hell, if that was the case, when we adjusted our volumes to what level we wanted them to be, that would be "playing the emulator."



Also, I think you're crazy about finding the plugins and fiddling with them to get them just so.  XD  But that, too, is just an opinion (and meant in the spirit of jest, I'd better say, just in case--my humour sometimes gets lost on the Internet.  I need a Humour Plugin...).



As for aspect ratio, I'm guessing 16:10 (because when I use fullscreen and set that as my aspect ratio, I seem to get the picture closest to what it's supposed to be).  But... wait, let me give you a screenshot so you know what I mean...

Normal: [[IMG]http://img20.imageshack.us/img20/7585/normaldq2.th.png[/IMG]](http://img20.imageshack.us/my.php?image=normaldq2.png)

Stretched Horizontal:
[[IMG]http://img266.imageshack.us/img266/1613/stretchedhorizontalvk0.th.png[/IMG]](http://img266.imageshack.us/my.php?image=stretchedhorizontalvk0.png)

Stretched Vertical:
[[IMG]http://img409.imageshack.us/img409/7272/stretchedverticalef9.th.png[/IMG]](http://img409.imageshack.us/my.php?image=stretchedverticalef9.png)

This one might be normal, but I don't know, y'see?  That may be the correct aspect ratio, or it might be skewed: [[IMG]http://img20.imageshack.us/img20/5632/normalmaybepg7.th.png[/IMG]](http://img20.imageshack.us/my.php?image=normalmaybepg7.png)

Therefore, since I am not sure if it's skewed or not...  I just get annoyed at it.  I don't know why, it just pisses me off. XD  So I usually end up going full screen for a while.

---

### Post by acoustibop on 2007-11-22
But pSX is not _intended_ as an enhancing emulator, Sarteck.  I think a large part of the reason why pSX Author made an emulator that's around accurate rather than enhanced emulation is because of the artifacts that enhancement inevitably introduces.  Essentially, he wanted to make an emulator that played games as similarly to way the Playstation plays them as possible.  If you don't like that, don't complain here, complain to pSX Author in the pSX forum.  Not that that will have the slightest effect.

Your real complaint is not with pSX, but that enhancing emulators are not easier to install and configure, and don't run as well as pSX.  That isn't pSX Author's problem - complain to the enhancing emulator developers.  Not that that will help - the only Linux ones are ePSXe and PCSX and they're both long out of development.

You haven't answered my question, though - what is your monitor aspect ratio?  Also, what desktop resolution are you using?  As I've said, I've never had these problems with windows distorting in pSX, in Linux or in Windows, and nor do other people.  I think the most likely reasons for this might be that you've set a desktop resolution that's not appropriate for your monitor's aspect ratio, or that you've set an aspect ratio in pSX that's not appropriate for your monitor.  Until you answer those questions, we can't deal with the problem.

BTW by "playing the game... rather than... playing the emulator," I was referring to the way that the constant little slowdowns and artifacts in enhancing emulators tend to distract from the game and make you think about the emulator instead.  I've never found another emulator that distracts so little from the game as pSX does.  However, I guess that could be taken as a comment on the people who get obsessed about tweaking every little bit in their emulator and trying to impress other people with it.  It wasn't meant that way, though, and if you'd read my previous comment about 'transparency,' I would have thought you'd have understood that.

---

### Post by RavUn on 2008-01-10
So, I really want to play metal gear solid but I cannot find a Rom.  I have the 2 CDs, is it hard to create a Rom using those??  Or, is there a place I could find the Rom?

---

### Post by acoustibop on 2008-01-11
Very easy to rip your CDs, RavUn, as long as you're careful.  However, you shouldn't ask about finding 'ROMs' here: downloading Playstation games is illegal (also dumb - they're frequently faulty from careless ripping.  You can find most Playstation games cheaply and easily on ebay, Amazon and other games dealers and ripping is easy) and any reputable forum will not tolerate members asking where to find them.  BTW Playstation rips are usually referred to as images rather than ROMs.

To get back to ripping: see [this post from the pSX official forum]("http://psxemulator.proboards54.com/index.cgi?board=rules&action=display&thread=1195746305#1195747981") for a script for ripping CDs to the .bin/.cue image format.

The one problem with this is that the .bin/.cue format doesn't include subcode from the CD, and this can be necessary for defeating copy protection if the CD is protected.  The formats that do are the CloneCD .ccd/.img/.sub and Alcohol .mdf/.mds ones and, unfortunately, the only applications that will rip to these formats, [CloneCD]("http://www.slysoft.com/en/") and [Alcohol]("http://www.alcohol-soft.com/") (there's a free version of Alcohol 52%), are Windows only - they won't even run in Wine.

So you still need access to Windows to rip the optimum Playstation game images.  Ripping DVDs and Cds is about the only reason I still keep a copy of Windows going... :(

---

### Post by RavUn on 2008-01-11
Oh I see.  I will have to grab my games from my parents'... but I suppose I'd be better off just playing them on the console rather than going through the hassle to play on my computer with a crappy graphics card :P

Thanks for the info acoustibop.

---

### Post by acoustibop on 2008-01-12
Well, that's one of pSX' strong points, RavUn - since it emulates in software, the videocard is only needed to display the output: it has very little to do with the emulation.  As long as your card will do 3D rendering, that will generally be good enough.

Also, unlike ePSXe, which always seemed to me to be rather poor at playing games from CDs rather than images, pSX plays games from CDs very well, so generally, this is quite an acceptable way of playing them.  Images are more convenient if you have the hard drive space, though and, if you're starting pSX with [Ultima's pSX Frontend]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263") to play images, once you have the Frontend configured all you need is three or four mouse clicks to start any game with whatever options you want set. ;D

**Edit:** are you playing mainly NTSC or PAL games?  If you're playing NTSC games, very few of these are copy protected (some are mod protected, but this doesn't affect ripping) so the .bin/.cue format should be Ok.  Quite a few PAL games are copy protected, though, so formats that support subcode reading become much more important for these games.

---

### Post by BigSilly on 2008-01-12
Hiya. Been having a quick read through this thread and decided to dip a toe into PSX emulation on Linux. Downloaded pSX as it sounds like it may be the best bet, got the BIOS file needed, and after installing libgtkglext from the repository it seems to start OK. However I'm getting jittery audio, and the terminal outputs "sound underrun". 

What can I do to fix this? Cheers folks. :)

---

### Post by acoustibop on 2008-01-12
Increase the values for the Latency sliders on the Sound tab, BigSilly.  Ubuntu seems to be getting better for sound latency problems now, but this has always been a problem in Linux.

I have two Gutsy installations on this machine, one with the older 8.37.6 fglrx driver (installed with Restricted Drivers Manager) and one with the 7.12 fglrx driver.  Installing any of the more recent fglrx drivers seems to increse the inherent latency for the system, so for applications like pSX, which are more affected by sound latency than video requirements, the 8.37.6 fglrx driver installation is better, while for applications requiring faster 3d, and Compiz effects, the 7.12 fglrx driver installation is better.

Previously, I always found it necessary to increase the slider values slightly, but in Gutsy with the 8.37.6 fglrx driver, I find sound latency is now low enough to make this unnecessary.  With the 7.12 fglrx driver latency is increased and I still have to increase latency values.  But it depends on your sound card, as well.

Don't increase the values for the Latency sliders more than you have to: it's basically a delay, and if the latency values get too large, you get the sound going out of sync with the game.

---

### Post by BigSilly on 2008-01-12
That's lovely Acoustibop. Thanks for the info. So far it's all looking (and sounding) good. 

Now to eBay, to pick up some old favourites! :D

---

### Post by acoustibop on 2008-01-12
BTW try [Ultima's pSX Frontend]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263") as well, BigSilly.  You can set up profiles for all your games and start them with everything set as you want with a couple of mouse clicks.

This works particularly well, of course, if you rip your games to images.  You can point the Frontend to your image; if you're playing from CDs, you can only specify the drive - you've still got to dig out the game and put it in the drive.

I notice you're in Sheffield; that means you'll mostly be playing PAL games?  The .bin/.cue format generally works fine with NTSC games, which are not often protected, but quite a few PAL games are copy protected.  To defeat this, you need to rip to image formats that include subcode from the original CD: [CloneCD]("http://www.slysoft.com/en/")'s .ccd/.img/.sub or [Alcohol]("http://www.alcohol-soft.com/")'s .mdf/.mds.  Unfortunately, there are no applications that rip to these formats that will run in Linux, even in Wine. :(

DVD and CD ripping is about the only reason I keep a Windows installation going now.  If you are still running Windows, though Alcohol do do a free version of Alcohol 52% that will rip to either of those formats.

---

### Post by BigSilly on 2008-01-13
Excellent advice, thanks again Acoustibop. I am in the UK, it would be usually be PAL games I would have to buy, but I haven't bought any just yet so I reckon I'll go for the US discs off eBay. There's bound to be someone selling some here, or I could just get some from eBay US I would have thought. I don't run Windows anymore, unless I could get a mate of mine to rip them for me....

Either way I'll be having some fun on this! Cheers for all your info.

---

### Post by acoustibop on 2008-01-13
Ebay US, or try amazon.com as well, BigSilly.  They allow a number of games retailers to sell through their site; that's probably actually the best source for NTSC games.

As I said, ripping is about the only reason I keep a Windows installation going now - Slysoft's CloneDVD and CloneCD are such good protected DVD and CD rippers.  I really wish they'd do Linux versions; there must be quite a potential market for their products by now... :(

---

### Post by UK-Wobbie on 2008-01-13
pcsx is cool ](*,)

---

### Post by acoustibop on 2008-01-13
Cool in the sense of no longer warm, UK-Wobbie?  Try [pSX Emulator]("http://psxemulator.gazaxian.com/")... still (very much) alive!

---

### Post by BigSilly on 2008-01-16
Finally managed to get my hands on a handful of US PS games, and have to say this is really a great emu. I'm still having an issue with the sound, but only on Tekken 3 for some reason. There's a lot of skipping going on, though the game is fine to play.  I've tried carefully adjusting the latency bar, but it makes little difference. If I select frame skipping on, then the sound is better but the game plays like a pig. I thought my specs would be OK for PS1 emulation. I have a AMD Sempron 2200+ (1.5gz) with a Geforce FX5600XT 128Mb graphics card. I'm not sure, but I think my sound is just some on-board thing. I'm not sure, but I think I've seen AC 97 mentioned somewhere. Sorry I can't be clearer than that. It's not a great system, but I thought it might do for PS1 stuff.

Is there anything I can do to improve things, other than buy new hardware? Thanks.

---

### Post by acoustibop on 2008-01-16
No, Frame skipping never seems like a good option to me in pSX, BigSilly: even on machines too slow always to run pSX at full speed, I prefer the lower but smooth performance with Frame skipping off than the jerky performance with it on.  Yes, your system should be fine for pSX.  It'll generally run perfectly well on very mid-range systems, even on quite low end ones.  Since it really emulates in software, and only uses the videocard to display the output, the videocard really isn't critical - CPU, soundcard and memory are the governing factors although, as I said, none of these need to be particularly impressive.

If you only get the sound problem with Tekken 3, I'd think there is an issue with the game rather than your system, although Tekken 3 is in the Compatibility Lists as playing without problems.  Are you playing from a CD or an image and, if an image, what format?

---

### Post by BigSilly on 2008-01-16
Could be the rip I suppose. It's the US version [U] SLUS-00402, and a mate of mine ripped it into 2 files - a .bin and a .cue file. He reckoned that should be fine. I've heard a teensy bit of skipping on a couple of other games, but generally it's nothing serious and can be fixed with a tweak of the latency. My Tekken 3 is the exception for some reason. 

Is it worth asking him to do it again for me do you think?

---

### Post by acoustibop on 2008-01-16
Could well be the rip - but why not try ripping it yourself, BigSilly?  Here's a script posted on the PSX Official forum for [ripping CDs to .bin/.cue]("http://psxemulator.proboards54.com/index.cgi?board=rules&action=display&thread=1195746305&page=1#1195747981").

---

### Post by BigSilly on 2008-01-17
Thanks for that dude. I'll give that a shot when I get the chance, and I'll post up how it goes.

---

### Post by BigSilly on 2008-01-18
Just thought I'd bump this to ask if you (or indeed anyone) could tell me why I'm getting a "segmentation fault" when I try to use this emu in PCLinuxOS? I select the language, then it complains I don't have the BIOS file (which I do have, in the proper place too). I point it at the file, but then it closes with the above error message.

Thanks in advance.

---

### Post by acoustibop on 2008-01-18
Is that a BIOS you've used successfully elesewhere, BigSilly?

At a guess, it's either a permissions problem or a dependency one.

---

### Post by anjilslaire on 2008-01-18
I posted this in a non-related thread by mistake, so I'm reposting here (sorry mods):

After installing pSX 1.13, and supplying the bios, It loads up fine, but when I try to play a game, from either a .bin OR from an original PS1 disc, I get the error screen shown, and I have to reset the emulator. No games work at all, and even trying different region bioses have no effect. Any thoughts? I know my NTSC bios is good, because its works in windows-based psx emulators.

Running kubuntu 7.10 32b, 1 gig ram AthlonXP 3200+, nvidia 6600 GT with nividia drivers/3d is good.

---

### Post by kbless7 on 2008-01-18
> **anjilslaire said:**
> I posted this in a non-related thread by mistake, so I'm reposting here (sorry mods):

After installing pSX 1.13, and supplying the bios, It loads up fine, but when I try to play a game, from either a .bin OR from an original PS1 disc, I get the error screen shown, and I have to reset the emulator. No games work at all, and even trying different region bioses have no effect. Any thoughts? I know my NTSC bios is good, because its works in windows-based psx emulators.

Running kubuntu 7.10 32b, 1 gig ram AthlonXP 3200+, nvidia 6600 GT with nividia drivers/3d is good.


What does the terminal say when you run pSX through it?

---

### Post by anjilslaire on 2008-01-19
Here's what I get when I load & (try to) run The Legend of Dragoon disc1 (original disc, no scratches):

```

laire@sheeple:~$ psx

(psx:20675): GdkGLExt-WARNING **: Cannot open @ M\u0008L.so
sound: underrun
sound: underrun
linuxcd: [SGIO] Full subcode
sound: underrun
sound: underrun
sound: underrun
linuxcd: read toc - length=0012 first=1 last=1
linuxcd: track01: adr=01 control=04 addr=00000200
sound: underrun

```

thanks

---

### Post by acoustibop on 2008-01-19
The image you've posted isn't an error - it's intended behaviour on Sony's part, anjilslaire.  It's mod protection.  Emulators would seem to be seen by some mod protected Playstation games as modchipped Playstations, so the game won't play and you get the warning instead.

Hopefully, pSX Author will fix this at some point, but in the meantime there's a perfectly acceptable workaround for most mod protected games: use a PAL BIOS instead.  See the [Running Copy-Protected Games]("http://psxemulator.proboards54.com/index.cgi?board=support&action=display&thread=1156643206") thread on the official pSX forum.  Incidentally, I'm not sure this workaround will work for .bin./cue images: I would expect that mod protection is achieved, like copy protection, with the subcode on the CD; since .bin/.cue images don't include subcode, the game simply won't run if played from a .bin/.cue image.  However, it may be possible to patch a properly ripped .bin image.

Unfortunately, the only CD image formats that include subcode are CloneCD's .ccd/.img/.sub and Alcohol's .mdf/.mds ones, and there are no applications that will rip to these formats that will work outside of Windows.  So, to rip to these formats, you'll need access to a Windows PC.  In fact, ripping CDs and DVDs is pretty much the only reason I keep a Windows installation going now... :(

You say none of your games will work - what games are you trying?  Legend of Dragoon is known to be protected in this way; if you're getting the same warning screen with your other games, they must be mod protected too.  This is surprising, since mod protection (the only protection normally used with NTSC-US Playstation games) is not very common.  It would be quite unlikely, if you have many games, that they would all be mod protected, although not impossible.

However, there may be some other issues here.  From the messages in your second post, you're getting a GdkGLExt warning: libgtkglext1 may not be properly installed on your system.  The sound: underrun message isn't particularly important unless you're getting sound problems: if you are, then increase the values for the latency sliders on the Sound tab - not more than is needed, though.  Do you get these messages when the game goes to the mod protection warning screen or does the emulator crash before you run a game?

---

### Post by kbless7 on 2008-01-19
For some reason I'm getting this error when I try to run pSX. It was fine last time I used it. Any ideas?

```
matt@Matthew:~$ psx
/home/matt/.themes/OS X Leopard/gtk-2.0/panel.rc:58: Unable to locate image file in pixmap_path: "Panel/panel-bg-trans.png"
/home/matt/.themes/OS X Leopard/gtk-2.0/panel.rc:61: Background image options specified without filename
[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Device or resource busy'
psx: pcm_params.c:2276: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted (core dumped)

```

---

### Post by acoustibop on 2008-01-19
What sort of system are you running on, kbless7?  Looks like it might be Linux on a Mac, but which architecture?  pSX won't run in a Mac OS (except under Windows or Linux emulation - and then badly) and won't run on a PPC.

Looks like the problem is with your sound device.  Again, without information, it's difficult to guess.

---

### Post by kbless7 on 2008-01-19
Well it works today. I didn't even restart since then, so I have no clue what happened. I am running gutsy.

-Matt

---

### Post by anjilslaire on 2008-01-19
> **acoustibop said:**
> The image you've posted isn't an error - it's intended behaviour on Sony's part, anjilslaire.  It's mod protection.  Emulators would seem to be seen by some mod protected Playstation games as modchipped Playstations, so the game won't play and you get the warning instead.

Hopefully, pSX Author will fix this at some point, but in the meantime there's a perfectly acceptable workaround for most mod protected games: use a PAL BIOS instead.

That did the trick :) My own rip of my Dragoon disc (.bin) works great using scph7502.bin.

Thanks! I'm sure this'll handle my other discs too.

---

