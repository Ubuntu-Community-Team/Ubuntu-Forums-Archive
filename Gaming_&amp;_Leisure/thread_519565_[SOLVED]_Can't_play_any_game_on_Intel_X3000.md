---
title: "[SOLVED] Can't play any game on Intel X3000"
date: 2007-08-07
forum: Gaming &amp; Leisure
---

### Post by mysticmatrix on 2007-08-07
I have a DG965RY motherboard having a integrated Intel X3000 IGP.
 I am still unable to play any game on my PC, either native or through Wine.
 Penumbra Demo shows the intro movies and then freezes at start of game and I have no other option than to reboot.
 Similarly MaxPayne demo also doesn't starts up and quits complaining
> err:quartz:GraphBuilder_AddSourceFilter Load (80070003)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0xa72268) : stub, simulating 64MB for now, returning 64MB left
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.
 Strangely, MaxPayne runs when I disable direct rendering ( by not loading DRI module of xorg.conf). But then performance is poor( about 2 FPS).
  Conter Strike:Condition Zero also causes a freeze, requiring a hard reboot.
  
  I am attaching output of glxinfo and also my xorg.conf.
---------------------------------------------------------------------------------------------------
Hardware: Intel Core 2 Duo 1.86GHz, Intel DG965RY mobo, 250 GB sata2 HDD Segate, 1 GB ram(single DIMM), Ubuntu Feisty.

  Please ask if I can provide any other info.

EDIT: Was able to run Crash Team racing on PSX Emulator though.

---

### Post by gwoodard on 2007-08-07
Ubuntu gaming and onboard (intel or amd) video cards are like water and oil (they don't mix) 

        I had similar trouble and got a video card (Nvidia Geforce 6200a) not the newest but very good with gaming, good price too. I am not trying to sell anything, get a video card, but read into other forums about that.

---

### Post by cogadh on 2007-08-07
The problem is the open source Intel drivers suck, so its not just a problem on Ubuntu, but on any Linux platform.

---

### Post by mysticmatrix on 2007-08-08
Well I was able to play Tremulous and Nexuiz(at medium setting) though. I guess there would exist a way to make those other game work.

As for a card, I plan to buy Nvidia card, but I have to wait till next year. :(

---

### Post by gwoodard on 2007-08-08
Good Planning then

---

### Post by Artemis3 on 2007-08-08
Did you tried installing the package xserver-xorg-video-intel ?

If you have an intel card, this is the first thing to do. xserver-xorg-video-810 (and 915resolution) are obsolete and should be uninstalled.

The proper name in xorg.conf for the driver section is intel instead of i810.


Test games like neverball, tremoulous or openarena (0.7 from getdeb).
Try not to use compiz & friends as you might hit a bug when trying to playback video. Hopefully those things will be fixed in gutsy...

---

### Post by hikaricore on 2007-08-08
Artemis: If you're talking about the BLUE block in video playback, this intel issue has been around for basically ever.
This is a limitation of the hardware + the drivers IMHO.

It can be gotten around by simply using another video output driver in your media player, but depending on the hardware may skip alot and the sound may studder.

---

### Post by mysticmatrix on 2007-08-10
Artemis 3, as I mentioned I can play Tremulous, Tuxracer, and OpenArena quite well using i810 drivers. Also changing the drivers to intel had made no gains for me.
What I wanted is to play some games with wine, which I was able to do on my old ATI RAdeon 9200. And yes those games run better on my hardware(ofcourse in Windows though).
Hikaricore, you are true in fact and this vidoe problem with compositing have been around for users of AIGLX in ATI cards and Intel IGP. This can be worked around by using X11 drivers, and I have never seen any sort of slowdown, even in HD content, by using X11 drivers.

I think the main problem here is the attitute of the community(wine, ubuntu, gaming) towards integrated graphics and they would rather say that your hardware sucks than to offer a solution(which most probably would be to buy a Nvidia card).

Artmis3 has correctly pointed out that there is a vidoe playback bug, and I personally garuntee you that it will not be fixed in Gutsy(it has not been done in Alpha 3 atleast), as most Nvidia and ATI users can simply switch to XGL, and who cares about IGP guys?

---

### Post by hikaricore on 2007-08-10
> **mysticmatrix said:**
> I think the main problem here is the attitute of the community(wine, ubuntu, gaming) towards integrated graphics and they would rather say that your hardware sucks than to offer a solution(which most probably would be to buy a Nvidia card).

and who cares about IGP guys?

The biggest problem here is that thousands of computers are still being created and released with integrated chipsets that Intel no longer maintains drivers for on the Linux side of things.
They stopped development on them if I'm not mistaken 2 years ago or more.  And these systems are still being sold.  Community volunteers picked up the project, but there's only so much you can do with badly made drivers.

User X comes along and decides to use to use Ubuntu (or any other Linux distro) with his integrated Intel video chipset that "Works just fine in wind0ze XP you [insert obsenity or Linux bashing here]" and this happens atleast 2 dozen times per month **just in the gaming section alone**.  This leads to similar people asking the same questions, then getting frustrated with Linux/Ubuntu because their beloved Intel chipset just isn't working like it always has.  Insert a few more rants and you get a general dislike of the subject in the community.  I care about the integrated folks, and I know a good quarter of IGP users are able to use their system/play games just fine, but those aren't the users we hear about on a daily basis, we hear about user X and about how stupid we all are for using Lunix.

I hope I've made a valid point.

---

### Post by mysticmatrix on 2007-08-10
Hikaricore, point accepted. Also I would emphasise on point that I would remain on Ubuntu and Linux come what may happen. My computer is a custom build and cheap PC (under 820$). I know I can't expect much from it. As for my chipset, it was released just last August.
 As for me, this chipset is no beloved for me( I can do lot of intel bashing on their driver support if you ask for), but if you say; 
> They stopped development on them if I'm not mistaken 2 years ago or more. And these systems are still being sold. Community volunteers picked up the project, but there's only so much you can do with badly made drivers
; then intel should be penalised for wrong information to public.
This is from Wikipedia ([http://en.wikipedia.org/wiki/Intel_GMA#Linux](http://en.wikipedia.org/wiki/Intel_GMA#Linux))
> Intel has had a long history of producing or commissioning open source drivers for its graphics chips, with all chipsets dating back to the i810 having open 2D and 3D drivers for Linux. It is the only major graphics hardware vendor to do so: for an analysis by company see Graphics hardware and FOSS.
In August 2006, Intel added support to the open-source X.Org/XFree86 drivers for the latest 965 series that include the GMA (X)3000 core.[18] These drivers were developed for Intel by Tungsten Graphics.

I also believe my drivers are fine(and also not upto the mark), come on I' m able to play Tremulous, Nexuiz, etc at medium setting. What I'm hurt is to get responses like to 'buy a Nvidia card'. If no one has any answer, don't post anything. I would rather happy to know that anyone can't answer than to suggest that no one will do anything except to suggest to 'buy a Nvidia card'.


EDIT: I would also suggest to add a sticky suggesting state of driver support of Intel GMA on Linux so that users can understand the amount of performance they can expect out of their hardware.

EDIT: Amazing that I found this on [www.intellinuxgraphics.org](www.intellinuxgraphics.org).
 > "Intel's commitment to providing high-quality drivers
that meet the needs of the mobile Linux community 
is second to none."
Matthew Garrett, Ubuntu Mobile Linux Engineer. That is seriously dumb. The drivers are not atleast of High Quality, either on Linux, Mac or Windows.

---

### Post by cogadh on 2007-08-10
I hate to break it to you, but "buy an Nvidia card" is actually a legitimate solution. Any Nvidia-based graphics card will work 100 times better than your IGP, mainly due to the fact that Nvidia provides incredibly good and robust drivers for their cards that far exceed anything that the open source Intel drivers can do. You could get a cheap card for less than $50 today and all your graphics problems would go away.

---

### Post by hikaricore on 2007-08-10
cogadh: Not to mention the IGP bogs down the system CPU, RAM, and FSB.

mysticmatrix: 
> second to none

Yes first comes none, which means you = SOL.
Second come Intel drivers which mean you = Ok it kinda works.  ^_^

lol

> My computer is a custom build and cheap PC (under 820$)

Custom build as someone made it for you?  Or you did it yourself?

[My recent custom build cost me about 225$]("http://ubuntuforums.org/showpost.php?p=3136346&postcount=5")

I still need to buy a video card, but even with that my grand total will be about 400$.
It's actually a very nice system that I'm considering a decent cooling system and this processor for: [http://www.newegg.com/Product/Product.aspx?Item=N82E16819103773](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103773)

---

### Post by mysticmatrix on 2007-08-11
Well I meant custom build as in to buy all components, get a screwdriver and assemble it yourself. As this was my first PC, I have included price of monitor, DVD drive, speakers, Mobo, Keyboard/Mouse, and what ever I bought.

So I guess final verdict was to buy a card, and guess that solved my problem and I can see that IGP's can be added to section of no Linux/Windows/Mac support for even basic gaming. :(

---

### Post by cbsim on 2007-08-17
> **cogadh said:**
> The problem is the open source Intel drivers suck, so its not just a problem on Ubuntu, but on any Linux platform.

Totally agree. :)

---

### Post by crumja on 2007-08-18
Mmm, the drivers are some of the best you'll get in the OSS world. Support is constantly being updated for new cards, bugs are being fixed and features are being added. Just check the git log for details on the driver.

As for your issue, I would try turning off composite and AIGLX first and using the Intel drivers as was previously said. Maybe you can even compile them from the repo.

---

### Post by jacob01 on 2007-08-18
w2ow i am having the exact same problem and i have heard the same thing about buggy driver

its kinda frustrating that old 3-4 year old video cards can at least run games that a new card cant eaven run

are there going to be any better driver when gutsy comes out or do i have to get a new card to play counter strike

---

### Post by mysticmatrix on 2007-08-18
> **crumja said:**
> 
As for your issue, I would try turning off composite and AIGLX first and using the Intel drivers as was previously said. Maybe you can even compile them from the repo.

I have tried running games with Composite turned off  but it didn't helped.
All native games run fine(Nexuiz, tremulous, TuxRacer, etc) ; it is playing with wine that is causing trouble.
Also I don't know how to build drivers from git repo, also changing driver to 'intel' from 'i810' also did not helped.

---

### Post by jf/ on 2007-08-18
> **hikaricore said:**
> The biggest problem here is that thousands of computers are still being created and released with integrated chipsets that Intel no longer maintains drivers for on the Linux side of things.
They stopped development on them if I'm not mistaken 2 years ago or more.  And these systems are still being sold.  Community volunteers picked up the project, but there's only so much you can do with badly made drivers.

i'm interested to find out more about this issue. Do you have anything to substantiate ur claim of "2 years ago or more"? The way i see it, the 965 chipset seems to be pretty new - and they've (well, according to intellinuxgraphics.org) released opensource drivers already? I'm not openly for Intel here, but I sure do wish for a real proper opensource (graphics or not) vendor. And of course, i would really like to find out the truth of the matter behind this issue here. thanks.

---

### Post by cogadh on 2007-08-19
Intel stopped making linux drivers a while ago (2 years sounds about right) and released the driver code to the open source community. The drivers you got for your card were not actually produced by Intel, they are community produced open source drivers based on Intel's old drivers (and licensed by Intel). Intel is still releasing new chipsets, but they only make Windows drivers for them, they left the Linux support up to the community.

---

### Post by Erik Andrén on 2007-08-19
Cogadh, you're full of it. Stop spreading FUD!

Intel is currently the only hardware vendor that actively supports their open-source driver. 
Check out this site for proof: [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)
Some 3d-elements of the device driver is outsourced to tungsten graphics but it's still Intel that pays the bill.

---

### Post by Miguel on 2007-08-19
Coghad is indeed spreading FUD. It might be true that Intel drivers are not the best out there, but they are, at least, of comparable quality to their windows counterpart. The same cannot be said of ATI's fglrx driver or even their r200 free driver. The latter doesn't have TV-out (well, until last week, that is), due to ATI's love to NDA's and crappy drivers. What the heck, even nVidia can't say their 8000 series cards work in Linux as well as windows. They crash a lot and run certainly slower than in windows, so they are getting closer to ATI in that respect.

One final point. If you buy a system today and put linux into it, the only GPU that will have 3D enabled by default with most features working is indeed an Intel CPU. It might not be the fastest but you know what? It works.

As a sidenote, the OP's issue is probably a wine bug.

---

### Post by jacob01 on 2007-08-19
> **Erik Andrén said:**
> Cogadh, you're full of it. Stop spreading FUD!

Intel is currently the only hardware vendor that actively supports their open-source driver. 
Check out this site for proof: [http://intellinuxgraphics.org/](http://intellinuxgraphics.org/)
Some 3d-elements of the device driver is outsourced to tungsten graphics but it's still Intel that pays the bill.

cogadh is totaly right intel stopped making them and on the intel site it directs you to the open source linux drivers like you pointed out but just because intel has a link to another site doesnt mean they support the driver they left it up to tungston graphics to make the drivers and there is a real flaw in the intel chipset driver. if you would look at the specs of the x3000 [here]("http://en.wikipedia.org/wiki/Intel_GMA#GMA_X3000") you can see how the card in theory should have to power to run games but due to the slow vertex shaders it is unable to run them reliably eaven in windows so it is most likely a combination of bad drivers and just not being built for gaming.

intel has recognized the problem with gaming on the chipset and are trying to improve the performance by making better driver for windows unfortunetly no one that i know of is making drivers to counter this problem for the linux users

i also run the x3000 graphics and like what the guy said, he can run native game but not verry good i could hardly play enemy territory on low settings an that game is pretty old
but what i believe is the weirdest thing of all is that i can run beryl really good, without shutter and still get pretty good frame rates and looks really smooth

check out wikipedia it explains why games arent to good [here]("http://en.wikipedia.org/wiki/Intel_GMA#GMA_X3000")

---

### Post by Miguel on 2007-08-19
From that very wikipedia article:
[quote=Wikipedia]
Linux

Intel has had a long history of producing or commissioning open source drivers for its graphics chips, with all chipsets dating back to the i810 having open 2D and 3D drivers for Linux. It is the only major graphics hardware vendor to do so: for an analysis by company see Graphics hardware and FOSS.

In August 2006, Intel added support to the open-source X.Org/XFree86 drivers for the latest 965 series that include the GMA (X)3000 core.[19] These drivers were developed for Intel by Tungsten Graphics.[20]

In May 2007, version 2.0 of the driver (xorg-video-intel) was released, which added support for the 965GM chipset. In addition, the 2.0 driver added native video mode programming support for all chipsets from i830 forward. This version added support for automatic video mode detection and selection, monitor hot plug, dynamic extended and merged desktops and per-monitor screen rotation. These features are built in to the X.Org 7.3 X server release and will eventually be supported across most of the open source X.Org video drivers.[21] Version 2.1, released in July 2007, added support for the G33, Q33 and Q35 chipsets.[22]

As is common for X.Org drivers on Linux, the license is a combination of GPL (for the Linux kernel parts) and MIT (for all other parts).[23]
[/quote]

---

### Post by jacob01 on 2007-08-19
intel may support the people who make the drivers but they still leave it up to some one else to make the driver 
you cant call up intel and ask for linux assistance they would direct you some where else the only linux support from intel is a director to the linux  intel linux graphics web site

and from the quote you pulled from the wikipedia site 

"In August 2006, Intel added support to the open-source X.Org/XFree86 drivers for the latest 965 series that include the GMA (X)3000 core.[19] These drivers were developed for Intel by Tungsten Graphics.[20]"

is handing something off to some one else really support?
well i guess they supported the chipset by getting some one else to make it for them 

if anything tungston graphics added support for the chipset not intel

yea they handed it of to tungston graphics   so i dont see what your point is

---

### Post by cogadh on 2007-08-19
Hello, did you even read the Wiki article you posted? The drivers were made by **Tungsten Graphics**, not Intel. Tungsten is a company that produces and supports open source drivers and applications. They are major contributors to DRI, Mesa, Blockbuster, Chromium and the Radeon OpenGL drivers. Company founder Brian Paul is actually the guy who created Mesa. The only thing Intel did was co-fund the initial driver project, they didn't actually do any of the development themselves. Hell, the intellinuxgraphics.org site isn't even an Intel-owned domain.

The next time someone accuses me of spreading FUD, they really should check their facts first. I did before I posted.

---

### Post by jacob01 on 2007-08-19
yea you are right in that intel pay x amount of money to get another guy (Tungston Graphics) to support their chipset

but is that really support?

---

### Post by Miguel on 2007-08-19
It is more support than I will ever get from ATi for my card (an old one, a Mobility Radeon 9600 pro turbo).

However, if you consider Intel's position negative, I suppose you actually don't think that governments pave roads, do you? I mean, they contract third party companies to build it for them. Or turkish F-16's are turkish and not IP of Lockheed Martin.

It is probably true that Intel's support is not as good as it could, but calling them on their linux support and then recommending a ***new*** nVidia card, whose 8000 series support is nearly ATI-like is funny to say the least. Of course, you could recommend an ATI card that runs half as fast as in windows (if it works, no hypermemory and no HD2000 in linux yet).

If Intel pays the development of their linux driver and provides Tungsten Graphics with the specs under no NDA, then they are at least a B citizen for me. Heck, it is possible that the TG folks are actually better at writing drivers than intel.

---

### Post by jacob01 on 2007-08-19
> **Miguel said:**
> It is more support than I will ever get from ATi for my card (an old one, a Mobility Radeon 9600 pro turbo).

However, if you consider Intel's position negative, I suppose you actually don't think that governments pave roads, do you? I mean, they contract third party companies to build it for them. Or turkish F-16's are turkish and not IP of Lockheed Martin.

It is probably true that Intel's support is not as good as it could, but calling them on their linux support and then recommending a ***new*** nVidia card, whose 8000 series support is nearly ATI-like is funny to say the least. Of course, you could recommend an ATI card that runs half as fast as in windows (if it works, no hypermemory and no HD2000 in linux yet).

If Intel pays the development of their linux driver and provides Tungsten Graphics with the specs under no NDA, then they are at least a B citizen for me. Heck, it is possible that the TG folks are actually better at writing drivers 
than intel.

yea i doubt that ati will produce a new driver for your 4 or so year old card maybe a couple minor bugs. i wouldn't compare the support of a 4 year old  gpu that is made by a company who is known for having bad support for its linux drivers to a new gpu that the company is still trying to get the windows drivers straightened out. its ati's fault they have such shity support and drivers 

the thing is that the 8800 drivers are just going to improve and you ati drivers are not since it is so old.

if intel was better at writing linux drivers intel most likely wouldn't have gotten TG to do it for them Tg is known more for its open source driver for linux and other operating systems than intel

we are trying to provide help and support not be fair to the gpu companies

wow Lockheed martin lol nice one your funny one they make aircrafts not pave raods lol nice (think a bit next time) maybe you could say hmm... the department of transportation,  you know just a suggestion but you know i got a good laugh out of it.

that makes no sense at least Tungston Graphics makes open source driver

---

### Post by jacob01 on 2007-08-19
some guy:
"It is probably true that Intel's support is not as good as it could, but calling them on their linux support and then recommending a *new* nVidia card, whose 8000 series support is nearly ATI-like is funny to say the least"

wow you think we are stupid

we are not intel nor are we trying to promote a specific company we are here to help each other in in the currently nvidia has better support

---

### Post by Miguel on 2007-08-20
> **jacob01 said:**
> yea i doubt that ati will produce a new driver for your 4 or so year old card maybe a couple minor bugs. i wouldn't compare the support of a 4 year old  gpu that is made by a company who is known for having bad support for its linux drivers to a new gpu that the company is still trying to get the windows drivers straightened out. its ati's fault they have such shity support and drivers 

I don't. Furthermore, the issue doesn't affect only my card. It affects **all** R300, R400 and R500. In some way, it also affects R600, since these don't even work. When a X1950 XTX isn't able to hit 60 FPS in linux when [Windows 1280x1024 4xAA 8xAF ultra quality averages 101 FPS...]( http://www23.tomshardware.com/graphics_2007.html?modelx=33&model1=723&model2=722&chart=287) well, something is very wrong.

> 
the thing is that the 8800 drivers are just going to improve and you ati drivers are not since it is so old.


I hope so for a 300$ hardware piece. I also wouldn't discard ATI drivers improving.

> 
if intel was better at writing linux drivers intel most likely wouldn't have gotten TG to do it for them Tg is known more for its open source driver for linux and other operating systems than intel


Then it isn't that bad that it's TG that made the drivers.

> 
we are trying to provide help and support not be fair to the gpu companies


That one is certainly true. Although some fairness is always welcome. In any case, this might still be a wine bug, since his card works OK with native games.

> 
wow Lockheed martin lol nice one your funny one they make aircrafts not pave raods lol nice (think a bit next time) maybe you could say hmm... the department of transportation,  you know just a suggestion but you know i got a good laugh out of it.

that makes no sense at least Tungston Graphics makes open source driver

I think you misunderstood me. I don't know if Lockheed Martin paves roads. I do know that they make aircrafts. What you might not know is that they also license aircraft building. Some examples are Turkey and Korea for the F-16. Heck, in Japan they've got a similar version called Mitsubishi F-2. Furthermore, the four initial viper users in Europe (Denmark, Belgium, the Netherlands and Norway) have some kind of license that allows them upgrades and similar things. Would you go as far as saying "those vipers have nothing to do with Lockheed Martin"?

Finally, no, I don't think you are supid. I honestly believe we have different opinions on what support is, especially in the nVidia case. I also honestly believe that nVidia's support can be called support, while AMD's doesn't deserve to. But I'd rather have an open-source driver. The situation with ATI 8500 cards a few years ago would be nice, with some open-source drivers (built from specs) and a proprietary driver that has some more punch.

---

### Post by jacob01 on 2007-08-20
ok i just submitted a bug report on the intel website for the intel linux drivers for the x3000 and the g965 chipset so if they do provide any support i will let you guys know hopefully they will help

---

### Post by jacob01 on 2007-08-20
wow is support really an automated message giving you information that you diddnt ask for i asked for linux  not xp

  
 
Thanks for contacting Intel Customer Support 
 
Related Resources (Graphics)
Other helpful product-related links.

Intel® Graphics Product Support 
Driver Downloads 
Identify Your Intel® Graphics Controller 



An automated search of our document library has identified the following solutions which might answer your email. 

You can view these solutions now by clicking on a document title below or by requesting to have the information sent to you by email. After reviewing these solutions, if your question was not answered, please use the escalate option at the bottom of the page.

Intel received the following:

"Intel(R) 82G965 Graphics and Memory Controller Hub (GMCH) Email Support Request i have the intel g965 when i launch a game or another graphical program the drivers lock up my system Linux"


 
These links are based on the information received:

Game Playability on Windows* XP 	E-mail this doc 
Online Crash Analysis (OCA) Resources - Graphics 	E-mail this doc 
OpenGL* Support 	E-mail this doc 
GMA X3000/X3100 for support hardware T&L and vertex shaders 	E-mail this doc 
What is High-Definition Multimedia Interface (HDMI)? 	E-mail this doc 
Game Troubleshooting 	E-mail this doc 
Diagnostic Report 	E-mail this doc 
Support for hardware transform and lighting (T&L) 	E-mail this doc 
DirectX* support 	E-mail this doc 
Identifying Your Intel(R) Graphics Controller 	E-mail this doc 

After reviewing these documents, do you still need help? You can escalate your question to a technical support representative. 

wow and the links i tried and they bring met to a page where it says your camplaint has been filed what complaint wow so much for support
why did they eaven ask what os i used and what kernal if they are going to give me information for xp and other operating systems other than the one i specified

wow nice support
now i going to try the technical support rep

---

### Post by jacob01 on 2007-08-20
i have reached a conclusion, intels email support sucks

---

### Post by mysticmatrix on 2007-08-20
Enough of all this!!!
This thread has really became a blame game instead of anyone trying to pin down where the problem is......

Do anyone that says that problem is with Intel drivers know what exact problems is(Like they haven't implemented a specific OpenGL extension that wine desperately needs)

Or that wine has missed something which is different in Intel from ATI/Nvidia that makes my games crash?

Or my hardware is crappy enough and will never be able to run that game???

Guessing by fact that games based on cube engine are just playable shows that my hardware is capable of running games!!! Believe it or not, some games can be played with IGPs. 

Also few windows games like Age of Empires 2 is playable in wine(Yes I know that's an REALLY old game, but I have seen Counter Strike 1.6 running fine on TNT2).

Now don't feel I am looking for answers, as perfect answer has already been imposed on me, BUY A NVIDIA instead of expecting your problems to be solved.

---

### Post by jacob01 on 2007-08-20
> **mysticmatrix said:**
> Enough of all this!!!
This thread has really became a blame game instead of anyone trying to pin down where the problem is......

Do anyone that says that problem is with Intel drivers know what exact problems is(Like they haven't implemented a specific OpenGL extension that wine desperately needs)

Or that wine has missed something which is different in Intel from ATI/Nvidia that makes my games crash?

Or my hardware is crappy enough and will never be able to run that game???

Guessing by fact that games based on cube engine are just playable shows that my hardware is capable of running games!!! Believe it or not, some games can be played with IGPs. 

Also few windows games like Age of Empires 2 is playable in wine(Yes I know that's an REALLY old game, but I have seen Counter Strike 1.6 running fine on TNT2).

Now don't feel I am looking for answers, as perfect answer has already been imposed on me, BUY A NVIDIA instead of expecting your problems to be solved.

i found out why and i posted it in one of my earlier posts

the chip doesn't even perform well in widows. the reason why it doesn't perform well in games is it has a slow vertex sharers which makes it incompatible with some games. this explain why we can play older games like enemy territory which don't require as much or any vertex shader this includes. the card which have the problem are the intel gma x3100 and x3000

so it is more of a hardware bug

but intel is working on trying to improve the drivers to get the most out of the x3000

i havent heard if they are trying to improve the linux driver

sorry if you could not find it in the other posts

---

### Post by jacob01 on 2007-08-20
i am going through the same thing and im going to give up and get a new card since people will never get reasonable performance out of this igp even with the best drivers because it is a hardware issue

---

### Post by Miguel on 2007-08-20
> **mysticmatrix said:**
> Enough of all this!!!
This thread has really became a blame game instead of anyone trying to pin down where the problem is......


Sorry. I'm one to blame for that.

> 
Do anyone that says that problem is with Intel drivers know what exact problems is(Like they haven't implemented a specific OpenGL extension that wine desperately needs)

Or that wine has missed something which is different in Intel from ATI/Nvidia that makes my games crash?

Or my hardware is crappy enough and will never be able to run that game???


Max Payne is a DX 8.0 game. Thus, your hardware should be able to play it under windows without problems. Even fast. The error you put makes reference to memory. Could you check the BIOS settings for your graphics card? Maybe it's put to minimum use of shared memory, and that's why Max Payne ain't working. 

On the other hand, if you are referring to [this Penumbra](http://penumbra-overture.com/), it is quite modern. I suppose you are running the linux demo. In this case, it might well be what you said of a missing OpenGL extension. In any case, requirement of Radeon 8500/GeForce 3 class of cards suggest the use of OpenGL 1.5 (DX8 class), and thus misleading me.

> 
Guessing by fact that games based on cube engine are just playable shows that my hardware is capable of running games!!! Believe it or not, some games can be played with IGPs.

I know. I've played cube and frozen bubble on an intel 855 IGP. And believe it or not, my next laptop wil surely have an intel IGP. Having a dedicated GPU is too much of a compromise, and too much of a hassle for a laptop.

I'll try to do some research, especially on the Penumbra part, since I believe your hardware should run Max Payne.

PS: I believe your card is comparable to my ATi Mobility 9600.

---

### Post by Miguel on 2007-08-20
I found the following [here](http://frictionalgames.com/forum/showthread.php?tid=208):

[quote=Fictional Games Forum FAQ]
**The game wont run on my Intel graphics card?**
At the moment NO Intel cards are supported or have been reported functioning. This include GMA 900: 910GL, 915G, 915GL, 915GV. GMA 950: 945G, 945GZ. The new GMA 3000/GMA X3000: Q963 Express, Q965 Express, G965 Express are unknown if they run the game or not.[/quote]

I suppose this might have to do with some OpenGL 2 extensions, but I'm not sure.

---

### Post by mysticmatrix on 2007-08-20
Thanks Miguel for some serious thoughts on my topic.
I have maxed out my shared memory to 384 MB from BIOS, if that was what you asked.

One strange fact is that Max Payne runs under Wine when I turn direct rendering off, but it is too slow(1 FPS). So there is some problem with Wine I guess.

As for windows part, the hardware is quite running many games quite fluidly. See this
[http://blogs.intel.com/technology/2007/08/gaming_on_integrated_graphics.html](http://blogs.intel.com/technology/2007/08/gaming_on_integrated_graphics.html)

And yes it is comparable to ATI Mobility 9600 where memory bandwidth goes, but supports Shader Model 3 completely.

And yes, I was referring to same penumbra.

And jacob01, guess what, Counter Strike 1.6 requires no vertex shaders(runs on TNT2). 

And linux drivers are being improved, as I got an update last month which enabled OpenGL 1.4 from previous 1.3.

---

### Post by jacob01 on 2007-08-20
i was talking about counter strike source sorry if i didn't specify that i know from experience counterstike source doesn't work

" As for windows part, the hardware is quite running many games quite fluidly. See this
http://blogs.intel.com/technology/20..._graphics.html" 

of coarse intel is going to say it runs games good they are the ones trying to sell it

if you read the page you posted  they are using the intel drivers which use the new xp driver which enable hardware vertex shader and it is going to be a while before any linux driver will suport that

---

### Post by mysticmatrix on 2007-08-20
> **Miguel said:**
> I found the following [here](http://frictionalgames.com/forum/showthread.php?tid=208):



I suppose this might have to do with some OpenGL 2 extensions, but I'm not sure.

Penumbra is up and running on my G965 under windows.(the demo version).

> " As for windows part, the hardware is quite running many games quite fluidly. See this
[http://blogs.intel.com/technology/20..._graphics.h](http://blogs.intel.com/technology/20..._graphics.h) tml"

of coarse intel is going to say it runs games good they are the ones trying to sell it

jacob01, I do have some games to play and right now I am playing Far Cry and COD2 on my computer.(I Love COD2). Try somethings yourselves before wiping off any claim with your prejudices.

---

### Post by Miguel on 2007-08-20
> **mysticmatrix said:**
> Penumbra is up and running on my G965 under windows.(the demo version).

Then I have to eat all my words and say that it's a driver "feature". I'd love to test your card under gutsy, with mesa 7.0 and intel driver 2.2.1 (Feisty's is 2.0 beta). The thing that pisses me off is that GMA950, which is indeed about half as fast  as X3000 runs beryl OK, and seems to run some games OK. Furthermore, Windows tests seem to indicate some not-so-old games run OK. Well, at least we've got the source of the drivers.

If your card runs Far Cry there is absolutely no reason why it shouldn't run Max Payne. Wine or otherwise. I'll do some further searches.

---

### Post by jacob01 on 2007-08-20
sorry man i was trying to help and i guess i was wrong
sorry about that

btw what driver are you using

ill list all the games i have tried
css
half life
bejuled- i dont think is compatable with wine
halo pc
and pretty much gave up there i got so mad just with counterstrike alone
enemy territory i could hardly play on low setting
tremules or somthing like that

then every time i try to get help people eithor don't reply or take the easy way out and say buggy drivers


i guess it might not have buggy drivers but  why isnt any game working very good when beryl works flawlessly

---

### Post by jacob01 on 2007-08-20
any game i atempt to play just crashes my system and i have been looking for the solution for 4 monthes i talked to the wine developers multiple times dell to make sure i do have the intel g965 with the intel x3000 and ubuntu irc and every one says buggy driver and such now you are playing these games what did you do to make it work?

dell messed up and said that they sent me an nvidia geforce 6000 le and i called them to see what it was and they said it was the g965 so unless i am not using the g965 i dont know whats up have any ideas

man i have been so frustrated and pretty much gave up until i get a new card since no one is able to help me

 and now every thing i have said i am questioning

---

### Post by mysticmatrix on 2007-08-21
> **Miguel said:**
> Then I have to eat all my words and say that it's a driver "feature". I'd love to test your card under gutsy, with mesa 7.0 and intel driver 2.2.1 (Feisty's is 2.0 beta). The thing that pisses me off is that GMA950, which is indeed about half as fast  as X3000 runs beryl OK, and seems to run some games OK. Furthermore, Windows tests seem to indicate some not-so-old games run OK. Well, at least we've got the source of the drivers.

If your card runs Far Cry there is absolutely no reason why it shouldn't run Max Payne. Wine or otherwise. I'll do some further searches.


Migul and jacob01, I think there has been some misunderstanding.
I am playing COD2 and Far Cry under **Windows XP**(not in wine).

And jaob01, I'll confirm that Counter Strike and many other games do lock down the system when I try them under ***Wine***. Also jacob01, I am running Tremulous at high settings under 800x600 and in medium settings under 1024x768.** and it is preety smooth(65 FPS average) All other native linux games** are also running good(like Saubertrun, Open Arena,[COLOR="Red"]Unreal Tournament 2004[/COLOR] etc).

Only game I've got sucessfully running under Wine is Age of Empires 2.

And the more I think, more do I am suspected to believe that trouble is with Wine, and not Intel.

---

### Post by mysticmatrix on 2007-08-21
Although might not be relevant, I would also list games that were playable under **Windows**:

1) Far Cry [ 800x600 Medium setting 40 FPS] (became playable with newest 14.31 drivers for XP from Intel)
2) COD2   [ 800x600  Semi-High setting 40 FPS ]
3) POP:Sands of time [800x600 HIGH setting 40 FPS]
4) Counter Strike Source[1024x768 HIGH setting 2x AA 4x AF 30 FPS]
5) and many other older titles.

Games not running:
1) Rainbow Six Vegas
2) DiRT Demo
3) Spider Man 3

---

### Post by Miguel on 2007-08-21
> **jacob01 said:**
> any game i atempt to play just crashes my system and i have been looking for the solution for 4 monthes

Jacob, when you say that every game crashes your system, does that apply to native games like, let's say, torcs, tremulous, open arena, scorched3d, frets on fire, forzen bubble or supertux? Does it happen with Quake3 (I hope the demo is still available)? By the way, questioning yourself and trying to find the answer shouldn't make you feel bad. It's the way science progresses.

**@ Mysticmatrix**
Thanks for your clarification. I already supposed you were talikg about Far Cry on windows basically because of COD2 (whose demo struggles to run perfectly smooth on a friend's GeForce 6800GT). Your settings and performance of Counter Strike Source simply amazed me.

[quote=Mysticmatrix]
Games not running:[list=1]
[*]Rainbow Six Vegas
[*]DiRT Demo
[*]Spider Man 3
[/list]
[/quote]

I'm not surprised with DiRT not running. From what I've read it's a huge resource hog, and won't run OK unless you have hardware in the 8800 class. I don't know about the others.

An example of game-driver conflict is actually ATi's fglrx with Torcs. In a series of tracks, although the game runs OK, it will crash as soon as the last car gets to the finish line, with an invalid glibc pointer message. It seems to be a similar case with Penumbra, which refuses to start on the open source radeon driver.

> 
And the more I think, more do I am suspected to believe that trouble is with Wine, and not Intel.


I'm with you on this one. The middle ground (the right one?) would be that Wine's calls for vertex shaders are incompatible with the feisty intel driver.

---

### Post by jacob01 on 2007-08-21
> **Miguel said:**
> Jacob, when you say that every game crashes your system, does that apply to native games like, let's say, torcs, tremulous, open arena, scorched3d, frets on fire, forzen bubble or supertux? Does it happen with Quake3 (I hope the demo is still available) 

yea i can run most native games like tux racing (although it locked up my system yesterday while switching windows) and i can play open arena pretty good but the enemy territory tremulous run so bad on high setting and is still nearly unplayable on low
i havent tried quake 3 because i about gave up on it

but i can play juast about all gams from the repository

another glitch i found it when i exit enemy territory or other full screen games it some time messes up my screen resolution

---

### Post by mysticmatrix on 2007-08-21
> **jacob01 said:**
> yea i can run most native games like tux racing (although it locked up my system yesterday while switching windows) and i can play open arena pretty good but the enemy territory tremulous run so bad on high setting and is still nearly unplayable on low
i havent tried quake 3 because i about gave up on it

but i can play juast about all gams from the repository

another glitch i found it when i exit enemy territory or other full screen games it some time messes up my screen resolution

This is strange as I was able to play tremulous at medium settings at 60FPS or so and was quite playable.

Miguel, can I update my drivers under Feisty by some way?
Also, how can I upgrade to Gutsy from here in Feisty to test new drivers? My present driver version is 2.1.9.94(This is what synaptic says)

---

### Post by Miguel on 2007-08-21
> **mysticmatrix said:**
> This is strange as I was able to play tremulous at medium settings at 60FPS or so and was quite playable.


Maybe one of you is running compiz/beril/compiz-fusion, which may not go well with tremulous. Torcs and compiz-fusion don't like each other, for example.

> 
Miguel, can I update my drivers under Feisty by some way?
Also, how can I upgrade to Gutsy from here in Feisty to test new drivers? My present driver version is 2.1.9.94(This is what synaptic says)

I wouldn't advise you to upgrade to Gutsy. I certainly wouldn't. As X.org is really modular, it should be possible for you to get a new driver without upgrading the whole system. Let me have a look at gusty's driver dependencies. Well, you can't install gutsy's intel driver without installing other low-level things. Too twitchy. Will look somewhere else.

---

### Post by jacob01 on 2007-08-21
> **Miguel said:**
> Maybe one of you is running compiz/beril/compiz-fusion, which may not go well with tremulous. Torcs and compiz-fusion don't like each other, for example.

im not running any compiz or any thing i am just using the default window manager

---

### Post by Miguel on 2007-08-21
> **jacob01 said:**
> im not running any compiz or any thing i am just using the default window manager

I'm out of ideas. I have been looking at the build process of a driver and, unless one desperately needed that driver, it's pretty time consuming and tough for the inexperienced. The instructions I found were these: [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

One good thing is that by getting the development packages of X and mesa, one might only need to perform steps 3.3 and 3.4 (note the word *might*, it's because I've never done it myself). And I would only build the drivers. Building my own mesa is something I wouldn't like to do.

It may be possible to open a bug in launchpad requesting intel driver 2.0.0 instead of the 2.0 RC currently in Feisty. It may be considered a bugfix release and would solve some issues.

---

### Post by jacob01 on 2007-08-21
i cant imagine getting verry good performance out of this card eaven in windows so i will most likely get a new card. i was just wondering if it was something easy that i could do to get it working

---

### Post by mysticmatrix on 2007-08-25
Ok Wine version is .9.44 and I'm now getting these errors
```
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33ef10,0x00000000), stub!
err:quartz:GraphBuilder_AddSourceFilter Load (80070003)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0xbea688) : stub, simulating 64MB for now, returning 64MB left
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

```

Does this explains matter any better?

---

### Post by hikaricore on 2007-08-26
FYI, WINE error output is next to useless in most cases.

---

### Post by cogadh on 2007-08-26
"fixme" messages are quite useless, but those "err" messages usually indicate that the driver for your video card doesn't support the functions that Wine is trying to use.

---

### Post by Miguel on 2007-08-27
Does anybody here know if these OpenGL extensions being called are actually part of OpenGL 2.0 (or 2.1)? In that case, it would explain something, as in Feisty only nVidia and ATi's fglrx support OpenGL 2.

---

### Post by cogadh on 2007-08-27
Well, a quick Google search on "wglMakeContextCurrentARB" turned some developer docs related to OpenGL 1.2 and a quick scan through the OpenGL 2.1 SDK docs gave me a headache, but not much else. It looks like that particular extension is *not* a 2.0 extension, but I could be very wrong.

---

### Post by mysticmatrix on 2007-08-27
> **Miguel said:**
> Does anybody here know if these OpenGL extensions being called are actually part of OpenGL 2.0 (or 2.1)? In that case, it would explain something, as in Feisty only nVidia and ATi's fglrx support OpenGL 2.

Well I have mentioned it before and would like to do again.
I am able to run the Game(MaxPayne) under Wine if I turn [COLOR="Red"]Direct Rendering Off.[/COLOR]. But then frame rate is like 1 FPS. 

So extensions are surely present(I believe they are present, I'm no expert), only that something is tricky, either in WIne or my Drivers.

I will give output of glxinfo, if that helps:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_swap_control, GLX_MESA_swap_frame_usage, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965G 4.1.3002 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_point_parameters, 
    GL_ARB_shadow, GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_non_power_of_two, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_logic_op, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, 
    GL_EXT_compiled_vertex_array, GL_EXT_convolution, GL_EXT_copy_texture, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_histogram, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_polygon_offset, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_filter_anisotropic, GL_EXT_texture_lod_bias, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_3DFX_texture_compression_FXT1, GL_APPLE_client_storage, 
    GL_APPLE_packed_pixels, GL_ATI_blend_equation_separate, 
    GL_IBM_rasterpos_clip, GL_IBM_texture_mirrored_repeat, 
    GL_INGR_blend_func_separate, GL_MESA_pack_invert, GL_MESA_ycbcr_texture, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texture_rectangle, GL_NV_texgen_reflection, GL_OES_read_format, 
    GL_SGI_color_matrix, GL_SGI_color_table, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_SGIX_depth_texture, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5a 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
```

---

### Post by st33med on 2007-08-27
I have found that most games don't support Intel GMA cards. BF2? Nope. Half-Life 2? Runs, but stutters, and crashes, even after giving it an option of forcehardwaresync. (BTW, I'm talking about playing games on Windows... Not that it matters, right?)

Integrated cards aren't the best for gaming. If you really want to play games, you might want to ship it to your manufacture to get it upgraded if you have a laptop. If you have a desktop, just buy a good nVidia card, ***NOT*** an ATI card.

---

### Post by Miguel on 2007-08-28
Would [this link](http://ubuntuforums.org/showthread.php?t=494943) help? I can give detailed downgrading instructions if needed. Even from the terminal. In any case, this might be more related to mesa than the X.org driver.

---

### Post by mysticmatrix on 2007-09-04
> **Miguel said:**
> Would [this link](http://ubuntuforums.org/showthread.php?t=494943) help? I can give detailed downgrading instructions if needed. Even from the terminal. In any case, this might be more related to mesa than the X.org driver.

Well miguel thanks for advise. But I guess I'll be waiting till final release of Gutsy itself than screwing up with backports.
Also I tried the Alpha 5 edition(live CD), and as far as desktop effects go, it's even worse than feisty.
I was at least able to play videos, only had a little syncing problem when video was moved(fixed by changing to X11 driver). Under Gutsy, video's simply refuse to run until I switch off Desktop Effects, or apply the X11 fix.

---

### Post by mysticmatrix on 2007-09-27
> **Miguel said:**
> I'm out of ideas. I have been looking at the build process of a driver and, unless one desperately needed that driver, it's pretty time consuming and tough for the inexperienced. The instructions I found were these: [http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

One good thing is that by getting the development packages of X and mesa, one might only need to perform steps 3.3 and 3.4 (note the word *might*, it's because I've never done it myself). And I would only build the drivers. Building my own mesa is something I wouldn't like to do.

It may be possible to open a bug in launchpad requesting intel driver 2.0.0 instead of the 2.0 RC currently in Feisty. It may be considered a bugfix release and would solve some issues.

OK I updated to Gutsy Beta today and have driver version Intel 2.2. Game now runs :guitar: but everything(except menu) is blued up. Will test a little more and give my conclusions

---

### Post by mysticmatrix on 2007-09-27
That thing must be problem in Wine itself.
Playing my counter Strike now :guitar::guitar::guitar::guitar:

Bye Bye WinLoze....

---

### Post by Miguel on 2007-09-30
glad to see Gutsy worked for you!

---

### Post by ImNeat on 2007-10-01
Is there a way to use the intel drivers provided in Gutsy on Feisty?

---

### Post by Miguel on 2007-10-02
You can either compile it by yourself (tough if you also want OpenGL 2), use the one in the link I posted above (no OpenGL 2 there AFAIK) or you can search in google "Apt-pinning". This alows you to use a version of ubuntu but prioritise some packages from another version. Be warned though that the current dependencies of xserver-xorg-video-intel will pull a new libc6 and gcc 4.2 as dependencies.

EDIT: I told you to google apt-pinning because I have never used it myself, so I have no experience.

---

### Post by Ripfox on 2007-10-02
So, how much better is this driver than the 2.0? I have an HPdv6000 with 945gm.

---

### Post by mysticmatrix on 2007-10-02
> **ripfox said:**
> So, how much better is this driver than the 2.0? I have an HPdv6000 with 945gm.

Can't tell about your hardware. These are the difference they made for me

1) I am able to play wine games. :popcorn:
2) Compiz Fusion doesnot works with XV video acceleration. So my hardware is officially blacklisted.

I still use compiz fusion after modifying the startup script, and applying the X11 fix.

For me if you can run wine sucessfully on 945, this might not be a big difference to end user. I don't know anything about technical stuff,though.

---

### Post by Miguel on 2007-10-02
The driver shouldn't make a lot of difference on a 945gm, as the biggest feature of those drivers are improved X3000 and X3100 support.

---

### Post by Ripfox on 2007-10-02
Well poo. I thought I was finally getting a break. :lolflag:

I find that with a little work I can run a lot of games under Wine...but, I have grown tired of messing with it. It seems that every time there is an update either on the game side or Wines side, something breaks.

I would give my left ventricle if I could just play Regnum. (mmorpg addict here)

Wakfu BETTER RUN OR ELSE :lolflag:

---

### Post by peabody on 2007-10-07
I have a 945GM (called an i950 on the packaging for the laptop) and all games in wine work great for me EXCEPT HL2 engine based games.  I'm dying to get this working.  Anybody know if running gutsy fixes this problem for that adapter?

I know I'm hoping for too much probably.  This adapter is listed as having serious issues in Windows.  I guess I can't be expecting to get it to working via Wine if it won't even work most of the time in Windows.  But I'm hoping.

---

