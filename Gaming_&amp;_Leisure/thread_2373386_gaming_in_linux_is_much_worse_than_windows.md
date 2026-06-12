---
title: "gaming in linux is much worse than windows"
date: 2017-10-05
forum: Gaming &amp; Leisure
---

### Post by someoe on 2017-10-05
hi,

my info :
```

Ubuntu 16.04.3

             Memory : 3.8 GiB

          Processor : Pentium(R) Dual-Core CPU E5700 @ 3.00GHz × 2 

            Graphics : Intel® G41 

             OS type : 64-bit

Screen resolution : 1366 x 768 (16:9)
                            1280 x 720 (16:9) 
                            1024 x 768 (4:3)
                            832 x 624 (4:3)
                            800 x 600 (4:3)
Kernel number : 4.10.0-35-generic

```

the problem :

when i was in windows i had a game called "Ancient Warfare 2" and it was higher from my end and i solved this by one of this two solutions :
 
changing my resolution from (1366 x 768) to (1024 x 768) and keeping the quality as (high) or keeping the resolution (1366 x 768) and changing the quality to (low)

but now when i moved to Linux Ubuntu i realized that Ubuntu isn't like windows (doesn't open applications without openGL, because the same game in the same computer opened in windows but didn't respond in Linux) and when i searched the network i found how to force openGL but that didn't help , the game was like this :

completely slow and when i change the resolution to (800 x 600) and the quality to (low) the game the game doesn't speed enough like the game speed in windows , in windows i was lowering the quality or the resolution and start the game without problems but in Linux with lowering the quality and the resolution to the lowest that doesn't help enough , i want to know what is in windows making it like this and is not in Linux.

and i want to know why windows doesn't need to force openGL likewise Linux

Please any help guys because this problem is bothering me Alot. :(

thanks.

---

### Post by ian-weisser on 2017-10-05
Have you brought this problem to the attention of the Ancient Warfare 2 developer(s)? They say on their website that they want to know.

Have you sent them the debug information they need to isolate the problem? They say on their website what they need.

---

### Post by someoe on 2017-10-05
thank you i had asked him and iam waiting for the answer

i want to know why windows don't have to force opengl like Linux because this happens in another games like adventure capitalist (that game have alot of errors :
[https://forum.unity.com/threads/graphics-problem-in-games-made-with-unity.488544/](https://forum.unity.com/threads/graphics-problem-in-games-made-with-unity.488544/)(ancient warfare 2 is an example)

and why windows games runs successfully on windows but worse under wine (in Ubuntu)

---

### Post by QIII on 2017-10-05
Hello!

Wine is not a perfect drop-in for Windows.  In fact, many Windows applications simply do not run at all under Wine.  It doesn't emulate Windows, but provides a compatibility layer for hooking Posix calls in place of Windows APIs.  WineHQ.org has a database with community test reports on various applications.

Also bear in mind that Linux != Windows.  Just because something behaves in some fashion in Windows does not guarantee the same behavior in Linux.  Applications designed for Windows are not designed for Linux.

---

### Post by mastablasta on 2017-10-06
> **someoe said:**
> 
and why windows games runs successfully on windows but worse under wine (in Ubuntu)
because they are designed to run in Windows. if they had the Linux version then it would be another matter. 

also linux can't use DirectX, because it has closed source, so until MS decides to port it to linux we are stuck with OpenGL or directx reimplementations.

wine - to explain it more plainly - tricks the game into thinking it's running on windows. the libraries in it are mostly reverse engineered or they have to be borrowed, since source code for windows libraries are not available.
wine makes system pretend it's running windows, it doesn't emulate it. which is why the performance is not hit as much as if it was an emulator. emulators need plenty of CPU power.

windows games are therefore best enjoyed on the system they were made for (windows). however many games nowadays get a linux version or their devs offer some help with running their game on wine. 

if you would like to play games on linux i suggest a visit to sites such as "Gaming on linux". they offer plenty of information on which game works on linux, which one will work as well as tips and tricks form the users to tame the games on linux.

---

### Post by someoe on 2017-10-06
thank you alot mastablasta,

but i have my main question unsolved :

i was from my young having windows and updating from version to version until i found that my windows is not registered (no one care -_-) so i installed Ubuntu to my computer and i was loving some games in windows , but when i download the linux version of it i find that it's worse than the windows version (i mean ... slower and even don't speed enough when lowering the quality and the resolution) i want to know if directx matters in this situations and if linux running with part of the graphics and games tith the the rest (like %25 to run the desktop and %75 to run the games and applications) because in windows there was no limit for gaming but in linux i found alot of problems like the game "ancient warfare 2" below and the game "ADventure Capitalist" from this thread : 
[https://forum.unity.com/threads/graphics-problem-in-games-made-with-unity.488544/](https://forum.unity.com/threads/graphics-problem-in-games-made-with-unity.488544/) (a question in unity) iam now at the main part of this question and it's the bad gaming on linux (not under wine) and i want to know what causes this (gaming without directx .... i try).

---

### Post by someoe on 2017-10-06
i have searched around the ******************************* internet and i found that :

"DirectX, simply put, is software developed by Microsoft that talks to a  PC's hardware components. Specifically, it's a collection of application  programming interfaces, or APIs, designed to handle tasks related to  rendering 2D and 3D vector graphics, rendering video and playing audio  on the Windows platform."

and from my ( &#865;° &#860;&#662; &#865;°) experience from windows i will tell you the next :

when you run a game that is meeting the (recommended requirements or even the low) the game runs and directx tweak it to work successfully but it making it a bit slow and leave you to change the quality or the resolution if you want the game to look working good but by a low resolution or low quality (they don't care about directx). in linux there's no directx so thersw just openGL , you can run the game just if you meet the opengl requirements and if not the game doesn't open and if you forced the game to open it will act like a successfully working and last version of openGL so you can't do anything to make the game looks like good working game.

this is the [COLOR=#ff0000]TRUE [/COLOR][COLOR=#000000]question :

is there anyway to make linux gaming (not under wine gaming i mean linux games) be like windows (with directx or not but acting like windows), i want to know if linux can be with directx (or any other way to run the games like windows not under wine). a way for linux to run likewise windows in gaming , not playing windows games put llinux games :)[/COLOR]

---

### Post by Perfect Storm on 2017-10-06
It could be that the games in questions are poorly ported to Linux which reflect back to those port the games. I don't know which games you are gaming, but the games I'm using the performance is (almost) the same as in Windows. I have a windows partitions for my Sims 4 :P

---

### Post by kurt18947 on 2017-10-06
I'm not a gamer but I think Steam has done a fair bit of work making their games run natively on Linux.

---

### Post by MikeCyber on 2017-10-07
I use Nvidia and have about the same performance as on Windows. But I guess for Intel you have to make sure to have the latest drivers and Mesa installed.

---

### Post by efflandt on 2017-10-08
Intel integrated graphics (especially older Intel graphics) lacks some GL and GLX features and shares some of your RAM as video RAM, so they are not only slow (especially older), but rob some of your system RAM (which is "sometimes" adjustable in BIOS). On my gaming laptop with hybrid graphics (Intel HD 4600 and Nvidia GTX765M) some graphics benchmarks would run with Nvidia graphics and drivers in Linux, but not run at all on Intel graphics due to missing features. Or in the case of (2) similar dual-core 1.66 GHz laptops with 2.5 GHz RAM from 2006-2007, one with what is now legacy ATI (AMD) X1300 graphics ran minecraft fine in Ubuntu with the default Radeon drivers, but the one with Intel integrated graphics was too slow for minecraft to be playable. In fact I have a Win10 laptop with quad-core Pentium 1.6 GHz (2.4 GHz turbo) with 8 GB RAM and integrated Intel graphics where the old Java minecraft is not playable in Win10 (only 1 to 5 frames per second).

Whether a graphics card would help depends upon the PCI Express (PCIe) version of your graphics card slot. If your PC has PCIe 1.0, modern graphics cards would work, but would be wasted because you will not get full speed out of them. For example when I put my old GTX 550 Ti (PCIe 2.0) or GTX 750 Ti (PCIe 3.0) on an old single core Pentium 3.2 GHz with PCIe 1.0 slot, either card worked, but streaming video had to be throttled to 480p to run smoothly. Both of those cards streamed video at higher resolution on a computer with PCIe 2.0.

I am not familiar with current AMD graphics, but If your graphics card slot is PCIe 2.0, the minimum Nvidia cards should be GTX (not GT) like GTX 750 Ti (60 watt) or GTX 1050 Ti (75 watt) which should have models available that get their power from the PCIe slot and without requiring separate power connection. For best results with an Nvidia card you would want to run a recent nvidia driver package and there is a graphics-drivers ppa if you need a newer nvidia driver than is in packages for your Ubuntu version.

My current desktop is from 2010, but it has a different CPU socket than yours that I was able to upgrade from i5 650 CPU to i7 870 that is a little slower than newer i5. But along with Nvidia GTX 1060 works very well for Linux Steam games.

PS: I recently tried minecraft in 64-bit Ubuntu on that slow laptop that would only run it at 1-5 fps in Win10. In Ubuntu it was actually a playable @ 16-18 fps. But that is a Java game that uses OpenGL anyway (not DirectX), even though Microsoft owns minecraft now. It might be interesting to install Linux Steam and see how that slow laptop does playing Team Fortress 2.

I have used playonlinux, but so far only for the Windows only Steam "Hammer" game map editor for specifically for Portal 2, and to test those maps with Portal 2 in playonlinux. Sometimes the audio would glitch for a while in Portal 2 in playonlinux before it corrected. But Linux Portal 2 and its simple included map editor works fine.

---

### Post by sdsurfer on 2017-10-14
Yeah I've experienced this, there are overall a couple reasons IMHO. The first is the market share, Linux is not where the money is for selling games. The second is because it's so configurable, it is beginning to look like unless it's been updated like "yesterday" it's likely to use libraries that are outdated.

An example, I really gave TBD (The Dark Mod) a good stab, after hours of Google searches to figure out how to resolve missing libraries, the game finally tried to start up only to have an issue with Open GL. Spend another hour or two trying to resolve that, but when it comes to video software, the nuances are very specific and I couldn't resolve it.

I finally gave up and took it as a sign from the universe that I have bigger things to do and shouldn't waste so much time goofing around with games. :-)

---

### Post by denismc on 2017-10-16
> **mastablasta said:**
> because they are designed to run in Windows. if they had the Linux version then it would be another matter. 

also linux can't use DirectX, because it has closed source, so until MS decides to port it to linux we are stuck with OpenGL or directx reimplementations.

wine - to explain it more plainly - tricks the game into thinking it's running on windows. the libraries in it are mostly reverse engineered or they have to be borrowed, since source code for windows libraries are not available. wine makes system pretend it's running windows, it doesn't emulate it. which is why the performance is not hit as much as if it was an emulator. emulators need plenty of CPU power.

windows games are therefore best enjoyed on the system they were made for (windows). however many games nowadays get a linux version or their devs offer some help with running their game on wine. 

if you would like to play games on linux i suggest a visit to sites such as "Gaming on linux". they offer plenty of information on which game works on linux, which one will work as well as tips and tricks form the users to tame the games on linux.

I remember prior to DirectX coming out Windows machines would rely heavily on a thing called WinG for gaming.  I may get flamed for this but i always viewed Wine as similar to how WinG worked.  It's an abstract layer above the hardware.  The farther away you get from the "metal" the slower your performance is going to be.  This is why Microsoft made it a big deal to create DirectX.  It was hugely useful for the gaming field because DirectX was as close to the hardware layer as you were going to get.  And performance skyrocketed.  It also helps that MS is very aggressive in listening to game/hardware developers in figuring out new tricks and additions to push the hardware more.  Since Wine doesn't have that fortune you can definitely expect performance to be significantly slower on a Linux machine.  It's just the way the world works.

---

### Post by mastablasta on 2017-10-17
> **denismc said:**
> It's just the way the world works.

yeah but not the way wine works. wine is a compatibility layer. some thing work better in it than they do in original windows. but only some.

most have no or at least shouldn't have any performance hit. DirectX can be installed in wine. 

the problem is mostly elsewhere. since it is a reverse engineered compatibility layer, not everything is fully compatible. for that reason errors, things that don't work etc. are a norm. in other words only few apps form windows world work with no errors in wine. but the fact that they do is awesome! if Windows opened the source code i am sure we could have a 100 % compatibility withing a few years :)

---

### Post by inerstellar-cowboy on 2017-10-17
I think your assesment is a little unfair.

As a few people said above, it could be that the titles in question are simply not the greatest ports over to linux

my specs are not too much different than yours, but I've been able to get games as graphically intensive as civilization v and xcom up

 I've even been able to run some games on wine

---

### Post by Kris_M on 2017-10-28
When I first started converting to Ubuntu from win7 I tried playonlinux but that was basically hopeless. I tried installing NWN and NWN2 from the disks (wine installed by playonlinux) but it wouldn't play nice with the install. So for these 2 packages I bought the GOG versions and installed them quite easily(same wine). A little googling for hints and playing with wine configs and they run fine. Nvidia  750 GTX Ti. The trick is to find what modules to add to wineconfig.

I also occasionally play Ultima Underworld I and II and so installed DOSBOX and installed them from disk. Stonekeep also runs fine if the CD is in the player, mounted in DOSBOX. Also grabbed some old King's Quest stuff. which played fine.

When I ran into problems I googled - there are many forums out there for GOG and the like, on Linux.

---

### Post by oldrocker99 on 2017-10-30
There **have** been quite a few AAA games released on Steam for Linux: Age of Wonders III, BioShock Infinite, Borderlands 2, Crusader Kings 2, Dominions 4, Empire:Total War, Europa Universalis IV, Pillars of Eternity, Planescape:Torment Enhanced Edition, Civilization V and VI, Civilazion: Beyond Earth, Torment:Tides of Numenera, Tyranny, The Witcher 2, XCOM, Tropico 5, War For the Overworld, Planetary Annihilation: TITANS, Wasteland 2, all of the Half-Life series, Stellaris, Dungeons 3 & 4, Hearts Of Iron IV, Out Of The Park Baseball 17 & 18, Overlord II, and Tomb Raider (not a complete list by any means). There are also a raft of **** indie games.

In other words, you can game very, very well in Linux.

---

