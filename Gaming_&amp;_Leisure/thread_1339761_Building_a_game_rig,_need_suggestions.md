---
title: "Building a game rig, need suggestions"
date: 2009-11-27
forum: Gaming &amp; Leisure
---

### Post by jessiebrownjr on 2009-11-27
Hey guys! I'm aware most of the games I'm interested in probably won't work with Linux but what my main concerns are need to be addressed as well I suppose. Are most good ATI/nvidia cards usually really compatible with Ubuntu/wine/any other popular emulators?
If you have good or bad experiences with them, please let me know. I have a geforce 8400 on my desktop at the moment but I can't tell if its good or bad cause there isn't really a linux game to strain it...

For instance I couldn't play WoW through Wine because of drivers, and I'd like to avoid this if I can when I can hand build my next PC. Sorry if this post is vague, but help if you can!
Thanks!
:popcorn:

---

### Post by PariahVayne on 2009-11-27
> **jessiebrownjr said:**
> Hey guys! I'm aware most of the games I'm interested in probably won't work with Linux but what my main concerns are need to be addressed as well I suppose. Are most good ATI/nvidia cards usually really compatible with Ubuntu/wine/any other popular emulators?
If you have good or bad experiences with them, please let me know. I have a geforce 8400 on my desktop at the moment but I can't tell if its good or bad cause there isn't really a linux game to strain it...

For instance I couldn't play WoW through Wine because of drivers, and I'd like to avoid this if I can when I can hand build my next PC. Sorry if this post is vague, but help if you can!
Thanks!
:popcorn:
I can play WoW on my GeForce 5700 which uses a dated driver. You should easily be able to with a 8400!

What are some of the games you were interested in playing?

---

### Post by rednano12 on 2009-11-27
From what I've heard, NVidia cards have great support.

---

### Post by jessiebrownjr on 2009-11-27
Thanks for the replies guys. I could get wow to load via some of the tutorials that I saw. I modified things accordingly to get it to let me zone in, but it always crashed afterwards. about 10-15 seconds into loading. After that, I exhausted my searching and modiyfing of files and had zero luck, so I gave up on WoW. BUT thank the lord, I quit playing WoW after 4 years and Im very happy I did hehe. Lately I've been playing Quake 4/Doom 3 on windows, so pretty much games like that. I'm content with just using Windows for games since that seems to be the going trend, but if I can avoid it I will. Im aware there are windows emulators for games that are better then Wine that cost a fee, which might be an option as well in the future. 

Considering I might be going into software developing and/or electronics engineering I'll probably keep windows and linux both for various compatibility reasons I can't forsee yet.

So nvidia you say, sounds good... I haven't put any effort into attempting to try to play doom 3 over linux because I *assumed* I'd get better graphics results running it natively over XP/vista. Are these assumptions correct, or do the emulators not really lag that much? Windows probably has extra processes going on (antivirus and firewalls and whatnot) vs linux, but not sure how much that comes into play. If I build a gaming rig to play cutting edge games of course, it would matter.

---

### Post by PariahVayne on 2009-11-27
> **jessiebrownjr said:**
> Thanks for the replies guys. I could get wow to load via some of the tutorials that I saw. I modified things accordingly to get it to let me zone in, but it always crashed afterwards. about 10-15 seconds into loading. After that, I exhausted my searching and modiyfing of files and had zero luck, so I gave up on WoW. BUT thank the lord, I quit playing WoW after 4 years and Im very happy I did hehe. Lately I've been playing Quake 4/Doom 3 on windows, so pretty much games like that. I'm content with just using Windows for games since that seems to be the going trend, but if I can avoid it I will. Im aware there are windows emulators for games that are better then Wine that cost a fee, which might be an option as well in the future. 

Considering I might be going into software developing and/or electronics engineering I'll probably keep windows and linux both for various compatibility reasons I can't forsee yet.

So nvidia you say, sounds good... I haven't put any effort into attempting to try to play doom 3 over linux because I *assumed* I'd get better graphics results running it natively over XP/vista. Are these assumptions correct, or do the emulators not really lag that much? Windows probably has extra processes going on (antivirus and firewalls and whatnot) vs linux, but not sure how much that comes into play. If I build a gaming rig to play cutting edge games of course, it would matter.

The graphics on Doom III/Quake IV in Linux are exactly the same as they are in Windows. They also play pretty much identically in WINE as they do natively as they are both OpenGL based. WINE just acts as a basic interpreter for .EXE(s)

NVidia is they best choice definitely, but ATI have improved a lot in the past 9 months.

WINE is also more advanced than Cedega or CrossOver games.

---

### Post by jessiebrownjr on 2009-11-27
I just attempted to run doom 3 off my NTFS drive via wine, it loaded and ran smoothly up until the point of me loading in the world then I just got a blank/black screen and an un responsive system... Im on a laptop with no graphics card though so Ill try again when I get home.. Ill enable the FPS meter (imassuming it has one) and ill check it windows xp vs linux/wine and see how it runs... I did notice that the planet mars behind the doom logo was broken, but well see how it goes on my desktop before I complain!

So is it direct X that gives linux/wine problems then since openGL is apparently kosher?

Thanks!

---

### Post by PariahVayne on 2009-11-27
> **jessiebrownjr said:**
> I just attempted to run doom 3 off my NTFS drive via wine, it loaded and ran smoothly up until the point of me loading in the world then I just got a blank/black screen and an un responsive system... Im on a laptop with no graphics card though so Ill try again when I get home.. Ill enable the FPS meter (imassuming it has one) and ill check it windows xp vs linux/wine and see how it runs... I did notice that the planet mars behind the doom logo was broken, but well see how it goes on my desktop before I complain!

So is it direct X that gives linux/wine problems then since openGL is apparently kosher?

Thanks!

What chip does the laptop have? If it's Intel then it will have problems with Doom III.

As for DirectX, WINE does a great job emulating DirectX9 mostly. DirectX 10(Vista/7 version of DirectX) is being worked on. 

I'm no expert with WINE, but as I undertand how it works with DirectX stuff is to call the OpenGL equivalent of the DirectX command. So basically it would be;

DirectX command into WINE => WINE calls the OpenGL equivalent => OpenGL carries out the command.

---

### Post by jessiebrownjr on 2009-11-28
The craptop(lol) does have an intel chip, as well as an intel core 2 duo processor..

The desktop has geforce 8400 and athlon 64 x2.

Ok so I can see wine doing great with a native openGL game, and degraded perfomance due to translation with the directX conversion?

---

### Post by PariahVayne on 2009-11-28
> **jessiebrownjr said:**
> The craptop(lol) does have an intel chip, as well as an intel core 2 duo processor..

The desktop has geforce 8400 and athlon 64 x2.

Ok so I can see wine doing great with a native openGL game, and degraded perfomance due to translation with the directX conversion?

Basically but sometimes DirectX based games can be quicker under WINE than Windows. 

WINE is kind of try it and see.

---

### Post by jessiebrownjr on 2009-11-28
Alrighty, when I get back to my lovely desktop I'll tool around with Wine and see if I can get doom 3 to run. I've never had a computer that could run top of the line games and make it look pretty at the same time, so thats my goal this time around but we'll see how that goes.. hehe...

---

### Post by PariahVayne on 2009-11-28
> **jessiebrownjr said:**
> Alrighty, when I get back to my lovely desktop I'll tool around with Wine and see if I can get doom 3 to run. I've never had a computer that could run top of the line games and make it look pretty at the same time, so thats my goal this time around but we'll see how that goes.. hehe...

Doom III hasn't been top of the line since 2005 =P

---

### Post by jessiebrownjr on 2009-11-28
I went to the wine forums/irc channel and nvidia is apparently the winner there. They said that the games are pretty much a crapshoot on if they will work or not but naturally openGL games work better. So, I guess I'll just make sure I get a great nvidia card and build it the best my wallet will allow ;-)

---

### Post by PariahVayne on 2009-11-28
> **jessiebrownjr said:**
> I went to the wine forums/irc channel and nvidia is apparently the winner there. They said that the games are pretty much a crapshoot on if they will work or not but naturally openGL games work better. So, I guess I'll just make sure I get a great nvidia card and build it the best my wallet will allow ;-)

Yeah NVidia is awesome with Linux. Good luck getting a decent card.

---

### Post by cascade9 on 2009-11-28
Be carefull if you go over, say 9600GT/GT220. Some of the higher end nVidia cards need a lot of power, and power connections not every PSU has.

---

### Post by alienclone on 2009-11-28
if you are "building a game rig" then my "suggestion" would be to run Windows.

if all you plan to do on it is play Windows native games, then do it in Windows.

---

### Post by jessiebrownjr on 2009-11-28
> **alienclone said:**
> if you are "building a game rig" then my "suggestion" would be to run Windows.

if all you plan to do on it is play Windows native games, then do it in Windows.

BLASPHEMY!
I did alot of reading last night on the wine forums and talked to a few folks in IRC. Some games that work on Wine run faster then on Windows and some work faster on Windows, depends on alot of stuff.. But, I'll have the best of both worlds!

No but its not purely for gaming, its going to be capable of it for once... and lol@hasn't been on top sense 2005, I know that, guess my sentence came out wrong..

Yeah I'll make sure I get a huge PSU. I'm going to run SLI I think and go nuts on it.

I was looking at lots of computer specs you can build yourself for a grand, seems to be good.

---

### Post by cascade9 on 2009-11-28
IMO, SLI is for 3 sorts of people. 

1- "I've already got a *insert card name here* eg a 9800, and rather than go buy  a newer, faster card I'll just shove a 2nd 9800 in there. 

2- Look at my SLI setup! *lots of links to pics*

3- I really, really, really want to run crysis at max settings with a good framerate, so I'm getting x2 GT 295s cause theres nothing out there with more guts.....unless  get x3 or x4 Gt 295s! Woohoo! 

A single video card, for similar costs to x2 SLI cards, is normally about as fast..or faster. On a 1K budget, its pointless, unless you want the cachet of SLI. A GT 295 will go for over $500, and I cant imagine that you'll be spending 1/2 your budget on a card.

---

### Post by jessiebrownjr on 2009-11-28
> **cascade9 said:**
> IMO, SLI is for 3 sorts of people. 

1- "I've already got a *insert card name here* eg a 9800, and rather than go buy  a newer, faster card I'll just shove a 2nd 9800 in there. 

2- Look at my SLI setup! *lots of links to pics*

3- I really, really, really want to run crysis at max settings with a good framerate, so I'm getting x2 GT 295s cause theres nothing out there with more guts.....unless  get x3 or x4 Gt 295s! Woohoo! A single video card, for similar costs to x2 SLI cards, is normally about as fast..or faster. On a 1K budget, its pointless, unless you want the cachet of SLI. A GT 295 will go for over $500, and I cant imagine that you'll be spending 1/2 your budget on a card.

As for your number 1 post..according to nivdia's SLI stats. Card A times 2 = twice as fast literally, 3 of card A was 2.8x as fast as 1 card. See how they stack? I don't think you can get that much of an upgrade just getting a new solo card. 

point 2) I would only text like 1 guy I know about it :-)



Im pretty sure, I could find cards that are less then half the price of the top dog single card, and use them together to out perform it. I remember the #1 speed slot item always had a hefty extra price on it, and if you got the 2nd or 3rd, the price dropped drastically. 

And I would be #3 on your list. I just bought a large pretty high def monitor to use :-). from the time I've had a computer, my computer was always marginal about running the new games.. would run them... with bad FPS and low settings.. I do indeed want to finally have a gaming toy that will run it were it lacks those flaws. 

Correct me if I'm wrong here, but can't certain number cruching applications use GPU cores now to assist with processing? I swore I saw it done before... atleast in the realm of wep cracking or something the like. 

If the fact above is true then I'll for sure be getting as many cores as I can and jam them in as many holes as I can :-p...

---

### Post by PariahVayne on 2009-11-28
> **jessiebrownjr said:**
> As for your number 1 post..according to nivdia's SLI stats. Card A times 2 = twice as fast literally, 3 of card A was 2.8x as fast as 1 card. See how they stack? I don't think you can get that much of an upgrade just getting a new solo card. 

point 2) I would only text like 1 guy I know about it :-)



Im pretty sure, I could find cards that are less then half the price of the top dog single card, and use them together to out perform it. I remember the #1 speed slot item always had a hefty extra price on it, and if you got the 2nd or 3rd, the price dropped drastically. 

And I would be #3 on your list. I just bought a large pretty high def monitor to use :-). from the time I've had a computer, my computer was always marginal about running the new games.. would run them... with bad FPS and low settings.. I do indeed want to finally have a gaming toy that will run it were it lacks those flaws. 

Correct me if I'm wrong here, but can't certain number cruching applications use GPU cores now to assist with processing? I swore I saw it done before... atleast in the realm of wep cracking or something the like. 

If the fact above is true then I'll for sure be getting as many cores as I can and jam them in as many holes as I can :-p...


SLi (2 cards) = about 1.5 in most things depending on the cards.

As for the CPU there is little point owning a quadcore on Linux for games. WINE can play few games that require that kind of muscle, and anything native will run perfectly on a single core. If you must get a multicore I would suggest getting the fastest dualcore possible.

---

### Post by jessiebrownjr on 2009-11-28
> **PariahVayne said:**
> SLi (2 cards) = about 1.5 in most things depending on the cards.
 
As for the CPU there is little point owning a quadcore on Linux for games. WINE can play few games that require that kind of muscle, and anything native will run perfectly on a single core. If you must get a multicore I would suggest getting the fastest dualcore possible.
 
Well im sure Nvidia pads there results somewhat, but they said almost twice as fast for 2 SLI and 2.8 times as fast for 3 sli... but regardless.
 
My main concern isn't Linux only, I just wanted to make sure that my rig was as linux compatible as possible.  Apparently according to wine, that just means get new Nnvidia cards :-)
 
And I might be wrong, but I think you are confusing the cores with 32 bit/64 bit OS issues and the like. Wine doesn't directly control what information is set to what core on the processor, I think that would be done on the motherboard level or vice versa. If you can find some research that says otherwise, I'd love to hear it honestly cause I'm out of the loop. 
 
Naturally if I want to build a pretty cutting edge gaming system, I might have to run straight up Windoze if Wine doesn't cut it. As far as getting the best dual core there is? They are going to phase those out slowly, and if I want a good motherboard that can support new features/new cpu architectures, I have to get the best technology available--like quad core Intel stuff.

---

### Post by PariahVayne on 2009-11-28
> **jessiebrownjr said:**
> Well im sure Nvidia pads there results somewhat, but they said almost twice as fast for 2 SLI and 2.8 times as fast for 3 sli... but regardless.
 
My main concern isn't Linux only, I just wanted to make sure that my rig was as linux compatible as possible.  Apparently according to wine, that just means get new Nnvidia cards :-)
 
And I might be wrong, but I think you are confusing the cores with 32 bit/64 bit OS issues and the like. Wine doesn't directly control what information is set to what core on the processor, I think that would be done on the motherboard level or vice versa. If you can find some research that says otherwise, I'd love to hear it honestly cause I'm out of the loop. 
 
Naturally if I want to build a pretty cutting edge gaming system, I might have to run straight up Windoze if Wine doesn't cut it. As far as getting the best dual core there is? They are going to phase those out slowly, and if I want a good motherboard that can support new features/new cpu architectures, I have to get the best technology available--like quad core Intel stuff.

You're wrong but that's ok. Good luck!

---

### Post by a!man_96 on 2009-11-28
*Nvidia 9400Gt is nice..*

---

### Post by jessiebrownjr on 2009-11-29
> **PariahVayne said:**
> You're wrong but that's ok. Good luck!

Terrible reply...

I proved myself wrong because I'm an electronics tech and this is how you do it, with facts and research!

[HTML]http://www.codinghorror.com/blog/archives/000942.html[/HTML]

It is up to the SOFTWARE that is being run, not the OS. The software has to be told to use more then 1 core, it has nothing to do with the os. (Wine might be an exception, im posting on the winehq to ask)

If you read that post, it explains the benefits of having a dual core etc, or a tricore.

Such as closing a program that stole all yoru CPU, because you have other, idle cpus to do so.

But it seems that, unless games are enabled to use all of dual/quad, dual is good.

If the speed is downgraded to upgrade to a quad core, then you lose out it seems most of the time. If there comes a point in time where they stop making duals, or quad speeds get much higher, then it won't matter, it will just be a price issue. 

But currently it seems you are correct, a fast dual is the way to go, thanks for the heads up!

---

### Post by PariahVayne on 2009-11-29
Ok if you're an eletronics tech then you know that the software has to be written to take advantage of multicore CPUs. Also, if you're an electronics tech, why do you need advice from random people on a forum about what components to get for your new PC?

---

### Post by jessiebrownjr on 2009-11-29
The fact that I worked on SATCOM systems in the navy has nothing to do with software compabilties or gaming systems WHAT so ever. 

There are computer SCIENCE majors (software right?)
Computer ENGINEERING majors (hardware+low level software/os/drivers i think)
new field**
Electronics engineers (they know everyting, i'm not this guy)
and electronics techs (hand me a manual and I can what the engineer built)


Im in the very beginning of learning how computer engineering works.

If you can't attempt to be helpful or informative with your posts then don't post in the thread of mine please. I don't recall saying I was 100% sure of something.
quote:
And I might be wrong, but I think you are confusing the cores with 32 bit/64 bit OS issues and the like. Wine doesn't directly control what information is set to what core on the processor, I think that would be done on the motherboard level or vice versa. If you can find some research that says otherwise, I'd love to hear it honestly cause I'm out of the loop.

I'm not trying to go off on an ego trip, bit its common courtesy to tell somebody why they are confused/wrong (if thats the case) instead of rudely saying you are wrong but good luck. Lets keep this thread from turning into a flame war, and more into informative so we can all learn something?

edit:
I looked back over your posts and you are a very informed individual, hardly from a "random person." The error I saw was where you said Wine cant play dot dot dot... I made my assumption, we were both wrong, and I showed the proof... That isn't that big of a deal, its the games fault :-)

---

### Post by PariahVayne on 2009-11-29
> **jessiebrownjr said:**
> The fact that I worked on SATCOM systems in the navy has nothing to do with software compabilties or gaming systems WHAT so ever. 

There are computer SCIENCE majors (software right?)
Computer ENGINEERING majors (hardware+low level software/os/drivers i think)
new field**
Electronics engineers (they know everyting, i'm not this guy)
and electronics techs (hand me a manual and I can what the engineer built)


Im in the very beginning of learning how computer engineering works.

If you can't attempt to be helpful or informative with your posts then don't post in the thread of mine please. I don't recall saying I was 100% sure of something.
quote:
And I might be wrong, but I think you are confusing the cores with 32 bit/64 bit OS issues and the like. Wine doesn't directly control what information is set to what core on the processor, I think that would be done on the motherboard level or vice versa. If you can find some research that says otherwise, I'd love to hear it honestly cause I'm out of the loop.

I'm not trying to go off on an ego trip, bit its common courtesy to tell somebody why they are confused/wrong (if thats the case) instead of rudely saying you are wrong but good luck. Lets keep this thread from turning into a flame war, and more into informative so we can all learn something?

You assumed to know my pattern of thought and were wrong, I merely replied. You were the one who seemed to take offence at this. 

But anyway, good luck .

---

### Post by PariahVayne on 2009-11-29
> **jessiebrownjr said:**
> edit:
I looked back over your posts and you are a very informed individual, hardly from a "random person." The error I saw was where you said Wine cant play dot dot dot... I made my assumption, we were both wrong, and I showed the proof... That isn't that big of a deal, its the games fault :-)

Good man for being to able to admit your mistake but I don't quite understand what you mean by;

> The error I saw was where you said Wine cant play dot dot dot...

Could you please enlighten me?

---

### Post by jessiebrownjr on 2009-11-29
> **PariahVayne said:**
> You assumed to know my pattern of thought and were wrong, I merely replied. You were the one who seemed to take offence at this. 

But anyway, good luck .

I didn't assume to know your pattern of thought, its called reading comprehension. You said something in way that led me to believe something, with which I disagreed. I posted my reply to get factual information or informed opinions on the subject from other people as well (the point of a forum) and also to get information to inspire me to look into things to plan out my system. 

I'm actually asking you this, not to be a jerk but, why do you think wine can't run more then one core? Is it written out in a FAQ somewhere, or is it just assumed to be that way because of the programs that use it? my quick search showed that people noticed certain programs only used 1/2 or 1/4 of their cores, but that wasn't JUST in wine. Is wine an exception that illiminates dual core processing?

---

### Post by PariahVayne on 2009-11-29
> **jessiebrownjr said:**
> I didn't assume to know your pattern of thought, its called reading comprehension. You said something in way that led me to believe something, with which I disagreed. I posted my reply to get factual information or informed opinions on the subject from other people as well (the point of a forum) and also to get information to inspire me to look into things to plan out my system. 

I'm actually asking you this, not to be a jerk but, why do you think wine can't run more then one core? Is it written out in a FAQ somewhere, or is it just assumed to be that way because of the programs that use it? my quick search showed that people noticed certain programs only used 1/2 or 1/4 of their cores, but that wasn't JUST in wine. Is wine an exception that illiminates dual core processing?

Where did I say that WINE can't run more than one core?

---

### Post by jessiebrownjr on 2009-11-29
> **PariahVayne said:**
> SLi (2 cards) = about 1.5 in most things depending on the cards.

As for the CPU there is little point owning a quadcore on Linux for games. WINE can play few games that require that kind of muscle, and anything native will run perfectly on a single core. If you must get a multicore I would suggest getting the fastest dualcore possible.

This isn't you directly saying it, but it is what led me to believe it. You said "wine can play few games" that is semi-vague. It makes it seem like the core issue is up to wine. And also, anything native will run on a single core.  This statement here, once again, should be attributed to the software being ran, but not the OS running it. I thought it would be a hardware issue on how the cores were utilizied, but I was wrong. I infered you said it was Wine that limited the cores... Is that what you meant to say?

This whole debate is getting silly lol, I said you led me to believe something (whether intentional or not), and I said my opinion. If you already know what I'm saying to be true, then thats dandy, but the way you said it to me was confusing. I guess it was the military or my tech training but I make assumptions based on what I read, because I expect things to be said semi-literally.  I'm not trying to insult you in any fashion. Just learning !

healthy debates make one stronger! :-) :popcorn:

---

### Post by PariahVayne on 2009-11-29
> **jessiebrownjr said:**
> This isn't you directly saying it, but it is what led me to believe it. You said "wine can play few games" that is semi-vague. It makes it seem like the core issue is up to wine. And also, anything native will run on a single core.  This statement here, once again, should be attributed to the software being ran, but not the OS running it. I thought it would be a hardware issue on how the cores were utilizied, but I was wrong. I infered you said it was Wine that limited the cores... Is that what you meant to say?

This whole debate is getting silly lol, I said you led me to believe something (whether intentional or not), and I said my opinion. If you already know what I'm saying to be true, then thats dandy, but the way you said it to me was confusing. I guess it was the military or my tech training but I make assumptions based on what I read, because I expect things to be said semi-literally.  I'm not trying to insult you in any fashion. Just learning !

healthy debates make one stronger! :-) :popcorn:

Ah I see. To put it simply it's experience. After a while you get a feel for WINE. I've also set up plenty of stuff on other peoples machines. You learn pretty fast what sort of things work and what doesn't.

As to native stuff, there just isn't a game that pushes a single core to the max yet. Sad but true.

---

### Post by cascade9 on 2009-11-29
> **jessiebrownjr said:**
> Well im sure Nvidia pads there results somewhat, but they said almost twice as fast for 2 SLI and 2.8 times as fast for 3 sli... but regardless.
 
And I might be wrong, but I think you are confusing the cores with 32 bit/64 bit OS issues and the like. Wine doesn't directly control what information is set to what core on the processor, I think that would be done on the motherboard level or vice versa. If you can find some research that says otherwise, I'd love to hear it honestly cause I'm out of the loop. 
 
Naturally if I want to build a pretty cutting edge gaming system, I might have to run straight up Windoze if Wine doesn't cut it. As far as getting the best dual core there is? They are going to phase those out slowly, and if I want a good motherboard that can support new features/new cpu architectures, I have to get the best technology available--like quad core Intel stuff.

nVidia probably dont so much 'pad' results as pick and choose the games they use as examples. Some games get a nice bonus from SLI, some dont. I'd always go for single card, if your SLI setup doesnt do what you want it to, its get 2 whole new video cards. Buy a higher end single card, and if your not getting what you want, buy another. 

Nah, PariahVayne isnt making a 32/64 bit mistake. Most games dont use quad, or even dual core that well. For the fastest framerates a higher clocked dualcore is faster than a lower clocked quad. 

For AMD, you can get new AM3 dual core CPUs that drop into the newst socket (Phenom II in AM3). Get the right motherboard and you may be able to unlock cores as well (turn a dual core into a triple/waud core, turn a triple into a qaud). 

For intel..its a bit up in the air. The i7s come in LGA 1166 (dual channel RAM) and LGA 1366 (triple channel RAM). i5s are LGA 1166 _only_. Core 2 Duo/Core 2 Quad doesnt run on LGA 1166 or 1366. The LGA 1366 is faster, and will probably always have all the 'top end' Intel CPUs (at least untill Intel put out yet another new CPU socket), but they are probably a bit out of your price range.

---

### Post by jessiebrownjr on 2009-11-30
> **cascade9 said:**
> nVidia probably dont so much 'pad' results as pick and choose the games they use as examples. Some games get a nice bonus from SLI, some dont. I'd always go for single card, if your SLI setup doesnt do what you want it to, its get 2 whole new video cards. Buy a higher end single card, and if your not getting what you want, buy another. 

Nah, PariahVayne isnt making a 32/64 bit mistake. Most games dont use quad, or even dual core that well. For the fastest framerates a higher clocked dualcore is faster than a lower clocked quad. 

For AMD, you can get new AM3 dual core CPUs that drop into the newst socket (Phenom II in AM3). Get the right motherboard and you may be able to unlock cores as well (turn a dual core into a triple/waud core, turn a triple into a qaud). 

For intel..its a bit up in the air. The i7s come in LGA 1166 (dual channel RAM) and LGA 1366 (triple channel RAM). i5s are LGA 1166 _only_. Core 2 Duo/Core 2 Quad doesnt run on LGA 1166 or 1366. The LGA 1366 is faster, and will probably always have all the 'top end' Intel CPUs (at least untll Intel put out yet another new CPU socket), but they are probably a bit out of your price range.

Once again I'm making a possible leap here, but how would you unlock a core? I used to overclock (before dual cores mind you) and you could only change the FSB, and the multiplier if you had the right CPU mod or motherboard mod. I had an athlon I did a pin modification once to change the multiplier--overclocked beautifully. 

And also I have decided that I will be using an Intel CPU regardless of price. I have been using AMDs for many many years now. Seems they are laggin (so an article I read said :-)

---

### Post by cascade9 on 2009-12-01
You need a motherboard with 'advanced clock calibration' to unlock the 3rd and 4th core on Phenom II dual-cores, and the 4th core on Phemon II triple cores. 

AMD also has 'black edition' CPUs, all with unlocked multis for over and underclocking. 

AMD 'lagging'? AMD hasnt been at the top of the performance tree for a while. Intel has had that for ages. That doesnt mean that AMD is slow, and for price/preformace AMD is king. A $185 or less AMD X4 965 is comparable in speed to $300 i7 920.

Basing your CPU choice on who is fastest is like a basing a car buying decision on who won nascar, f1 or or rallying.

---

### Post by jessiebrownjr on 2009-12-01
> **cascade9 said:**
> You need a motherboard with 'advanced clock calibration' to unlock the 3rd and 4th core on Phenom II dual-cores, and the 4th core on Phemon II triple cores. 

AMD also has 'black edition' CPUs, all with unlocked multis for over and underclocking. 

AMD 'lagging'? AMD hasnt been at the top of the performance tree for a while. Intel has had that for ages. That doesnt mean that AMD is slow, and for price/preformace AMD is king. A $185 or less AMD X4 965 is comparable in speed to $300 i7 920.

Basing your CPU choice on who is fastest is like a basing a car buying decision on who won nascar, f1 or or rallying.

[http://www.overclock.net/amd-cpus/535501-amd-phenom-ii-core-unlocking-guide.html](http://www.overclock.net/amd-cpus/535501-amd-phenom-ii-core-unlocking-guide.html)

I used to overclock, I have no interest in it anymore. The problem with overclocking is that the data you get--might be corrupted because of the overclock.. this can come in a small un noticeable package or a big ol' system crash. The point of a good over clock is to get it stable..That being said

From that article I see that the extra cores are either unstable or a marketting ploy (which this wont last forever)... so that leaves me with, luck in either fashion.. I have to hope I get a good chip, and hope its stable.. 

Also from what was brought up in this post earlier, which was found to be true
the 3rd and 4th cores for gaming are a waste. 

[http://forum.winehq.org/viewtopic.php?p=35772#35772](http://forum.winehq.org/viewtopic.php?p=35772#35772)

Read what the wine dev said on the wine forums.

Your car analogy caught me off guard lol, but technically I guess you are saying the 'driver' won the race?

Thats a little too deep for this cpu discussion, they all have the same "drivers" just are diff cars now in the cpu analogy.. One actually is faster then the other, and stable at that.

---

### Post by cascade9 on 2009-12-02
> **jessiebrownjr said:**
> [http://www.overclock.net/amd-cpus/535501-amd-phenom-ii-core-unlocking-guide.html](http://www.overclock.net/amd-cpus/535501-amd-phenom-ii-core-unlocking-guide.html)
 
 I used to overclock, I have no interest in it anymore. The problem with overclocking is that the data you get--might be corrupted because of the overclock.. this can come in a small un noticeable package or a big ol' system crash. The point of a good over clock is to get it stable..That being said
 
 From that article I see that the extra cores are either unstable or a marketting ploy (which this wont last forever)... so that leaves me with, luck in either fashion.. I have to hope I get a good chip, and hope its stable.. 
 
 True about corruption, but thats why if your going to unlock cores, or do any real overclocking, its always best to test your system. 
 
 The extra cores may, or may not,be defective. It all depends on luck (but I wouldnt doubt that knowing exactly what CPU to get would help, not that many people have the option to get xxx-xxxxx-xxx instead of zzz-zzzzz-zzz CPU) 
 
 Its not a marketing ploy. From what I know, AMD is kind of unimpressed with ACC, have released a grand total of 0 white papers on the thing, and are doing thier best to get rid of it. As far as AMD are concerned, unlockign cores isnt really 'fair', they already have the black editions for the overclocking set.

> **jessiebrownjr said:**
> Also from what was brought up in this post earlier, which was found to be true the 3rd and 4th cores for gaming are a waste. 

[http://forum.winehq.org/viewtopic.php?p=35772#35772](http://forum.winehq.org/viewtopic.php?p=35772#35772)

Read what the wine dev said on the wine forums. 

The wine dev is probably right.....for some programs, in some cases. But a lot of games _do_ like having extra cores. Its mainly older games that don' need the extra cores. (Yes, I admit, these are windows benchmarks, but I haven't seen many, if any wine benchmarks) 

Older Games-
Series Sam 2- 
Athlon 64 X2 6400+ (Dual core, 3.2Ghz)-  152 FPS.
Phenom 9700 (Quad Core, 2.4Ghz)- 119 FPS.
Athlon 64 X2 4800+ (Dual core, 2.4Ghz)-  118 FPS 
Quad cores do nothing with Serious Sam 2
[http://www.tomshardware.com/charts/cpu-charts-2008-q1-2008/Serious-Sam-2,Marque_fbrandx32,390.html](http://www.tomshardware.com/charts/cpu-charts-2008-q1-2008/Serious-Sam-2,Marque_fbrandx32,390.html)

Prey- 
Athlon 64 X2 6400+ (Dual core, 3.2Ghz)-  112 FPS.
 Phenom 9700 (Quad Core, 2.4Ghz)- 104 FPS.
 Athlon 64 X2 4800+ (Dual core, 2.4Ghz)-  94 FPS 
Quad helps here, but a dual core of higher Mhz wins. 
[http://www.tomshardware.com/charts/cpu-charts-2008-q1-2008/Prey,Marque_fbrandx32,387.html](http://www.tomshardware.com/charts/cpu-charts-2008-q1-2008/Prey,Marque_fbrandx32,387.html)

Unreal Tournament 2004-
Athlon 64 X2 6400+ (Dual core, 3.2Ghz)-  84 FPS.
 Phenom 9700 (Quad Core, 2.4Ghz)- 69 FPS.
 Athlon 64 X2 4800+ (Dual core, 2.4Ghz)-  68 FPS 
Quad core doesnt do anything with UT2004. 
[http://www.tomshardware.com/charts/cpu-charts-2008-q1-2008/Unreal-Tournament-2004,Marque_fbrandx32,398.html](http://www.tomshardware.com/charts/cpu-charts-2008-q1-2008/Unreal-Tournament-2004,Marque_fbrandx32,398.html)

Newer Games- 
Left 4 Dead-
Phenom II X4 945 (Quad core, 3.0Ghz)  139 FPS
 Phenom II X2 545 (Dual core, 3.0Ghz)   123 FPS
Uses Qaud core, but not that well. 
[http://www.tomshardware.com/charts/2009-desktop-cpu-charts/Left-4-Dead-1.0.0.5,Marque_fbrandx32,1403.html](http://www.tomshardware.com/charts/2009-desktop-cpu-charts/Left-4-Dead-1.0.0.5,Marque_fbrandx32,1403.html)

GTA IV-
 Phenom II X4 945 (Quad core, 3.0Ghz)  60 FPS
 Phenom II X2 545 (Dual core, 3.0Ghz)   38 FPS
Quad core eats dual core. Totally. 
[http://www.tomshardware.com/charts/2009-desktop-cpu-charts/GTA-IV-1.0.3,Marque_fbrandx32,1402.html](http://www.tomshardware.com/charts/2009-desktop-cpu-charts/GTA-IV-1.0.3,Marque_fbrandx32,1402.html)

Fritz 11-
Phenom II X4 945 (Quad core, 3.0Ghz)  7388
  Phenom II X2 545 (Dual core, 3.0Ghz)   3739
Quad wins again. 
[http://www.tomshardware.com/charts/2009-desktop-cpu-charts/Fritz-11,Marque_fbrandx32,1406.html](http://www.tomshardware.com/charts/2009-desktop-cpu-charts/Fritz-11,Marque_fbrandx32,1406.html)

For a lot fo games already around, quad core is pointless. But for newer games, there is a point. It would make sense if as multi-cores become the only thing you can really get (in x86 anyway) that all the newer games with any real hardware requirements will run faster on more cores.  

> **jessiebrownjr said:**
> Your car analogy caught me off guard lol, but technically I guess you are saying the 'driver' won the race?

Thats a little too deep for this cpu discussion, they all have the same "drivers" just are diff cars now in the cpu analogy.. One actually is faster then the other, and stable at that.

Nah, I wasnt saying that. In a nut shell, I meant "compare apples and apples". Buying a car because they won the F1, etc, its comapring apples and oranges (with the orange being the actual car they bought) 

I really believe that comparing the top end CPU from Intel to the top end CPU from AMD is somethign that lots of people do, but doesnt have any real baring on what they are buying. Sure, if your looking at buying a $1000 CPU, its not that bad an idea, but for anyone with a budget lower than that (which is, ohh, 90%+ of us) then its mind of pointless. In the $150-250 dollar CPU market, AMD does very well.  

If it makes you feel any better, if AMD released a $1000+, 12 core, 12MB cache CPU (which they probably could, and it would prossibly eat the i7 alive on lots of benchmarks) I wouldnt be considering that either.

---

### Post by PariahVayne on 2009-12-02
x

---

### Post by cascade9 on 2009-12-02
Not misleading, just light on the exact specs. ;) 

It would be misleading if there were different GPUs for different CPUs in either of those sets of tests. As far as I know, its the same video card. Toms really should post the specs of the testing machine they use, but being toms, they don't. If anyone can find the hardware specs I'd like know, but after poking around for a while I cant see them. Theres a few threads on the toms forum asking about what the hardware specs are, but no-one offical has answered them. 

I only used toms because I could compare dual core and quad core of the same Mhz. I'm actually not really a fan of that site at all, but sometimes its usefull.

---

### Post by PariahVayne on 2009-12-02
x

---

### Post by Junkieman on 2009-12-02
Jessiebrownjr, I've had a similiar issue not being playing games from lack of hardware (Doom 3/WoW). Now I want to change that :)

nVidia sounds like a good choice, I'm thinking in the 9600GT range myself. Can anyone here recommend other nVidia models which you had good experiences with?

Thanks :)

---

### Post by handy on 2009-12-02
The times are in a process of change (as usual):

[http://ubuntuforums.org/showthread.php?t=1238129](http://ubuntuforums.org/showthread.php?t=1238129)

It all comes down to how patient you are.

Within the next year, the 3D of the open-source ATi drivers will be blitzen!

---

### Post by PariahVayne on 2009-12-02
x

---

### Post by handy on 2009-12-02
> **PariahVayne said:**
> Not if they face some of the restrictions the Intel drivers suffer.

Have a look at my first post in the link provided above?

At the end of it are a number of links, perhaps one or two of them will give you the information that you require.

In a nutshell, over a period of time the kernel will be taking over control of the graphics cards. This has already started to happen for ATi GPUs. Though the process has a ways to go yet.

In the end it will be the kernel & mesa. :)

ATi is high on the hit list to sort out, because AMD/ATi have been doing such a bad job under Linux.  On their behalf, is the fact that AMD have been providing technical info' where they can to the open-source people.  

Though this has been complicated due to the GNU licensing legal situation.

---

### Post by jessiebrownjr on 2009-12-02
Although that is good news for some time from now, my "rig" was going to be build in january maybe.. hehe..

---

### Post by handy on 2009-12-02
> **jessiebrownjr said:**
> Although that is good news for some time from now, my "rig" was going to be build in january maybe.. hehe..

Yeh, it is a bit tricky just at the moment to choose whether to buy nVidia or ATi.  Up until a few months or so ago, there was no questions about it, nVidia all the way (I own both nVidia & ATi GPUs).  

Now, I personally wouldn't buy anything other than ATi.  The 2D is already the best you can get, via the open-source support, it just depends on which ATi GPU re. the timing of when the 3D will also be the best you can get. 

Most people don't have the patience to wait up to a year.  I'm older than most who use the forum, so patience is not the problem it used to be... ;)

That said, I'm currently using catalyst 9.10 on Arch, & the 3D is fine for the games that I currently play.

---

### Post by jessiebrownjr on 2009-12-03
> **handy said:**
> Yeh, it is a bit tricky just at the moment to choose whether to buy nVidia or ATi.  Up until a few months or so ago, there was no questions about it, nVidia all the way (I own both nVidia & ATi GPUs).  

Now, I personally wouldn't buy anything other than ATi.  The 2D is already the best you can get, via the open-source support, it just depends on which ATi GPU re. the timing of when the 3D will also be the best you can get. 

Most people don't have the patience to wait up to a year.  I'm older than most who use the forum, so patience is not the problem it used to be... ;)

That said, I'm currently using catalyst 9.10 on Arch, & the 3D is fine for the games that I currently play.

I feel you on the patience aspect hehe, but its more of... my pc is already 4-5 years old.. Athlon 64 xp 2.2ghz 2g ram, i upgraded the gpu to a 512 geforce.. hehe... It runs doom 3 OK in both linux and Windows... Pretty decently I might add, but nothing newer.. I tried assassin's creed and *poof* lag farm. I can't agree with you on the nivdia/ati because I have had adverse experience with them, and I don't get burned twice.. They might be getting better, but they lost my business a long time ago.. 

My only current question which ill look at more towards what CPU im getting... Half the reviews I've read about dual vs quad are 2 years old.. thats a problem...

I shall probably end up getting the best  quad I can for the fact of, I won't be upgraded for years, or playing every single game that comes out recently, and I think the longevity will pay off..

---

### Post by cascade9 on 2009-12-03
Of coruse Assasins Creed lags. You way under minimum spec- 

Processor: Dual core processor 2.6 GHz Intel Pentium D or AMD Athlon 64 X2 3800+
RAM: 2 GB
Video Card: 256 MB DirectX 10.0-compliant video card or DirectX 9.0-compliant card with Shader Model 3.0 or higher
Sound Card: DirectX 9.0 or 10.0 compliant sound card
HDD Space: 12GB
DirectX Version: DirectX 10.0

You CPU would be a +3700, single core, at best. Its more likely a +3200. 

As for dual vs quad- you want to play newer games? Get the quad. Old games? dual. 

In the end, though, you will end up hitting the same issue you have now. I've seen lot of people over the years say 'this gaming rig will last me for years'. The most they ever get, while still being able to play all  new games, is 3-4 years.

---

### Post by ZoiaGuyver on 2009-12-03
ATI like has been said here are coming along in quite large leaps, but they arn't really going to put a dent into Nvidia imo, NV from the start has basically had linux drivers (even though they are not open-source). NV has always tried to keep people happy with the linux drivers offering performance on-par or slightly above the Windows drivers.

I used ATI for a long time, i still use ATI on some machine's but it depends on the situation. At the moment with how Wine is progressing i have nearly all my "Steam Platform" games working... Only one's that dont work are really obvious Batman:Arkham Asylum refuses to play due to the integration of Windows Live Games. Whether this will improve with time is yet to be seen, although Wine are working on better support for Fallout 3 and that uses the same gimmick Live Games. Imo you can with a little patience get most games to work well under linux, anything based around the Quake/Doom/Unreal Engines are normally a breeze as they all make heavy use of OpenGL. The prob one's are Frostbite (DX based Engine) and the Crysis engine..

Going onto a CPU though you should def get a quad core imho, the performance of the i5's and i7 intel's is really amazing. I have an older Core2Quad Q6600 which does me for the games i play (mainly Source Engine and WoW :P).

If you arn't restricted budget wise the i7 has been rated as the best cpu for all out power.

The i5's are no slugs though and although they loose the benefit of HT they put up really good marks.

Both are the new sockets though (afaik im a little behind at the mo i've spent a long time out of the market).

---

### Post by jessiebrownjr on 2009-12-03
Yeah I'm going to blow most of a budget on a great mobo/cpu/ 2x gpu for sli and ram. Going to scrap my old HDD and DVDRW and accessories.. Obviously have to get a new case/psu. The 1k$ budget I might have or have not said isn't set in stone. I might have upwards of 1500$, might not get anything! lol.

Is there any new CPUs(new designs not speeds) that are due to be released by, lets say feb 1st? Mainly asking about the best CPUs not budget CPUs.

---

### Post by handy on 2009-12-03
If you stay a step or so behind the cutting edge, you will save a lot of money on hardware.

---

### Post by jessiebrownjr on 2009-12-03
> **handy said:**
> If you stay a step or so behind the cutting edge, you will save a lot of money on hardware.

best mini-piece of advice you can give! This is what I intend to do... The few extra hertz here and there only add up to some frame rates I won't be able to tell the difference in past a certain point. this gaming rig will be not to impress friends with framerates, but play the newest games without lagging alot. I'm honestly used to sub-par frame rates.. And as sad as it is like Doom 3 is the "nicest" game i've played in high settings without lagging.. It kinda got me addicted.. ;-p

---

### Post by cascade9 on 2009-12-03
> **jessiebrownjr said:**
> Yeah I'm going to blow most of a budget on a great mobo/cpu/ 2x gpu for sli and ram. Going to scrap my old HDD and DVDRW and accessories.. Obviously have to get a new case/psu. The 1k$ budget I might have or have not said isn't set in stone. I might have upwards of 1500$, might not get anything! lol.

Is there any new CPUs(new designs not speeds) that are due to be released by, lets say feb 1st? Mainly asking about the best CPUs not budget CPUs.

Yeah, theres a new faster AMD Phenom II 975, not that your interested in that LOL. There is also the new Intel core i9. Fat chance getting that running for $1k,or even $1.5K, the CPU alone is likely to be over $900. 

As for getting a 'top of the line' system for $1k....not possible, really. Even the 'middle of the line' i7 (i7 950) is going for over $550. Then you'll need a LGA 1366 motherobard, $150 for really cheap one (more like $200+ for the more decent models), triple channel DDR3, $150 odd for ther cheapest (and more like $200 for the better stuff). Thats $850 on just motherboard, ram and CPU. Not 'great' versions of the mobo/ram, that would take you to $1k. Even with the cheaper stuff, add a single GTX 260 (very middle of the road for gaming) and its over $1k. Without Hdd, Optical drive, power supply, case. Or SLI.  
 
If you dropped to a i7 920, it might be possible, but your still going to end up with low end cards in SLI. 

> **handy said:**
> If you stay a step or so behind the cutting edge, you will save a lot of money on hardware.

Yes, true. Just one of the reason I avoid the bleeding edge, its too expensive. 

When your looking at more for a CPU than you are for a whole system of decent specs your just blowing money. I could build a nice box with lots of upgrade potential for less than the cost of the i7 950 ($550)..

---

### Post by jessiebrownjr on 2009-12-05
> **cascade9 said:**
> Yeah, theres a new faster AMD Phenom II 975, not that your interested in that LOL. There is also the new Intel core i9. Fat chance getting that running for $1k,or even $1.5K, the CPU alone is likely to be over $900. 

As for getting a 'top of the line' system for $1k....not possible, really. Even the 'middle of the line' i7 (i7 950) is going for over $550. Then you'll need a LGA 1366 motherobard, $150 for really cheap one (more like $200+ for the more decent models), triple channel DDR3, $150 odd for ther cheapest (and more like $200 for the better stuff). Thats $850 on just motherboard, ram and CPU. Not 'great' versions of the mobo/ram, that would take you to $1k. Even with the cheaper stuff, add a single GTX 260 (very middle of the road for gaming) and its over $1k. Without Hdd, Optical drive, power supply, case. Or SLI.  
 
If you dropped to a i7 920, it might be possible, but your still going to end up with low end cards in SLI. 



Yes, true. Just one of the reason I avoid the bleeding edge, its too expensive. 

When your looking at more for a CPU than you are for a whole system of decent specs your just blowing money. I could build a nice box with lots of upgrade potential for less than the cost of the i7 950 ($550)..


yeah i'm going to try to up my budget to 1500$. I was counting on financial aid refunds to feed my rig.. Going to get a 2nd job between semesters and up the ante :-). 

Ok now. Let me pose this quesiton, what is more important (if you had to choose)?
GPU or CPU? I want the games to look pretty and not lag obviously, so which part helps this along the most.. if that makes any sense. I know the cards make the anti aliasing and the cpu does the physics etc, but help me out here.

---

### Post by cascade9 on 2009-12-05
I'm pretty sure that later nVidia GPUS do physics on the GPU, its not a CPU task. That may very well depend on the game though. 

As for GPU or CPU- the glib answer is 'I want a nice happy medium. Not to much CPU, not to much GPU'. 

If I had to pick between a crappy CPU or crappy GPU, I'd take the nasty CPU.....for gaming only. For my real world tasks, bad GPU thanks. LOL 

Better to have a decent CPU and a single GPU than to spend a forture on SLI and get bad results cause your CPU bound and the GPUs arent getting enough information from the CPU.

---

### Post by ZoiaGuyver on 2009-12-05
I agree with Cascade tbh. The "standard" answer is to try and hit a middle ground with CPU/GPU that neither are bottlenecked.

Best thing to do is check site's for good cpu's with decent benchmarks (benchmarks dont really mean a lot but they can give you some pointers on hitting a balance). Look at the test rig's and how they set them up for the test's, and try to get an idea from that.

Obviously most benchmarks you will see will be "Windows" bench's. Although they arn't really a reflection on linux they will allow you to get a very "rough" idea as to a way of not getting bottlenecked.

Apart from that they should also give you an idea of what you can get for the budget.

---

### Post by jessiebrownjr on 2009-12-05
> **ZoiaGuyver said:**
> I agree with Cascade tbh. The "standard" answer is to try and hit a middle ground with CPU/GPU that neither are bottlenecked.

Best thing to do is check site's for good cpu's with decent benchmarks (benchmarks dont really mean a lot but they can give you some pointers on hitting a balance). Look at the test rig's and how they set them up for the test's, and try to get an idea from that.

Obviously most benchmarks you will see will be "Windows" bench's. Although they arn't really a reflection on linux they will allow you to get a very "rough" idea as to a way of not getting bottlenecked.

Apart from that they should also give you an idea of what you can get for the budget.

I just read an article about how much memory is effective on video cards etc.. Tom's hardware, was very informative. The point of this article was to see if having *more then enough* ram then a game required positively affected FPS, which it did not. It wasn't until the textures used up the ram on the cards the perfermance dropped.. On that note, he also spoke about some games engines showing different things happening. Some of them used heavy CPU for the game, some heavy GPU. I think he said Valve's engines for instance aren't as reliant on GPUs as much as other games. I read another article that crysis had the physics engine using the CPU etc (i think).. Honestly all this is just blowing my mind cause its not leading me to any decision but SPEND MORE SPEND MORE..

---

### Post by ZoiaGuyver on 2009-12-05
Well tbh thats the catch, Tom's Hardware is great it's prob one of the best review site's around (although it does at time's seem to be a little in AMD/ATI's pocket). But it wont make your mind up :D

He's also right about the engine's Source Engine is more reliant on CPU than GPU performance.. until you start maxing out setting's. It's the same with Quake4 and the "Ultra" mode. Crysis using the CPU as the Physics engine when PhysX Ageia isnt available was always a problem.

Easiest thing to suggest is get the best performing CPU you can for your budget, the best GPU you can (with the largest amount of onboard memory you can).

The memory of the actual systems has very little "performance" rated to it. But some game's use larger amounts of memory to pre-fetch stuff so you don't get loading time's and the like's. It also help's to stop game's "thrashing" hard drives :p

---

### Post by cascade9 on 2009-12-06
> **ZoiaGuyver said:**
> Well tbh thats the catch, Tom's Hardware is great it's prob one of the best review site's around (although it does at time's seem to be a little in AMD/ATI's pocket). But it wont make your mind up :D 

I actually dont like toms that much, its always got issues that some other sites avoid. About all its good for its the comparisons, but even they have issues. Try to find the system specs on the 'chart' systems. LOL 

Funny, enough, if I hear that there is a bias there its normally the other way around. That could be old news, though, as a lot of that impression comes from stuff from a while ago. Like the 'take the heatsink off' tests they did that show up every now and again (I've recently seen that posted here) 

> **ZoiaGuyver said:**
> He's also right about the engine's Source Engine is more reliant on CPU than GPU performance.. until you start maxing out setting's. It's the same with Quake4 and the "Ultra" mode. Crysis using the CPU as the Physics engine when PhysX Ageia isnt available was always a problem. 

True, but you can poke at benchmarks till the cows come home. 
 
> **ZoiaGuyver said:**
> Easiest thing to suggest is get the best performing CPU you can for your budget, the best GPU you can (with the largest amount of onboard memory you can).

I'm not so sure about that...but see below ;) 

> **jessiebrownjr said:**
> Honestly all this is just blowing my mind cause its not leading me to any decision but SPEND MORE SPEND MORE..

Really, really bad idea. Once you go past some fuzzy 'sweet spot' you pay a ton more for not that much better performance. As to where that spot is, thats debatable but think about this- 

If you went out in 2006 or so and bought a top of the line 8800GTX (768MB) you'll get lovely framerates. Wow, you think, this will last me for years! 

[http://www.tomshardware.co.uk/charts/desktop-vga-charts-2006/Oblivion-The-Elder-Scrolls-4,605.html](http://www.tomshardware.co.uk/charts/desktop-vga-charts-2006/Oblivion-The-Elder-Scrolls-4,605.html)

Fast forward to 2009, and wow, the poor old 8800 GTX isnt doing so well- 

[http://www.tomshardware.co.uk/charts/gaming-graphics-cards-charts-2009-high-quality/Fallout-3,1509.html](http://www.tomshardware.co.uk/charts/gaming-graphics-cards-charts-2009-high-quality/Fallout-3,1509.html)

Its still getting a respectable framerate, but its not that amazing. Now, if you spent x2 the amount of money and got x2 8800GTXs in SLI, your getting...er...not that much more. If you have of put the extra money in your pocket, and waited till 2009 to get a new card, you could get a single GTX 275 and get better framertaes! 

The more you spend, the less perfromance increase you will get. Once you go past some point (and its debatable where that point is but its before the $1.5K US mark) its better to save the 'extra' money and buy something else later.

---

### Post by jessiebrownjr on 2009-12-06
The memory on the cards in SLI..are they additive or paralell?  If 2x1=2, thats great... if its the other way around, ill be sad.  To what you were saying about the cutoff.. Im thinking about getting the lowest end.. of the newest architecture intel cpu I can buy, if that makes sense.. wont worry so much about the FPS past what  I see, as long as I can run it in super high anti aliasing at widescreen resolution :-)

---

### Post by cascade9 on 2009-12-08
The memory adds. I really dont get this obsession with SLI...even the serious gamers I know with tons of cash avoid it. 

You're probably going to have issues with drivers under linux as well.

---

### Post by jessiebrownjr on 2009-12-08
> **cascade9 said:**
> The memory adds. I really dont get this obsession with SLI...even the serious gamers I know with tons of cash avoid it. 

You're probably going to have issues with drivers under linux as well.

im pretty confident that my main concern isn't solely linux compatibility. it is a concern, but about as far as i can go with that seems to be just 'pick nvidia'...

Im sure whatever I get will work dandy with windows 7 and direct x 11, and if I can also play it from Ubuntu, thats fine and dandy

Where do you get this info about serious gamers you know with tons of cash...?It kinda sounds like an opinion of yours :-)

---

### Post by cascade9 on 2009-12-13
> **jessiebrownjr said:**
> Where do you get this info about serious gamers you know with tons of cash...?It kinda sounds like an opinion of yours :-)

From the gamers I know with tons of cash? LOL 

One guy I know upgrades about every 18 months. Last upgrade- i7 960, 6GB, 1TB 7200, GTX 285. Before that he had a core2qaud (cant recall the model), 4GB, 750GB 7200, GTX 9800. 

Its not just my opinion, but I doubt you will believe that LOL. Try going to one of the big hardware/overclocker forums and asking them ;)

---

