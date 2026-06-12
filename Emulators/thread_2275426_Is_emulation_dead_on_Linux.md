---
title: "Is emulation dead on Linux?"
date: 2015-04-26
forum: Emulators
---

### Post by BigSilly on 2015-04-26
Quite surprised by the almost total dearth of emulation options on modern Linux distros these days. It used to be a real strength of the platform. Can't find things like Snes9x-gtk or anything like it, can't find anything decent Sega related (beyond kludging in Kega), Retroarch doesn't seem to want to work. At first I thought it might just be an Ubuntu 15.04 thing, but looking across even things like Arch and Debian itself I can't find anything ready to go out of the recognised programs, and even less new emulators and options.

Very sad. :(

---

### Post by General_Faliure on 2015-04-26
I don't agree with you.
You are right that it is a bit more difficult as with windows, but a lot of emulators and front ends can be found.
I have built my arcade cab over 4 years ago, and it has been running Lubuntu Linux from the beginning.
You may have to add some PPA's for the newest emulators, but my cab runs rock solid from the beginning.
Also, Daphne, the laserdisk emulator requires you to install ia32 libs on a 64 bit system, but after that it works fine.
So far, mainly pcsx2 i can't get to play nice, most games run too slow, or with visual errors. I haven't put much time in it, i mostly like the arcade and laserdisk games.
Here's a link for info on emulator PPA's: [http://emulation-general.wikia.com/wiki/Emulation_on_Ubuntu](http://emulation-general.wikia.com/wiki/Emulation_on_Ubuntu)
Here for the Amiga: [http://fs-uae.net/download#ubuntu](http://fs-uae.net/download#ubuntu)
Don't give up too easily.

---

### Post by BigSilly on 2015-04-26
I'm familiar with most of those PPA's, and they haven't been updated for the newest Ubuntu. I can't run snes9x-gtk, it hasn't been updated. Ditto Retroarch, which though it has a PPA for 15.04, it doesn't run properly. You're right and I don't mean to be negative, but it's just that we seem to be going through a bit of a bad period with emulators on the desktop, and I wanted a bit of a moan about it. :-D  Maybe they'll update soon enough and I'll be happy again.

---

### Post by Holger_Gehrke on 2015-04-26
Dead as Cthulhu ('That is not dead which can eternal lie,/And with strange aeons death may die.'), I'd say.
A lot of emulators are open source, so nothing stops you from compiling them yourself - and perhaps even setting up your own PPA.
The only real problem I see for emulation is that all the classic consoles are emulated at a more than acceptable level of fidelity and the next generation which is not emulated consists of systems that are close enough to PCs in term of power (both cpu and graphics), that real time emulation might not be possible.

And now for something completely different: I recently came upon [this article]("http://wfae.org/post/retro-video-games-link-past") on the website of an NPR station about classic video game sales. Towards the end it talks about parents who are buying classic video games for their kids. They grew up with those games, know them and are certain that they are okay for the kids. Those kids might grow up to be the next generation of emulator users ...

---

### Post by General_Faliure on 2015-04-27
15.04 has just been out a couple of days, so you have to give them some time.
One could also say Ubuntu is updating too fast for the developers to keep up:-)

---

### Post by michael-piziak on 2015-06-28
I am using Snex9x on an Ubuntu 12.04 lts system.  I have not upgraded to a newer Ubuntu because I couldn't get it to work on two 14.04 lts systems.   12.04 lts is supported until April of 2017, so I see no need to keep updating my system when I find that my old programs (mostly emulators) aren't being updated to work on the latest Ubuntu.

You can try to install Snes9x how I did though and see if it will work on your system.  The terminal instructions are:

[COLOR=#333333][FONT=Verdana][SIZE=3]**sudo add-apt-repository ppa:bearoso/ppa**[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana][SIZE=3]**sudo apt-get update**[/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana][SIZE=3]**sudo apt-get install snes9x-gtk**[/SIZE][/FONT][/COLOR]


[COLOR=#333333][FONT=Verdana][SIZE=3]Thiscame from the website: [http://www.upubuntu.com/2012/09/a-list-of-best-game-console-emulators.html](http://www.upubuntu.com/2012/09/a-list-of-best-game-console-emulators.html)

Higan, the new name for bsnes, works good on 14.04 lts systems.  It's available in the software center.

I don't know what you meant by "kludging in kega" but Kega Fusion does work well for Sega and is in the software center also.[/SIZE][/FONT][/COLOR]

---

