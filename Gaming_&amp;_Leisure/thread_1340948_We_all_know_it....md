---
title: "We all know it..."
date: 2009-11-29
forum: Gaming &amp; Leisure
---

### Post by HellionDarkLord on 2009-11-29
My thoughts about gaming are as follows.

1.  Everybody wants to play their favorite game on Ubuntu. Everybody complains when they can't figure out how to play WOW or battlefield 2 or any of many other titles that won't run on Ubuntu.

2.  Nobody cares enough to go out of their way to make it happen.  It could happen if people really cared enough.

3. If you don't care enough to do something about it stop complaining!!

4.  I wish to start a group dedicated to Ubuntu gaming because I care enough that I want to start doing something about not being able to play decent games out of the box just as well as windows.  

The problem is that there are not enough people out there who understand how to port a game to Linux.

My only problem is that I don't know where to start learning how to port games to Linux otherwise I'd already have done it.

Any help would be appreciated.

---

### Post by Arthur_D on 2009-11-29
Porting means to rewrite/add some stuff in the source code to get a game working on another platform. So, you would need the original source code, and for commercial games, it's practically impossible to get it in a legal way if the game publisher doesn't want to cooperate.
Some games are written from scratch as clones, and if people own the original game they can use the art from that in the game. That would be the best AFAIK.
Or, maybe the easiest would be to get involved in the Wine and PlayOnLinux projects.

---

### Post by Raffles10 on 2009-11-29
> **Arthur_D said:**
> Porting means to rewrite/add some stuff in the source code to get a game working on another platform. So, you would need the original source code, and for commercial games, it's practically impossible to get it in a legal way if the game publisher doesn't want to cooperate.
Some games are written from scratch as clones, and if people own the original game they can use the art from that in the game. That would be the best AFAIK.
Or, maybe the easiest would be to get involved in the Wine and PlayOnLinux projects.

Exactly, without the source code you're stumped even then you'd need to know how to rewrite it, a highly skilled process. More useful may be lobbying game companies like Bioware who released a linux version of the excellent Neverwinter Nights but so far haven't done so with NWN2. This needs to be done in large numbers or they just won't bother.

---

### Post by w4rr3n on 2009-11-29
After banging my head against WoW and Wine one night, I found out the only thing I really had to do was run wow in wine with opengl and everything worked flawlessly. You're right that if you put forth the effort it's possible. But it took several hours of forum digging and variable substitution to find exactly what was wrong (and after it being such a simple solution I felt pretty dumb). Trying to get the right information to different people with unique system set-ups is an uphill battle that will inevitably leave some people without a solution (or too frustrated to continue trying).

I understand your desire and I empathize with your frustration (believe me), but I think Raffles is correct. Lobbying the bigger game companies is one of the few viable options for bringing bigger names to the Linux platform. Presently there is not (or does not seem to be) any market sizeable enough to offer a turn around on company capital investment in porting their games to Linux. You would need a very large group of people all contacting a company or group of companies. That said, I'm willing to help you organize something if you're interested.

Feel free to PM or email me.

---

### Post by Arthur_D on 2009-11-29
> **w4rr3n said:**
> After banging my head against WoW and Wine one night, I found out the only thing I really had to do was run wow in wine with opengl and everything worked flawlessly. You're right that if you put forth the effort it's possible. But it took several hours of forum digging and variable substitution to find exactly what was wrong (and after it being such a simple solution I felt pretty dumb). Trying to get the right information to different people with unique system set-ups is an uphill battle that will inevitably leave some people without a solution (or too frustrated to continue trying).

You should take a look at PlayOnLinux. It's a program that lets you install games using Wine, but with specific configurations and/or Wine versions for each game. Somewhat bloated you might say, but it works quite well for me. Two games I couldn't get installed with "vanilla" Wine installed just fine under PoL. :D

---

### Post by hikaricore on 2009-11-30
Wow works smashingly on Linux as long as you have a reasonable video card.
Porting is impossible unless you want to reverse engineer the entire client.
Blizzard does not care about Linux players and never will.

As for porting this would be much easier if developers coded cross platform to begin with.

---

### Post by castlefox on 2009-11-30
After read this article,

[http://arstechnica.com/gaming/news/2009/11/how-pc-gamers-can-be-heard-hint-not-by-threats-of-piracy.ars](http://arstechnica.com/gaming/news/2009/11/how-pc-gamers-can-be-heard-hint-not-by-threats-of-piracy.ars)

I can understand how saying why you wont buy a game wouldnt help your cause.  

I wish more people would go on whatever games' forum say that want a linux client for the game and they will be more than happy to buy the game. 

I think the best way to contribute to this effort is to be more active in the community by saying whatever game needs a linux client.  Wine could also use more help.

---

### Post by oldrocker99 on 2009-11-30
At least we do have Neverwinter Nights, with a first-rate Linux client. I liked the mechanics of the second game (which BioWare didn't write), but I did not like its looks, far preferring the slightly brighter hues of the original. I've been playing for 7 years now, first under XP, and now under Ubuntu.

:guitar:

---

### Post by HellionDarkLord on 2009-12-12
sorry so long with no reply.  I have had computer issues.  I have been trying without success to install the cuda driver for my n260gtx ocv4.  I finally did it and the answer was so stinking simple I can't believe it.  All I had to do was fresh install without installing the 180 driver and then DL the 190.18 driver and run it.  Simple as that.  I tried installing over the 180 driver three times cause I thought it was supposed to be installed first.  (can't remember where that idea came from.)

Anyhow,  I have found a game that is quite an awesome game but lost it's maintainers.  It's called brutal chess.  It is still alpha, but works nicely enough and looks pretty.  The only thing is that it's not finished.

I have tried compiling from source, but that failed. I posted the details here
[http://ubuntuforums.org/showthread.php?p=8487532#post8487532]("http://ubuntuforums.org/showthread.php?p=8487532#post8487532")


So, I'm working on something at least....  I don't know how to help wine or pol.

---

### Post by Irritant on 2009-12-12
If Linux were more consistent across various distros in regards to libraries, game companies would be more apt to port.  Currently, alot probably feel it's more headache to support the platform than it's worth.

---

### Post by hikaricore on 2009-12-12
> **Irritant said:**
> If Linux were more consistent across various distros in regards to libraries, game companies would be more apt to port.  Currently, alot probably feel it's more headache to support the platform than it's worth.

This is a tired old excuse.
Libraries are simple, check the system for a required version, if it doesn't exist fallback on a copy in the game folder.  SOLVED.
There are only a couple major package management systems out there, I'm sure companies like Canonical and RedHat would be thrilled to offer advise and assistance to prominent game developers who would bring tons of potential users to Linux by finally getting over the excuses.
Honestly this isn't all that complicated.  OpenGL is as good if not better than Direct3D and is supported by both major (nvidia/ati) gpu manufacturers.
What else is there that needs to be said?

If EA or Blizzard would get off their damn ***** and start providing ports of _current_ games others would follow suit.
Hell World of Warcraft for example already has a fully functional OpenGL rendering mode, all that would need be done is port the basic client and launcher tool.

---

### Post by murderslastcrow on 2009-12-13
I think more game development companies shoes program cross-platform to begin with, also. I mean, you'd almost think they're undereducated, not being able to program in a language that's easy to port to multiple systems.

However, I'm sure if as many developers who contributed to one of the top distros just quit what they were doing and helped to test and develop Wine, we would soon be leaps and bounds ahead of where we are now (which is already very far, mind you). I don't suggest they do this, just talking about numbers/time.

I think we may simply have to organize large groups of people to petition companies for Linux clients, as well as spend more time testing Windows software in Wine. Face it- if Wine were perfect, it wouldn't matter, and the only thing keeping people from using/developing for Linux would be because they hadn't heard of it yet.

But I'm getting ahead of myself. When something's so wonderful and nearly perfect, you long for the perfect moment.

---

### Post by sakuramboo on 2009-12-13
[http://twit.tv/floss8](http://twit.tv/floss8)

That is an interview with Ryan Gordon, the most well known name in the industry of application porting. He explains, very basically, how he does game porting.

When you got some time, hop onto irc.freenode.org and head into the #ubuntu-gaming channel. It was originally a project for building interest in FOSS game development, but DPic (the creator of the project) seems to have given up. A few of us still hang out in there.

I'm actually very into the Linux gaming scene. My list of commercial and FOSS games grows almost monthly. But, I focus solely with native games. I don't waste my time with WINE or any other layering applications like that (with one exception).

---

### Post by HellionDarkLord on 2009-12-13
So, in order to get game companies to port games it has to be profitable for them.

It also needs to be easy

okay list starting here:

1. Consistent platform to build games on.   This could be accomplished by having a large system independent application like synaptic with repositories full of packages that will provide support for a generic gaming platform that can be used with many different distros. (the distro maintainers themselves would need to participate) Something that will allow many distros to use their own libraries and still use the gaming platform.

2. Advertise for free.  If everything else is free in Ubuntu shouldn't game advertising be as well?  More than just word of mouth.  Demos are a great way to advertise.  Even if a person can't play a whole level they still know without a doubt that the game will run on their system.:KS

3. How does WOW make lots of money?  People pay money every month to play on online servers.  What if the games are ported for free by people who know how:D and the software itself becomes free, but in order to do more than play a training demo players have to go online to play and pay, not for the game software, but the server time.  A credit system would be more beneficial to some gamers that only play once a week (if those exist) or don't play consistently over a month's time.  This also allows the game company to make the same amount of money from someone who can't pay a whole lot all at once but really wants to play.

4. Back to advertising.  Advertising that Ubuntu can play X popular game that is very mainstream in the Microsoft world looks very appealing to people wanting to convert to Ubuntu completely.  If X game runs with higher FPS, more stability, and such on Ubuntu then it becomes more desirable to play games on Ubuntu or something new like a... Gambuntu?

In order to provide better stability maybe it would be desirable to make an Ubuntu derivative that is only upgraded once every year or so giving an entire year for bugs to get worked out.  

Of course all this depends on number #1.

So really I'm asking what you think about #1.

---

### Post by HellionDarkLord on 2009-12-13
okay actually it loks like Play on linux may be just the thing.  That way nobody has to rely upon game companies to do anything.

---

### Post by EnGorDiaz on 2009-12-13
> **HellionDarkLord said:**
> My thoughts about gaming are as follows.

1.  Everybody wants to play their favorite game on Ubuntu. Everybody complains when they can't figure out how to play WOW or battlefield 2 or any of many other titles that won't run on Ubuntu.

2.  Nobody cares enough to go out of their way to make it happen.  It could happen if people really cared enough.

3. If you don't care enough to do something about it stop complaining!!

4.  I wish to start a group dedicated to Ubuntu gaming because I care enough that I want to start doing something about not being able to play decent games out of the box just as well as windows.  

The problem is that there are not enough people out there who understand how to port a game to Linux.

My only problem is that I don't know where to start learning how to port games to Linux otherwise I'd already have done it.

Any help would be appreciated.

listen to ur self for a damn second 

for one big companys like EA wont allow linux ports of there games its illegal against there eula

and to windows emulation layers arent going to be as good as real windows lets face it directx 11 < opengl 2.3

also it is ******* hard for the wine team no money sometimes short of developers depending on the season and almost no support from huge software companys so dont think they dont understand

---

### Post by hikaricore on 2009-12-13
> **HellionDarkLord said:**
> okay actually it loks like Play on linux may be just the thing.  That way nobody has to rely upon game companies to do anything.

POL is a frontend for WINE.  I fail to see how it has any relevance in this situation.

---

### Post by HellionDarkLord on 2009-12-13
okay i just tried unsuccessfully to make oblivion run in wine with POL.  All it does is says it's making a prefix then it freezes.  At least it didn't freeze the whole system.:-({|=
So much for it being the magic cure.  What games have you made work with POL?

---

### Post by sakuramboo on 2009-12-14
> **EnGorDiaz said:**
> for one big companys like EA wont allow linux ports of there games its illegal against there eulaGot any examples?

---

### Post by Arthur_D on 2009-12-14
> **HellionDarkLord said:**
> okay i just tried unsuccessfully to make oblivion run in wine with POL.  All it does is says it's making a prefix then it freezes.  At least it didn't freeze the whole system.:-({|=
So much for it being the magic cure.  What games have you made work with POL?
Age of Empires 3 and Trackmania. Didn't work OOTB with Wine, but POL did the trick(s). :D

---

### Post by del_diablo on 2009-12-14
> **HellionDarkLord said:**
> 1. Consistent platform to build games on.   This could be accomplished by having a large system independent application like synaptic with repositories full of packages that will provide support for a generic gaming platform that can be used with many different distros. (the distro maintainers themselves would need to participate) Something that will allow many distros to use their own libraries and still use the gaming platform.

Or they bluecopy what they are already doing, just do the entire libery blob they are already doing but the difference should be that the libs included in the games would be for fallback :P

---

### Post by HellionDarkLord on 2009-12-14
> **del_diablo said:**
> Or they bluecopy what they are already doing, just do the entire libery blob they are already doing but the difference should be that the libs included in the games would be for fallback :P

so they should include all the needed libraries in the games?  What do you mean?  would that make the game iso huge? I think that a downloadable gaming package that is custom done for every distro by the distro maintainers (If they want commercial game support) is feasible.  That way the game companies only have to worry about making the games and don't have to worry about what distro has what libraries.  That makes for too many variables.  If game companies were presented with something that says all you need to do is make it work with this gaming package, and we'll do the rest of the work with the extra libraries needed and other dependencies they would probably be more apt to make it work.  Simply cause it would cost them less in labor and customer support.  Ubuntu has GREAT customer support here!

---

### Post by HellionDarkLord on 2010-01-02
well, I'm slowly trying to make this game more awesome.  It's been abandoned and the developer's blog deleted so I don't think anyone will mind my messing with it.

This is the [[COLOR="Blue"]thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1353346").

check it out.  Not much yet, but getting there.

---

