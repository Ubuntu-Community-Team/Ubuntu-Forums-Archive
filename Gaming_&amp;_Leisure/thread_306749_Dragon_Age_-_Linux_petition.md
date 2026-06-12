---
title: "Dragon Age - Linux petition"
date: 2006-11-25
forum: Gaming &amp; Leisure
---

### Post by B0rsuk on 2006-11-25
Dragon Age is a new game being developed by Bioware - creators of Baldur's Gate, Baldur's Gate II, Neverwinter Nights 1, Kotor, and some others. Let's vote for a Linux port, there's a thread on Bioware's forum:

[http://forums.bioware.com/viewtopic.html?topic=494004&forum=84](http://forums.bioware.com/viewtopic.html?topic=494004&forum=84)

Why should we try ?
- **because this is a very good developer**
- **based in fresh, realistic fantasy new world**, inspired by stuff like books of George RR Martin (Game of Thrones)
- because nwn1 was (is) wildly popular linux rpg game; nwn2 linux petition has around 1600 posts on atari forums.
- **because unlike atari** (publisher of Neverwinter Nights2), or obsidian(developer of nwn2) **Bioware team does post on forum quite often. They obviously read it.**
- because it is confirmed that Dragon Age will be PC only. This means it will not be available for consoles. This means **it won't come to xbox**. No xbox game is known to run on Linux.
- Dragon Age is coded in **C/C++, no mention of .NET or C#**. This is good for porting and for Wine.

Summary: there's actually quite good chance of Linux port. We still don't know if the game will use OpenGL, and what the publisher will be. Add your voice to petition thread !

5 early screenshots:
[http://rndm.co.uk/dragonage/screenshots/sp_index.php?dir=./early_screenshots](http://rndm.co.uk/dragonage/screenshots/sp_index.php?dir=./early_screenshots)

---

### Post by Antonlacon on 2006-11-25
> because it is confirmed that Dragon Age will be PC only. This means it will not be available for consoles. This means it won't come to xbox. No xbox game is known to run on Linux.

Doom3 + Quake.

---

### Post by B0rsuk on 2006-11-25
> **Antonlacon said:**
> Doom3 + Quake.

Xbox versions were announced and ported later. Originally there was no mention of console versions, as far as I remember.

Prey was said to come to xbox and PC even before it was released. Result: no linux version.

---

### Post by hobieone on 2006-11-25
if these games are going to be made for the playstation 3 then in my book there is no excuse what so ever for a native linux client due to the playstion 3 game are all done in open gl and the fact the playstation 3 is ussing a linux os

---

### Post by B0rsuk on 2006-11-25
Would you put a chastity belt on just because it has 'SONY' written on it ? SONY the Rootkit Company ?

And no, Dragon Age will be PC only. Thank gods.

---

### Post by xopher on 2006-11-25
This game looks really interesting, and as you pointed out - it lacks all the things that would automatically rule out a linux port.

I'll keep my fingers crossed! :)

---

### Post by xenoalien on 2006-11-25
Are there any screenshots of Dark Age? Post a link to them if so.

---

### Post by Antonlacon on 2006-11-25
[http://www.1up.com/do/slideshow?pager.offset=0&mt=0&cId=2019479&mId=3074454](http://www.1up.com/do/slideshow?pager.offset=0&mt=0&cId=2019479&mId=3074454)

Didn't find any on the official page, and the rest involve a subscription to Games for Windows.

---

### Post by airtonix on 2006-11-26
Guys i wouldnt even bother.......seriously

SOmeone who makes a website that requries javascript just to get the damn background images t load!!!

I mean COME ON...they obvioulsy live in a world of gates and windows.

---

### Post by B0rsuk on 2006-11-26
1up website is NOT official website, so it's not their fault it uses javascript. I already gave you a link to screenshots in my first post.
By the way: 1up may be technically crappy and bloated as it is, but it tends to write disturbingly good (honest) game reviews. They gave Nwn2 score of 6/10, first sentece of the review saying it's two patches away from being playable. And for some good laugh, read their Dark Messiah of Might and Magic review.

Actually, I learned the game uses .NET for some tools, but it could be worse, it could be C#.

As for Bioware, at least they respond to the topic. Multiple times.

---

### Post by Kaidelong on 2009-11-07
.NET is irrelevant to the subject of porting games; it does not provide any graphics or multimedia functionality. You can write a game for Linux using C# pretty much the same way you would write it using C++, probably using SDL.NET. There is actually a slight improvement here over C++: .NET and Java have a single "compiler" regardless of the original language it was written in; the original compiler transforms the source code into byte code, which is then compiled for the platform by the run time. The language-specific compiler can then be distributed as bytecode, with no need to distribute a port of the compiler itself.

What would be more relevant is if they were using DirectX - as most game developers do - which is propietary and closed, and thus nothing like Mono can exist for DirectX except through reverse engineering. However, the community have reverse engineered - the legal sort of reverse engineering where you replicate something via a description of how it works, not by looking at the thing itself - a great deal of windows and DirectX, and this is where Wine comes in. 

Instead of asking the developers to make a port, a better thing to do would be to ask them to test it on Wine and tell the Wine developers what Wine is breaking in their game. Developing a game for Wine will let it run anywhere Wine runs, and on windows itself. This way, the developers don't actually have to port the game, they just need to abstain from making Wine crash and burn. This is the approach taken by CCP games for EVE Online after the disaster that was their (actually Transgaming's) Linux port of the game: people ended up running the windows version in Wine even though there was a Linux version available! Wine is one of the better things to come out of the open source world and it should not be underestimated as a "porting" tool. Also, in the course of doing so, they may even be able to improve Wine for everyone that follows them, perhaps one day Wine will be so sophisticated no special effort will be needed to "port" windows games to Linux.

In the meantime, most game developers will continue to regard Linux as a small and unattractive target market, mostly run by servers and not desktop machines and prohibiting the use of their favorite developer tools and techniques. That doesn't mean you have to stop using it for your day to day activities just because you're big on gaming. You could run windows virtualized or with a dual boot system to play games (a "Wintendo" partition). You can check out how to do this in the Gentoo wiki among many other places.

Sorry if the post is too long, but I had a lot to cover, hope some of it was helpful. ;)

PS: Dragon Age: Origins is coming out for the XBoX 360 and Playstation 3. I imagine the reason why you find Wine struggles with XBoX 360 games probably has to do with developers using the XNA toolkit on both Windows and XBoX 360, perhaps XNA breaks Wine in a way older windows games doesn't? Unfortunately, this makes sense for the developers as Windows PCs and XBoX 360s are a huge market and being able to develop one game for both easily makes up for the loss of portability, so you'll just have to wait for Wine to catch up on that one.

---

### Post by Melcar on 2009-11-07
Developing for WINE is not the answer.  In fact, that will only make the problem worse.  Really, the only solutions are native games and/or ports.  Well, actually, it depends on what you believe is best for Linux as a gaming platform; want it to remain a second class platform for games (developers targeting WINE), or a viable OS for game development with a healthy community of developers supporting it (develop native games and come out with ports)?

---

### Post by Kaidelong on 2009-11-08
I don't think so, actually, I think the best way to defeat window's lock in would be to replicate the windows API to the point that people will choose to write games for the large, but functional portable subset of it (IE, Wine and perhaps later ReactOS could embrace, extend, and extinguish windows).

If Wine improves and games are developed for Wine and not Windows, then you get portability without telling game companies to adopt a whole new tradition of writing portable games or write games which cannot readily be ported back to windows. Imagine what things would be like if people could download linux FOR FREE and it supported virtually all the same software windows does.

Also developing for Wine does not mean that people can't make good developer tools for it, as Wine improves it could even be shipped with Linux distributions in much the same manner Windows NT ships with a UNIX interoperability layer for running UNIX applications.

---

### Post by Melcar on 2009-11-08
If you develop for WINE you develop for Windows.  You are only hurting Linux more.  Why would game developers bother making Linux clients for their games when they can just make a Windows version and make it work on WINE?  You're not fixing the problem, you're just putting a band-aid over it.

---

### Post by 569874123 on 2009-11-08
> **B0rsuk said:**
> Would you put a chastity belt on just because it has 'SONY' written on it ? SONY the Rootkit Company ?

And no, Dragon Age will be PC only. Thank gods.

That is kind of like insinuating linux is very inaccessible or command-line only cause some operating systems are(ubuntu is not, neither is mint etc).
Sony BGM is the one responsible for that root-kit scandal(it has nothing to do with games, but music) and only Windows operating systems were getting screwed by it,so linux people would only have 1 more reason to tell people to come on to linux...
SCE is responsible for being supportive of open-source,linux and creating the ps3...

---

### Post by meborc on 2009-11-08
the games runs fine under wine... as in RIGHT NOW :) petition if you like, i will continue my game

---

### Post by Kaidelong on 2009-11-09
> **Melcar said:**
> If you develop for WINE you develop for Windows.  You are only hurting Linux more.  Why would game developers bother making Linux clients for their games when they can just make a Windows version and make it work on WINE?  You're not fixing the problem, you're just putting a band-aid over it.

I think this is a very interesting discussion that has been bought up, I do disagree on the idea that developing for Wine hurts Linux though, let me enumerate my arguments against this.

1) If you develop for Wine, you develop for everything that can run Wine. Wine is an API layer for Linux that replicates the functionality of the Windows API. It's not an emulator: stuff running on Wine runs natively, using Wine's Windows API to manipulate the system.

2) The fact that developers have to port their games in the first place is the problem. Making it so that porting those games is unnecessary fixes the problem. Wine is already doing a great job at this. Porting a game to Linux without Wine is more expensive than porting it to Linux with Wine. If you tell them to write the Linux version first, even if the resulting code is more portable, they end up with the more daunting problem of writing code for a platform that a very small part of their market uses and then having to port it again to Windows where most of their market is.

3) Microsoft prides themselves on making major changes rarely and preserving backwards compatibility. This trait has helped them hold onto their developers. Developers who desire this "future-proofing" aspect of Windows development will not be intimidated by Wine since Wine chases Windows.

4) Wine is open source, and can be ported independently to other platforms.

5) Wine is LGPL licensed. The software industry can use Wine to provide Linux interoperability without having to worry about "viral" infection forcing them to divulge source code.

I think Wine just makes sense as a development target. EVE Online's Windows version IS its Linux version as CCP is kind enough to test their game on Wine. Everyone (except Microsoft; Windows Genuine Advantage is in part an effort to curb the threat from Wine, not just the threat from piracy) benefits from developers who do that; the developers themselves, Wine, and Linux. 

Thus, I think it's a great idea to tell developers to test their products on Wine (and hopefully, contribute to Wine).

---

### Post by meborc on 2009-11-09
i think it will be easier to push game developers to test their games on wine then to ask them to port them to linux...

as many new games CAN be played with wine, i think the development effort needed is much smaller than porting a game. this means less money spent and easier to get a positive response from the developers

like i said, i run dragon age: origins on wine and it WORKS... ok, i have to use low graphics and i don't see the game intro, but so what? i usually esc+esc to menu anyways :)

i love the game, it runs on wine as fast as on my vista partition

---

### Post by Sages on 2009-11-09
yeah a native/port of the game would be great! but for those who simply can not wait the game will work under current wine, sound an all.

I have it working on my computer which i must say isnt good compared to most these days but it works the game great.(if a bit choppy in places)
It plays the same in maxed out settings as i does in low.

ubuntu 9.10
CPU Pentium 4 3ghz
1gig of ram
xfx fatality geforce 7600gt

just to give a bit of heads up on what can play this game..

---

### Post by Melcar on 2009-11-09
For those of you that got it running, any special steps to get it to install?  The installer always craps out after it unpacks all the files.

---

### Post by meborc on 2009-11-09
> **Melcar said:**
> For those of you that got it running, any special steps to get it to install?  The installer always craps out after it unpacks all the files.

are you installing from the official dvd or ...? because my official dvd installed fine

also be sure to use the latest wine (1.1.32 at the moment) from ppa

if you go to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=18283&iTestingId=46286](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18283&iTestingId=46286) scroll down and you see all the comments of people having problems and how to solve them

all i can say is, official dvd version working fine on my box with no-cd patch... had to add some dll's, but it was no big deal

---

### Post by Sages on 2009-11-09
my copy installed faily well. i did get a error pop up at the very end of the installation but i clicked to play any way and its worked fine. 

The only problem i have really seen now is that for some reason my pc wont play it on low settings. (which isnt a problem but few more fps are always nice) It just gives of a lot of black lines on the land.

---

### Post by 569874123 on 2009-11-09
Bioware and Microsoft are "friends" so i wouldn't expect it to be ported.

---

### Post by Rodney9 on 2010-04-14
> **meborc said:**
> the games runs fine under wine... as in RIGHT NOW :) petition if you like, i will continue my game

I have tried to install Dragon Age on Ubuntu 9.10 with Wine-1.1.31, it go all the way to ' PhysX 'installing and then it just seems to stop.

I have waited 2 hours and nothing happens, I see it in conky using cpu but as I say it does nothing for hours.

How did you get it to install ?

---

