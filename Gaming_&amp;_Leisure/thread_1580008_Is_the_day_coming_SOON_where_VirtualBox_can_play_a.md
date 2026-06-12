---
title: "Is the day coming SOON where VirtualBox can play any game?"
date: 2010-09-22
forum: Gaming &amp; Leisure
---

### Post by adn258 on 2010-09-22
Personally Linux is great for me because I don't play video games anymore at all.  So I don't care about that.  Many people do however enjoy emulators games.  I've noticed ps2 emulators etc. having a lot of problems on linux.  I do use windows as a guest os in my virtual box.  

I was reading recently that they may soon have support for 3d game cards on the host through the virtual.  Basically you can't play high graphical games using virtualbox on Ubuntu because it won't support a high graphics card on the virtual system on the host.

There has been talk about changing that though which would take major efforts.  IF that happened it would mean that hardcore gamers though could get rid of windows as their main os and use Linux  with windows installed virtually on virtualbox while at the same time they could play all the games that they wanted (AND USE MORE EMULATORS ps1 ps2 etc.) .

I think this will be a HUGE step into promoting linux and free software even more than it's becoming lets hope the day comes soon when this happens.  What do people here think?  Does anyone know anything more for the news on this subject?

---

### Post by Justin_Bailey on 2010-09-22
I'm not really sure what problems you're having with console emulators, but I can assure you're that you are in the minority.

Linux doesn't need a VM crutch to run emulators or even games.  Native games and emulators run just fine if your hardware is capable.
The problem many users run into is a lack of understanding.  Your "designed for windows" bottom of the barrel DirectX integrated video cards often lack proper drivers and OpenGL support.  These misinformed users then attempt to run windows programs through wine and can't grasp why they fail where users with proper hardware breeze right through.

As for native programs, games, emulators etc.  You still need to be certain your hardware is capable and that you've properly configured these programs.
Trying to run pcsx2 on a lowend single core processor with an Intel video chip is bound for sorrow where as a decent dual core and an ati/nvidia card works quite well.

---

### Post by ucal on 2010-09-22
How would it change anything?  Gaming companies would still make games for windows and linux users would still have to buy windows.  I guess it would be slightly more convenient, but hardly groundbreaking in any important way.

---

### Post by mips on 2010-09-23
> **Justin_Bailey said:**
> 
The problem many users run into is a lack of understanding.  Your "designed for windows" bottom of the barrel DirectX integrated video cards often lack proper drivers and OpenGL support.

What video cards lack OpenGL & DirectX support? All my nVidia cards to date have supported them.

@adn258
From a emulator standpoint the native emulators for Linux should run just fine. The Windows ones however seem to be slightly better though, probably due to more users & support. But for all intense purposes the native linux ones are just fine.

If you are referring to native windows games running on Win in a VM then I understand what you are getting at. DirectX to OpenGL translation is still not quite there yet although you already see products like VMWare Fusion for Mac etc. This will only get better with time. There are two ways of doing this, translating DirectX to OpenGL (Wine D3D) which is slower or accessing the GPU hardware directly.

---

### Post by adn258 on 2010-09-23
ok got a lot of negative remarks on this one lol.  Well I am using the 64 bit ubuntu and currently for example PCSX2 doesn't work really because it was written for 32 bit linux .  I don't want to switch too 32 bit but this is another story.

Otherwise other linux native emulators have worked fine for me as well pcsx2 with 64 bit ubuntu at this point though is really a no go.  No matter how you cut it while I HATE WINDOWS with a passion it does at least at this point have better total gaming support emulators or not;  pcsx2 for windows 64 bit but not for ubuntu 64 bit is an example of this.

Peace

---

### Post by Justin_Bailey on 2010-09-23
> **mips said:**
> What video cards lack OpenGL & DirectX support? All my nVidia cards to date have supported them.

I suggest reading my post again.
This is not what I said at all.

---

### Post by mips on 2010-09-23
> **Justin_Bailey said:**
> I suggest reading my post again.
This is not what I said at all.

> Your "designed for windows" bottom of the barrel DirectX integrated video cards **often lack proper drivers and OpenGL support.**

I'm not following.

---

### Post by Justin_Bailey on 2010-09-23
Much of my response was directed at Intel graphics chips.
As such the section you quoted without context was as well.

Back on topic, if you're running software known to have issues with 64bit such as pcsx2 then you're obviously going to have trouble.  The topic of operating system and virtual machines is irrelevant at best in this case, once the kinks are worked out of pcsx2 on 64bit this will be a non-issue.

---

### Post by Ozor Mox on 2010-09-24
This is what I'm really hoping for. For the most part, I'm happy to buy games for my PS3, and play FOSS games on Ubuntu. Every so often though, a PC game will be released for Windows that I *really* want to play, and I get narked that I'll have to acquire a copy of Windows and set up a dual boot just to play it. Great example right now, Civilization V.

If I could install Windows in a virtual machine to play these games that require 3D acceleration, I would look like this -> :D

---

### Post by adn258 on 2010-09-25
> **Ozor Mox said:**
> This is what I'm really hoping for. For the most part, I'm happy to buy games for my PS3, and play FOSS games on Ubuntu. Every so often though, a PC game will be released for Windows that I *really* want to play, and I get narked that I'll have to acquire a copy of Windows and set up a dual boot just to play it. Great example right now, Civilization V.

If I could install Windows in a virtual machine to play these games that require 3D acceleration, I would look like this -> :D

My point exactly it would feel ten times better playing the game on a virtual windows machine as the guest OS not another OS and having to duel boot :].  That was my point lol.  

Peace

---

### Post by del_diablo on 2010-09-25
> **Justin_Bailey said:**
> Much of my response was directed at Intel graphics chips.

Intel? That not even GFX cards. Its just something so you can get render with.
It sucks equally under Windowze.

---

### Post by Justin_Bailey on 2010-09-25
Well that's not entirely true, the video drivers for integrated intel chips are much more reliable on windows and there's also the benefit of DirectX functionality which can not be used on Linux.

---

### Post by del_diablo on 2010-09-26
While that is true, a lot is still lacking of DX exntensions under Windows too.

---

