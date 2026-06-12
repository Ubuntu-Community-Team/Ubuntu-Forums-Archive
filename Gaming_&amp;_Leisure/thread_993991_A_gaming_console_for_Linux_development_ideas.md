---
title: "A gaming console for Linux: development ideas"
date: 2008-11-26
forum: Gaming &amp; Leisure
---

### Post by kuniyori on 2008-11-26
Hello!!! New to the forum but I've been using linux for a number of years now and there is a few areas i would like to see exploited by linux that has not been done so far.

The main area so far is as gaming machine. While I know this is possibe, it is time consuming and overly complicated especially for a newbe. So here are some of the parts I think would help to make this a robust system.

1) A unified GUI for all legacy console systems, with the core emulator being viewed as a plugin to the main program.
2) Support for:
>NES
               >SNES
               >Nintendo64
               >GameCube
               >Sega MegaDrive/Genesis
               >Sega Saturn
               >Sega Dreamcast
               >PSX
               >PS2
               >and some of the associated handheld gaming
                systems
               >Windows PC games using WINE
3) Internet gaming in multiplayer mode similer to the mode on ZSNES
4) Support for PS3, XBox360 and Nintendo Wii controllers (including the chat pad addon for the XBox 360).
5) Voip and chat support for communication during multiplayer gaming
6) Library of games, roms and automatic downloading of artwork for games (similer to iTunes without all the nasty stuff!!)
7) Virtual drive for PC games

I just think this approach is a lot more reasonable than expecting developers to develop for or port games to linux:(...
Also give a good outlet for companies who developed games for older systems which are now obsolete. Plus its one thing that has really bugged me about all of the emulators so far and I really love my old games!!!!:lolflag: I have seen the project to integrate it into mythtv but its approach is not very good (IMHO). I jut thought a constructive approach is a lot better than the usual rant on this subject.

If anyone has any experience in any areas which are in this and would like to start a team to develop the idea (Grapic Artists/Designers, Programmers, etc..), or if anyone just has any ideas to add/remove from this list all comments are welcome!!!!!

---

### Post by johnkzin on 2008-11-26
Sounds like what you want is a non-portable version of an OpenPandora.  You might want to look into their project to see how you might apply it to a set-top-box or something.

---

### Post by MonkeyBoy on 2008-11-26
The [EVO]("http://www.evo-phase1.com/index.html") might be worth watching to see whether it gets adequate software support.  

The problem with all the non-mainstream consoles so far is that nobody makes a lot of software for them.  A couple of years ago a mate of mine got a gp2x while I got a tapwave zodiac.  The gp2x was far superior as far as hardware power went but the zodiac had much more software available from the palm community.  For this reason he got bored of his console quite quickly, but my zodiac was my favourite device for a long time.  

Maybe a console frontend would be a good solution.  Like mythtv but a console rather than a media centre.  Then we could build our own linux consoles.

---

### Post by crazyfuturamanoob on 2008-11-26
> **johnkzin said:**
> Sounds like what you want is a non-portable version of an OpenPandora.  You might want to look into their project to see how you might apply it to a set-top-box or something.

Pandora looks cool, it's even smaller than Sony's PSP, and far more powerful. (and more expensive)

It has even 2 joysticks! Looks perfect for gaming in places where I can't bring my laptop.

But can I run my own code on it freely, without any custom firmwares, hacks & exploits?

---

### Post by johnkzin on 2008-11-26
> **crazyfuturamanoob said:**
> Pandora looks cool (...)

But can I run my own code on it freely, without any custom firmwares, hacks & exploits?

It's a completely open Linux box.  Yes, you should be able to run anything on it that you compile for ARM Linux :-}  (I think they might be debian based, but I'm not sure)

But I'm not an expert.  You should ask over on their forums/lists.

---

### Post by kuniyori on 2008-11-26
> **johnkzin said:**
> Sounds like what you want is a non-portable version of an OpenPandora.  You might want to look into their project to see how you might apply it to a set-top-box or something.

Im thinking more of just a unified easy to use program on any linux distro. 

> **monkey boy said:**
> The EVO might be worth watching to see whether it gets adequate software support.

The problem with all the non-mainstream consoles so far is that nobody makes a lot of software for them. A couple of years ago a mate of mine got a gp2x while I got a tapwave zodiac. The gp2x was far superior as far as hardware power went but the zodiac had much more software available from the palm community. For this reason he got bored of his console quite quickly, but my zodiac was my favourite device for a long time.

Maybe a console front-end would be a good solution. Like mythtv but a console rather than a media centre. Then we could build our own linux consoles. 

This is the main problem that I see too. Im just a big fan of many of the older games but by combing all of these into one distro/program it gives you a really good software base to work with. It also help build a relation ship between games developers who worked on these older consoles and linux by giving them an outlet for what they thought were dead games, generating revenue for them. It builds a brand for them among linux gamers and a good repertoire with linux gamers were they to give old games away for free or at low cost.

By removing the barriers (high learning curve) for gamers on the linux system it might also change attitudes and due to the low cost of adopting such a system for anyone with a PC it builds it as a platform. Most emulators for the 'good' consoles are at a developed enough stage and have good quality games associated with them.

It just makes sense at the moment as each of the projects that would be needed to form the 'bigger picture' are at mature stage and are mostly quite stable. Its just a case of integrating them into a single package.

EVO woll not succeed as a platform because the cost to a developer is just too high, no player base, no other titles, etc.... I would prefer to make a game for any of the other consoles or Windows PC if I was a games developer... It just makes no sense to support it, a games company has to make money..

---

### Post by johnkzin on 2008-11-26
> **kuniyori said:**
> Im thinking more of just a unified easy to use program on any linux distro. 


By "a unified easy to use program", do you mean:

One emulator that emulates all of the platforms you listed, and has all of the features you listed.

Or

One front end program that invokes the various emulators in a friendly and easy to use manner, and add-on pieces to ensure the peripheral compatibility you mentioned.


There's a big difference between the two.  And, OpenPandora may have the latter (they're not just a hardware device, they're a gaming solution to replace the gp2x that Monkeyboy mentioned.  I know that a lot of their gaming capability is going to come from bundling other open emulators and just letting you use those for multi-platform game compatibility.  I imagine that they're planning to put a friendly font end on it.  So, it might be possible to leverage that front end.  There are a lot of people putting a ton of effort into OpenPandora ... you might find that it'd be easiest to leverage their project into a console variant to match what they're doing.

(In case it wasn't clear, they are a fan/customer base from the old gp2x that decided to "build their own" when that project died out.  They're a community driven project that is designing their own hardware and their own linux based gaming platform, utilizing a range of emulators; the hardware designers had to form a company for manufacturing the hardware, but the software is still community driven.)

I have no idea how dist. neutral they're being.  I'm sure that for what they're generating they're going to put it on top of one dist. (like I said, I think it's debian-arm based).  But, how hard would it really be to take that effort and "port" it to other dists?

And, you never know, they might think it's such a great idea that you wouldn't have to fork their code, but instead just be a side-project (or even part of the core project) for OpenPandora.


Really, look into their project, what you want doesn't sound amazingly different from what they're doing.  The main difference is:

1) they have a target platform that they created for the project.

2) they are probably only planning to support 1 dist.

If they're staying as open as they originally planned, then you may find that while their core effort sticks to those two, they may be open to contributors who submit changes/fixes/etc. that help it work on multiple hardware platforms and multiple linux dists.

---

