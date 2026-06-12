---
title: "Games for Mac but not linux?"
date: 2009-11-20
forum: Gaming &amp; Leisure
---

### Post by pieman711 on 2009-11-20
I've recently noticed (never really thought about it before) that there are quite a few games out that appear to run natively in Mac os X. Why is there a drive to bring out games for os X and less of a drive to port games to linux? I noticed there is a company, aspyr,  that managed to port COD4 to os X but I haven't heard about any plans for it to come to linux. 
The only mainstream game I've manage to install natievely in liunx is neverwinter nights and I've got a few things working in Wine (last night I managed to get nwn2 to install in wine using [http://illespal.googlepages.com/wine.html](http://illespal.googlepages.com/wine.html) ) 
I would love it if more games installed natively in linux and for me it is ther only, and quite major, downside of using ubuntu as an OS.
Does anyone know why it is possible to get a game like COD4 to run in os X and not ubuntu?

---

### Post by Aayu on 2009-11-20
Firstly, while it certainly is easier to port a game from OS X to Linux, they are both still, very different machines.  The kernel is different (obviously) the underlying architecture is different (all Macs are 64bit), therefore, a porting company would need to develop a 32bit version from the 64bit version (a port of a port).  There are also tons of different distros to test on (Debian, Ubuntu, Fedora, Slackware, CentOS etc), a company would NEVER make a game for just a single distro..  and the amount of resources that would take, well, it wouldn't be financially viable.

---

### Post by johnboy1313 on 2009-11-20
Aayu hit the nail on the head, there is no way a company would release software to a open source platform it would not be financially viable.

---

### Post by lakersforce on 2009-11-20
> **Aayu said:**
> ...(all Macs are 64bit), therefore, a porting company would need to develop a 32bit version from the 64bit version (a port of a port)....

It's only a matter of time before 32-bit will disappear. Who still uses 32-bit anyway? (I know that some does, but it's a transition phenomenon.) I have been using 64-bit exclusively aprox. the last 3 years.

---

### Post by poebae on 2009-11-20
> **johnboy1313 said:**
> Aayu hit the nail on the head, there is no way a company would release software to a open source platform it would not be financially viable.
I think you've misinterpreted what Aayu said.

A company releasing software for an open source platform doesn't mean that they have to make that software open source. There's nothing wrong with charging money for a closed-source Linux client of a game.

---

### Post by beastrace91 on 2009-11-20
> **johnboy1313 said:**
> Aayu hit the nail on the head, there is no way a company would release software to a open source platform it would not be financially viable.

I think you both missed the point. They COULD very well make money off it. And once a game is ported to OSX it is really decently easy to port said game to Linux most times - the biggest hurdle in porting a game is replacing the M$ only DirectX with something else (most commonly OpenGL). Once this is done it is a bulk of the work.

As for having to test on multiple distros - the solution to this I think is pretty simple. You test on like the top two or three distros (Ubuntu and Fedora for example) and then you release a .deb, .rpm, and .run file versions of the game installer. The first one for Ubuntu the second for Fedora and the third for everything else. Then from there you state that you only officially offer support for these top two distros (but people are more than welcome to try and get it running on all the others under the sun using the .run installer).

IDK, just my 2 pence,
~Jeff

---

### Post by pieman711 on 2009-11-20
I wasn't talkikng about porting from os X to linux exactly, just wondering if it was done commercially from win to os X how come it wasn't done from windows to linux? How do mac users get around the direct x problem? If activision were happy to let select apple developers port their software i can't imagine microsoft being happy to give them free reign of direct x.
Also I didn't mean just handing the software to an open source project. I was thinking more of a company like aspyr porting it for a profit. It's easy to see why no one wants to give money making software to open source...

---

### Post by Bölvaður on 2009-11-20
isn't it that games are "ported" via WINE. Think that is the trick many companies use instead of doing it properly.

---

### Post by Aayu on 2009-11-20
> **pieman711 said:**
> I wasn't talkikng about porting from os X to linux exactly, just wondering if it was done commercially from win to os X how come it wasn't done from windows to linux? How do mac users get around the direct x problem? If activision were happy to let select apple developers port their software i can't imagine microsoft being happy to give them free reign of direct x.
Also I didn't mean just handing the software to an open source project. I was thinking more of a company like aspyr porting it for a profit. It's easy to see why no one wants to give money making software to open source...

It took aspyr almost a year and a half to get COD4 out on the mac.  It really does depend on wether companies see a profit in doing it for Linux.  Aspyr's games obviously don't sell as well on the mac as the PC versions do but sure, they could make a profit, any porting company could, providing it was planned and done properly..  most don't want to / think it's too risky (especially on Linux).  As for the DX problem, the games use OpenGL on mac, which is a huge job in itself..  another problem would be if a game used low level assembly (some still do) for small parts of the core engine, I know all too well what a slap in the face porting asm to other OS's is like.. 

I would love to have most of my games on Linux though, then I'd have zero need for Windows on my rig!

---

### Post by pieman711 on 2009-11-20
Yeah I notice it wasn't exactly an instant process. 
I've not got much experience with programming, the closet I've come to it is dabbling in basic when I was about 16 (don't blame me, I got into the wrong crowd at college) but if the work was already done to get it into open GL for os X would it then be easier to get it to linux? Would be better to try and make a XINE instead of WINE?

---

### Post by schwim on 2009-11-20
I've got a lovely computer with fantastic stats sitting right beside my work machine that I use for gaming.  I would never consider having anything but Windows on it. Wine (and PlayonLinux) is a joke if you actually enjoy gaming.

I'll be as happy as everyone else if linux ever becomes a viable gaming platform, but I'm not holding my breath and I'm not searching for tutorials to install a game on a platform that it wasn't designed for.

---

### Post by Vadi on 2009-11-20
> **Aayu said:**
> Firstly, while it certainly is easier to port a game from OS X to Linux, they are both still, very different machines.  The kernel is different (obviously) the underlying architecture is different (all Macs are 64bit), therefore, a porting company would need to develop a 32bit version from the 64bit version (a port of a port).  There are also tons of different distros to test on (Debian, Ubuntu, Fedora, Slackware, CentOS etc), a company would NEVER make a game for just a single distro..  and the amount of resources that would take, well, it wouldn't be financially viable.

Wrong.

Heroes of Newerth has one part-time person providing both OS X and Linux versions just fine. It's not that much work in reality.

---

### Post by lakersforce on 2009-11-20
> **poebae said:**
> ...closed-source...

Don't use that word! It's not even a real word.

---

### Post by hikaricore on 2009-11-20
> **lakersforce said:**
> It's only a matter of time before 32-bit will disappear. Who still uses 32-bit anyway? (I know that some does, but it's a transition phenomenon.) I have been using 64-bit exclusively aprox. the last 3 years.

Uhhh.... myself and almost everyone I know is still using 32bit.
64bit has nothing to offer at the moment except for headaches.

---

### Post by del_diablo on 2009-11-20
> **Aayu said:**
> It took aspyr almost a year and a half to get COD4 out on the mac.  It really does depend on wether companies see a profit in doing it for Linux.  Aspyr's games obviously don't sell as well on the mac as the PC versions do but sure, they could make a profit, any porting company could, providing it was planned and done properly..  most don't want to / think it's too risky (especially on Linux).

Mac uses GCC & G++ does it not? Meaning its just to recompile it and it will run.

---

### Post by lakersforce on 2009-11-20
> **hikaricore said:**
> 
64bit has nothing to offer at the moment except for headaches.

Only problem I ever experienced was playing youtube in the browser.

But as I said 32-but users is a transition phenomenon. (No flame intended, but it is the truth.) If you start porting games from Mac to X86_64 (or AMD64), my bet is most people will stop using 32-bit. So it is not really an issue to worry about.

---

### Post by hikaricore on 2009-11-20
The thing is 32bit works and will continue to do so for a long time.
Most people don't need 64bit at all.  Btw lets try and get this thread back on topic.

---

### Post by beastrace91 on 2009-11-20
> **Vadi said:**
> Wrong.

Heroes of Newerth has one part-time person providing both OS X and Linux versions just fine. It's not that much work in reality.

LOL. Nice.

~Jeff

---

### Post by Aayu on 2009-11-21
> **del_diablo said:**
> Mac uses GCC & G++ does it not? Meaning its just to recompile it and it will run.

Technically, yes, it would compile fine on a 64bit Linux distro.  Well, in an ideal world, but then none of us know what stuff they put into the game in the first place, especially if it is portable easily or not.  But the main question for a company would be 'How many people have gaming capable rigs on Linux?'.  Macs are barely gaming capable as they are now and the only games I run on it are Warcraft 3, Starcraft, World of Goo and Bejewelled lol.

As for Heroes of Newerth..  I wouldn't compare closed beta support, to the support of a fully released game.  Two very different beasts.

---

### Post by Sindwiller on 2009-11-21
> Who still uses 32-bit anyway?

Thread Hijack: Probably the vast majority who are running a 64-bit CPU with less than 3.5 GB RAM and less than 5 TB (is this number right? Or was it 20 TB?) harddisk space they have to address - basically those who don't want to hassle with missing 64-bit drivers, like me. It won't disappear for the next 5 years either.

Back on topic:

OS X is in many ways different - and more shitty if I believe what I hear.

> Mac uses GCC & G++ does it not? Meaning its just to recompile it and it will run.

No.

Stuff compiled with MingW (that's the gcc port for Windows) isn't automatically cross-platform either.

---

### Post by HTML-insane on 2009-11-21
What frustrates me the most is when games are available for the X-Box, PS2/3, Nintendo Wii, Windows, Mac OS and... NOT Linux. I mean... Mac OS, the PS2/3 and Nintendo Wii all rely on OpenGL for graphics anyway!

---

### Post by pieman711 on 2009-11-21
As for the 64bit/32bt discussion, I'm currently using a 32bit distro and am quite happy staying with it at the moment (if it ain't broke don't fix it!) but if it meant I could start playing better games I'd jump to 64bit without hesitating. 

I would have thought that there would be more people using gaming capable rigs with linux than there would be using os X. I didn't think apple really focusd there hardware in that direction and actually go out of their way to stop you putting os X on non apple hardware ([http://it.slashdot.org/index2.pl?fhfilter=apple+atom](http://it.slashdot.org/index2.pl?fhfilter=apple+atom)). I think if there were more main stream games for linux then a lot more people ould move their gaming rigs across to linux. I know it is the only thing holding some of my friends back and as I mentioned earlier it's the only peoblem I have using linux.

---

### Post by beastrace91 on 2009-11-21
Yep. I have four of five friends that would stop dual booting and I have an even larger number of friends that would jump over to Linux (who only use Windows currently) if their games all ran on them. The only major issues I've ever really had with Ubuntu is getting Windows software to work :-/ 

That being said - whether or not OSX source code could be recompiled right away on Linux is not really a huge deal IMO. The fact of the matter is (For the most part) the number of functions you would have to change/adapt from the OSX compiler to work with Linux would be small - because as stated once its running on OpenGL instead of DirectX thats a majority of the porting work.

~Jeff

---

### Post by Aayu on 2009-11-21
> **pieman711 said:**
> As for the 64bit/32bt discussion, I'm currently using a 32bit distro and am quite happy staying with it at the moment (if it ain't broke don't fix it!) but if it meant I could start playing better games I'd jump to 64bit without hesitating. 

I would have thought that there would be more people using gaming capable rigs with linux than there would be using os X. I didn't think apple really focusd there hardware in that direction and actually go out of their way to stop you putting os X on non apple hardware ([http://it.slashdot.org/index2.pl?fhfilter=apple+atom](http://it.slashdot.org/index2.pl?fhfilter=apple+atom)). I think if there were more main stream games for linux then a lot more people ould move their gaming rigs across to linux. I know it is the only thing holding some of my friends back and as I mentioned earlier it's the only peoblem I have using linux.

It's actually illegal to put OS X on non Apple hardware, as per Apple's EULA.  If more and more games on Linux 'do' start appearing, I'd be worried about their stability and performance.  Games (even native ones from Aspyr) run like molasses, Sim City 4 is a prime example of a 5 year old native OS X game running poorly on my 2008 iMac, so if a company did a quick and dirty to Linux, would anyone actually WANT to play it?

---

### Post by del_diablo on 2009-11-21
> **beastrace91 said:**
> That being said - whether or not OSX source code could be recompiled right away on Linux is not really a huge deal IMO. The fact of the matter is (For the most part) the number of functions you would have to change/adapt from the OSX compiler to work with Linux would be small - because as stated once its running on OpenGL instead of DirectX thats a majority of the porting work.

~Jeff

1. OS X is Unix certified, and its POSIX compitable
2. OS X and GNU/Linux both use the GCC/G++ compiler
3. OS X is running a X11 compatible display manager

The effort needed to actually recompile and get it to run is below minimal(1-2 lines of code per 10th source file?). If it already runs on consoles, then its JUST to recompile it.

---

### Post by beastrace91 on 2009-11-21
> **Aayu said:**
> I'd be worried about their stability and performance.  Games (even native ones from Aspyr) run like molasses, Sim City 4 is a prime example of a 5 year old native OS X game running poorly on my 2008 iMac, so if a company did a quick and dirty to Linux, would anyone actually WANT to play it?

That just sounds like bad code/hardware (last I checked Macs didn't have the greatest nVidia cards out there). I think for instance in my system can run Crysis under Cedega it can handle just about anything that is natively written for the operating system... Also have you played Savage2/HoN Beta? They both have pretty decent graphics and perform just fine under Linux

Regards,
~Jeff

---

### Post by Sindwiller on 2009-11-22
> 3. OS X is running a X11 compatible display manager

No it doesn't? That's why you have to run your own Xserver if you want to use native X11 apps under OS X you know.

> The effort needed to actually recompile and get it to run is below minimal(1-2 lines of code per 10th source file?). If it already runs on consoles, then its JUST to recompile it.

Ask all those FOSS developers who run Linux and Windows but have no Mac machine why they can't port it to OS X despite it being *so easy* that they wouldn't even need an own OS X machine.

---

