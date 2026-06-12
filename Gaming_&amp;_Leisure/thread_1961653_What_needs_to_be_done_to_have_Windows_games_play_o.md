---
title: "What needs to be done to have Windows games play on Ubuntu without Wine?"
date: 2012-04-19
forum: Gaming &amp; Leisure
---

### Post by epicbattle on 2012-04-19
I imagine it is a lot. But someday, might it be possible to install a windows game on Ubuntu without the use of Wine or having the company fully convert over to linux compatibility? To the point that it is just install and play? If it is possible, what needs to happen? What can I do to help the Linux community gain this ability? From the kind of software or drivers, to the people that have to OK it? 

:) Thanks!

---

### Post by haqking on 2012-04-19
> **epicbattle said:**
> I imagine it is a lot. But someday, might it be possible to install a windows game on Ubuntu without the use of Wine or having the company fully convert over to linux compatibility? To the point that it is just install and play? If it is possible, what needs to happen? What can I do to help the Linux community gain this ability? From the kind of software or drivers, to the people that have to OK it? 

:) Thanks!

about the same as sticking a VHS tape into a DVD player ;-)

---

### Post by lisati on 2012-04-19
"It depends", and at the very least will likely involve recompiling from source. Chances are that there will be a LOT of work needing to be done that will be beyond the skills of a casual game player.

> **haqking said:**
> about the same as sticking a VHS tape into a DVD player ;-)
Nice analogy, better than the "Stick a DVD in a CD player and see what happens" one that I thought of.

---

### Post by Sofox on 2012-04-19
The best hope for a Linux port is to get the source code of the game released by the company

This way, the fans can port the game over, and the game company can maintain their rights to sell the game by keeping the game asset under their copyright.

To give a topical example, a while back the source code for an old RPG called Arx Fatalis was released, and [just recently the Linux port of their engine reached 1.0]("http://www.ubuntuvibes.com/2012/04/first-stable-release-of-arx-libertatis.html").

Keep in mind, this example also has the advantage of future proofing the game. A game released on Linux today may not run on a Linux computer that's made 10 or 20 years from now, so having the game open source means that if there's interest, the game can always be updated for the newest systems, or for new features.

---

### Post by donkyhotay on 2012-04-19
> **epicbattle said:**
> I imagine it is a lot. But someday, might it be possible to install a windows game on Ubuntu without the use of Wine or having the company fully convert over to linux compatibility? To the point that it is just install and play? If it is possible, what needs to happen? What can I do to help the Linux community gain this ability? From the kind of software or drivers, to the people that have to OK it? 

:) Thanks!

As mentioned, you either need the source code to port it or you need wine as a compatibility layer. The analogy of trying to stick a DVD into a CD player and expecting to "just work" is a pretty good one. Windows software and linux software are two completely different things and just won't work without some sort of conversion.

---

### Post by Ghil on 2012-04-19
The main problem is and always will be DirectX. A lot of games uses these libraries, and unless you are willing to rewrite every game to use the equivalent in OpenGL, this is a dream that is way too far away.

---

### Post by Zeven on 2012-04-19
You can start by showing your support via Kickstarter, the Humble Bundle, Desura, and [here.]("http://ubuntuforums.org/showthread.php?t=1949235") Show developers that money can be made.

---

### Post by forrestcupp on 2012-04-20
The OP is not talking about ports. He's talking about getting Ubuntu to the point to where it can just install games that were created for Windows on its own without even having to use Wine. It will never happen, even if it could happen. Ubuntu is an *alternative* to Windows, not a *clone* of Windows. Ubuntu will never be able to install Windows games for the same reason that Macs can't, and the same reason that PS3s can't run Xbox 360 games.

If you want a clone of Windows, you need to check out ReactOS, and talk to them about what will it take to run Windows games. Either that, or just use Windows, which probably came on your computer. ;)

---

### Post by tmaranets on 2012-04-20
I think there are other programs that allow you to install Windows games and software.
----------------------------------------------------------------------------
[http://www.addictivetips.com/ubuntu-linux-tips/install-software-unavailable-in-ubuntu-repository-with-bleeding-edge/](http://www.addictivetips.com/ubuntu-linux-tips/install-software-unavailable-in-ubuntu-repository-with-bleeding-edge/)
----------------------------------------------------------------------------
I haven't tried it yet, but it looks good.

---

### Post by forrestcupp on 2012-04-20
> **tmaranets said:**
> I think there are other programs that allow you to install Windows games and software.
----------------------------------------------------------------------------
[http://www.addictivetips.com/ubuntu-linux-tips/install-software-unavailable-in-ubuntu-repository-with-bleeding-edge/](http://www.addictivetips.com/ubuntu-linux-tips/install-software-unavailable-in-ubuntu-repository-with-bleeding-edge/)
----------------------------------------------------------------------------
I haven't tried it yet, but it looks good.

That does look pretty awesome, but it's not for Windows software. That is for Linux software that isn't available, or the latest versions aren't available in Ubuntu's repositories.

---

### Post by Chame_Wizard on 2012-04-20
Porting with OpenGL!!:guitar:

---

### Post by Zeven on 2012-04-20
> **Ghil said:**
> The main problem is and always will be DirectX. A lot of games uses these libraries, and unless you are willing to rewrite every game to use the equivalent in OpenGL, this is a dream that is way too far away.

Why don't all developers just develop using OpenGL? That way they can get an additional 10% of the market by getting games on Mac OS and Linux as well.

---

### Post by Dlambert on 2012-04-20
I think a kernel with WINE functionality built in would be a good start.

---

### Post by haqking on 2012-04-20
> **Dlambert said:**
> I think a kernel with WINE functionality built in would be a good start.

not everyone wants or needs to use wine, why build in overhead for a given % of users.


why not build in everything into the kernel then ?

This is a pointless thread i mean,

why dont petrol cars run off diesel ?

why cant VLC open spreadsheets ?

Why cant you use a kettle to watch TV ?

Why dont VHS tapes fit and play in a DVD player ;-)

LOL

Peace

---

### Post by Sofox on 2012-04-20
> **Zeven said:**
> Why don't all developers just develop using OpenGL? That way they can get an additional 10% of the market by getting games on Mac OS and Linux as well.

Boy, did you miss the gigantic OpenGL vs DirectX war of the late 90s/early 00s?

To be honest, I don't know that much about it myself, but from what I recall Microsoft claimed a lot about how OpenGL was inferior to DirectX and DirectX was best for Windows and most supported. Obviously, this was a hugely debated issue, but Microsoft made a huge effort towards making DirectX good quality and promoting it as the best platform and Linux and Mac wasn't seen as important back then so people went with DirectX (not everyone did though, keep in mind Half-Life supported OpenGL, and id have long been supporters of it). 
There were two legitimate strenghts of DirectX back then though: DirectX could be faster at introducing new features since Microsoft could just say "yes" while OpenGL there had to be agreements between several companies before introducing new features; secondly since most games ended up supporting DirectX, it led a lot of graphics card makers to make cards and drivers that supported DirectX primarily and OpenGL to a lower quality. I don't know how it is these days though.

---

### Post by forrestcupp on 2012-04-20
> **Zeven said:**
> Why don't all developers just develop using OpenGL? That way they can get an additional 10% of the market by getting games on Mac OS and Linux as well.Because DirectX isn't just graphics. It's everything, including 3D audio and input devices, and it all works together seamlessly, like the positioning of an object in 3D space affects that object's audio in 3D space as well. OpenGL is just hardware accelerated graphics. It doesn't all port.

> **haqking said:**
> 
Why cant you use a kettle to watch TV ?

Lol.

I used a fish tank to watch TV once. When I was a young kid, and I was supposed to be in bed, I watched almost an entire episode of Saturday Night Live by hiding in the other room and watching the reflection on the aquarium. :D

---

### Post by na5h on 2012-04-20
I guess Java's "Write once, run anywhere" philosophy could come in handy here...browser-based games written in Java or Javascript might not be such a a bad idea either. HTML5! :-) Or perhaps games written in Python?

As for the "What needs to be done to have Windows games play on Ubuntu without Wine" question...Windows is NOT Linux!

---

### Post by forrestcupp on 2012-04-21
> **na5h said:**
> I guess Java's "Write once, run anywhere" philosophy could come in handy here...browser-based games written in Java or Javascript might not be such a a bad idea either. HTML5! :-) Or perhaps games written in Python?Games *can* be easily written to be portable. There are decent 3D and game engines out there that allow you to write code once, and it only needs to be recompiled for the different platforms. The problem is that most commercial game companies don't know or care.

---

### Post by del_diablo on 2012-04-21
> **na5h said:**
> Or perhaps games written in Python?

Compitablity break EACH version update. 2.5 python does not work with 2.6 python, etc. There is a reason why applications on Windows, who is using Python usually is bundeled with Python, just to avoid this issue.
The only thing so far that has not suffered severe break on update is Java.

> Native packages

Breaks at each major OS update. Look at Linux Game Binaries, you need to apply hacks or get recompiled versions of it.
Point in case: Is there and 2003 linux games you can still download and that works on Linux without having to apply severe hacks or compiling old libaries for them? Lugaru requires "hacks" to get it working on a modern distro, the same applies to other old binaries.

> Compiling from source

As lisati said, it will break and its too complex for a normal user. Even if it involes a automatisation of the compiling(IE: The installer is basically the compiler, but its like a Windows installer), it will at some point break due API incompitablities, which is a severe issue.

---

### Post by forrestcupp on 2012-04-22
> **del_diablo said:**
> 
As lisati said, it will break and its too complex for a normal user. Even if it involes a automatisation of the compiling(IE: The installer is basically the compiler, but its like a Windows installer), it will at some point break due API incompitablities, which is a severe issue.

especially if they use winAPI and DirectX.

---

### Post by Romeo9 on 2012-04-22
@[epicbattle]("http://ubuntuforums.org/member.php?u=609636"): You can't run windows games without wine or without porting it over completely.

There are a few ways I can think of that can make it easier and more user friendly to install windows games on Ubuntu, such as integrating wine with the Ubuntu OS on a very deep level and with some modification to the UI, for example removing borders, that will result in running windows games, programs installers etc... without noticing that wine is even being used and will give the game a very native feel.

Another way would be to use a botteling app, currently there aren't any on Linux, or atleast not that I know of, however Mac has 3 that I'm aware of, the most common is Winebottler: [http://wiki.winehq.org/WineBottler](http://wiki.winehq.org/WineBottler)

Other than that I can't think of any other way

---

### Post by jwbrase on 2012-04-22
> **epicbattle said:**
> I imagine it is a lot. But someday, might it be possible to install a windows game on Ubuntu without the use of Wine or having the company fully convert over to linux compatibility? To the point that it is just install and play? 

You only need to install Wine once. After that it is just install and play for most games that will actually run in the first place.

> If it is possible, what needs to happen? What can I do to help the Linux community gain this ability? From the kind of software or drivers, to the people that have to OK it? 

:) Thanks!

Well, you could get really rich, buy the rights to Windows from Microsoft (and from anybody they've licensed code from), open source it, and then hire a bunch of people to integrate the Windows API into the Linux kernel (I myself would use the Windows source to improve Wine, but since you're looking for a way to not use Wine, you'd have to deal with the kernel).

Let me know when you have a few billion dollars and are ready to make Microsoft an offer. :)

---

### Post by forrestcupp on 2012-04-23
People who want Linux to run like Windows just need to look into KDE for Windows, or other Windows shell replacements.

---

### Post by haqking on 2012-04-23
> **forrestcupp said:**
> People who want Linux to run like Windows just need to look into KDE for Windows, or other Windows shell replacements.

People who want Linux to run like windows, need to look in the mirror and ask themselves.......WHAT ?

---

### Post by jmszr on 2012-04-25
An interesting possible alternative?: [https://decentralist.wordpress.com/2012/04/24/is-microsoft-driving-valve-and-steam-to-strengthen-linux-as-a-gaming-platform/](https://decentralist.wordpress.com/2012/04/24/is-microsoft-driving-valve-and-steam-to-strengthen-linux-as-a-gaming-platform/) .

---

### Post by The Rnegade on 2012-05-01
> **epicbattle said:**
> I imagine it is a lot. But someday, might it be possible to install a windows game on Ubuntu without the use of Wine or having the company fully convert over to linux compatibility? To the point that it is just install and play? If it is possible, what needs to happen? What can I do to help the Linux community gain this ability? From the kind of software or drivers, to the people that have to OK it? 

:) Thanks!

I mean you could contact game developers asking them to consider making linux bianaries for their games, i dont know how succesful that would be. you would have to get there attention and you would have to convince them that it would be a profitable endeavor. maybe if you started some kind of online petition for it and get millions of signatures, you could convince them. 

the game companies have to make the ports unless source code is release which makes it possible for third parties to build linux ports. 

right now there are some companies that port games to linux upon the request of the game company, one example is lokkisoftware

---

