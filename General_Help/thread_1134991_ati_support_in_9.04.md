---
title: "ati support in 9.04"
date: 2009-04-24
forum: General Help
---

### Post by eyezdk on 2009-04-24
Well, now that we got 9.04 out, I am thinking of installing it on my HP laptop. the only thing is, i know i have an Ati Radion card, and last time i tryed it, it was some bad support, and i could not get any games to run. 

Is support for Ati cards got better in 9.04, or is it stil the same thing? 

/eyezdk

---

### Post by hgergo on 2009-04-24
It is much whorse!
The aold ati cards like x200m is not suported by ati!

---

### Post by Eestlane on 2009-04-24
Yeah, if 8.10 worked alright, and you have an older ATI card that latest drivers doesn't support, listed here:
> **Not supported cards:**
ATI Radeon 9500 Series
ATI Radeon 9550 Series
ATI Radeon 9600 Series
ATI Radeon 9700 Series
ATI Radeon 9800 Series
ATI Radeon X300 Series
ATI Radeon X550 Series
ATI Radeon X600 Series
ATI Radeon X700 Series
ATI Radeon X800 Series
ATI Radeon X850 Series
ATI Radeon X1050 Series
ATI Radeon X1300 Series
ATI Radeon X1550 Series
ATI Radeon X1600 Series
ATI Radeon X1650 Series
ATI Radeon X1800 Series
ATI Radeon X1900 Series
ATI Radeon Xpress Series
ATI Radeon X1200 Series
ATI Radeon X1250 Series
ATI Radeon X2100 Series

I suggest you to use 8.10.

Unfortunately I have ATI 9800 Pro, though open-source drivers work quite good, it's not the same as the propietary ones. Of course, trying it won't hurt in case you have some extra partitions to test in.


> AMD **may periodically provide Windows XP and Windows Vista driver updates** (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The **Linux ATI Catalyst&#8482; driver will only be supported in Linux distributions prior to February 2009** for the legacy products listed above.
Not fair!

I would be glad to use NVidia card next time, but if everybody do so, it means the competition weakens and gpus will pricen up.

---

### Post by eyezdk on 2009-04-24
Well, I have ATI mobility Radeon HD 3450 card. and my laptop is only 6 month old or so. so its a newer card. 

I just know, that in 8.10 it workedl like hell

---

### Post by Eestlane on 2009-04-24
Then you should definitely try out the new Ubuntu

---

### Post by bebox on 2009-04-24
I was using Ubuntu 8.10 with ati catalyst 9.4 and it was working great...
Now i installed Ubuntu 9.04 and ati catalyst 9.4 (2:8.602) is not working anymore (boot is working but when it has to enter gnome it's only a black screen and colors on the top of the screen, it refreshes 3 times and then it freezes)...only the driver in the repository is working (2:8.600) but it is horrible...compiz is awfull and vertical syncronization is also horrible.

Did anyone manage to get it working?

p.s. I am using ATI HD 3400 series on a lenovo t400 laptop.

---

### Post by Viper Daimao on 2009-04-24
My laptop has a radeon mobility x300 video card in it. I'm using 8.10 now with fglrx. 8.10 is the first time I've ever gotten Compizfusion to work. When I tried upgrading to 9.04 it warned me that my video card wouldn't be supported. 

My question, does this mean the video card just won't work for 9.04 and I have to stay with 8.10 or that I'll need to use a different driver and compiz isn't going to work with 9.04 but I can still upgrade?

---

### Post by jamessnell on 2009-04-24
> **eyezdk said:**
> Well, I have ATI mobility Radeon HD 3450 card. and my laptop is only 6 month old or so. so its a newer card. 

I just know, that in 8.10 it workedl like hell

I'm using a Radeon HD 2600 and I just upgraded to the latest [ATI drivers]("http://support.amd.com/us/gpudownload/Pages/index.aspx"). I had no real video issues in 8.10 and 9.04 seems fine with this card too. I play World of Warcraft in Wine, that works fine.. I use Compiz heavily, that's fine too.

---

### Post by giantoz on 2009-04-24
Are these cards not supported by the proprietary driver, or the open source?

I have an x1200, and I don't care about games, but I do care about video playback, and compiz support would be nice too.  Will I get decent video playback out of the box with jaunty's open source drivers?

Or should I just stick with Intrepid? (and get a new laptop ](*,))

---

### Post by jamessnell on 2009-04-24
Hmm, maybe that card isn't supported by the ATI driver.. Perhaps the open source one will work.. You should go look it up in the xorg docs - I'd expect you shouldn't have a lot of pain getting reasonable video support - though Hardware OpenGL support may be another matter..

---

### Post by benevolent on 2009-04-25
Same here! I have **ATI Radeon X1650 Series**.


Just upgraded to 9.04 and before the download begins it gave me an error that fgxlr (or fxglr? :lolflag: ) drivers doesn't exist in new ubuntu and have to be deleted!


Now i have the open source drivers.. Divx, youtube, compiz, working fine, but (example) google earth is freezing like hell.. Haven't tried any other application that needs 3d acceleration, but i think, they won't work as well...


So, what we, ati-non-supported users, must do?? Go back to 8.10?? It was fully supported there :confused::confused:

-dimitris

---

### Post by Gorlist on 2009-04-25
Seems rather bizarre, just installed onto a PC using a R X1300, no proprietary driver listed in the "Hardware Drivers" panel. Is this more because ati version 9.4 hasn't yet been officially released?

Tried a manual install (as I normally would in 8.10) though regardless of xorg settings it no longer functions, pretty colours, three attempts then a freeze. 

Tried playing Eternal Lands, the opensource drivers can't get me above 0 FPS. 

The only other spare card I have which can squeeze into this case is a Geforce 2 :)

---

### Post by spikoley on 2009-04-25
> **Viper Daimao said:**
> My laptop has a radeon mobility x300 video card in it. I'm using 8.10 now with fglrx. 8.10 is the first time I've ever gotten Compizfusion to work. When I tried upgrading to 9.04 it warned me that my video card wouldn't be supported. 

My question, does this mean the video card just won't work for 9.04 and I have to stay with 8.10 or that I'll need to use a different driver and compiz isn't going to work with 9.04 but I can still upgrade?

I just did a clean install with Jaunty with my X300 and Compiz runs great.  Is your card the same and what model is your laptop.   

```
lspci
```
> ATI Technologies Inc M22 [Mobility Radeon X300

---

### Post by Pas3n7 on 2009-04-25
> **giantoz said:**
> Are these cards not supported by the proprietary driver, or the open source?

I have an x1200, and I don't care about games, but I do care about video playback, and compiz support would be nice too.  Will I get decent video playback out of the box with jaunty's open source drivers?

Or should I just stick with Intrepid? (and get a new laptop ](*,))

Works fine for me out of the box. I haven't tried any real gaming yet, but videos and flash work fine. Compiz is good, but the highest effects levels are a bit laggy (still usable though, if you want it that bad).

```
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
```

---

### Post by fmfrisch on 2009-04-25
I find the new Catalyst 9.4 quite buggy. Compiz does not run as smooth as before. There is this weird thing that happens when you maximize windows everything freezes for a second. Have no option but running it since it's the only version compatible with new Ubuntu 9.04. Please if someone has a solution to this please share!

just a quick btw on the subject:
I've been looking for a way to change between graphic drivers. Is there some sort of GUI? I dont have the time to go edit the xorg.conf everytime. Just wanted to do some test etc.

---

### Post by StuartN on 2009-04-25
> **Viper Daimao said:**
> My question, does this mean the video card just won't work for 9.04 and I have to stay with 8.10 or that I'll need to use a different driver and compiz isn't going to work with 9.04 but I can still upgrade?

Running the Live CD will show you what graphics you will get under 9.04, without changing your existing installation.

I tried the Live CD on my Dell Inspiron 1501 with an ATI Radeon Xpress 200M. This card is not supported in Catalyst 9.4 and Ubuntu automatically configured the older "radeon" driver. Apparently this is slower than the proprietary Catalyst in Ubuntu 8.10, but the older Catalyst drivers are not compatible with X server 1.6 while the "radeon" is compatible.

And my Broadcom wireless worked out of the box with a choice of "b43" or Broadcom "wl" drivers.

---

### Post by jamessnell on 2009-04-25
> **fmfrisch said:**
> I find the new Catalyst 9.4 quite buggy. Compiz does not run as smooth as before. There is this weird thing that happens when you maximize windows everything freezes for a second. Have no option but running it since it's the only version compatible with new Ubuntu 9.04. Please if someone has a solution to this please share!

just a quick btw on the subject:
I've been looking for a way to change between graphic drivers. Is there some sort of GUI? I dont have the time to go edit the xorg.conf everytime. Just wanted to do some test etc.

My Radeon HD 2600 is supported by Catalyst 9.4, as such, since it's supported upgrading to 9.04 hasn't screwed me over in terms of video performance.. Maybe check to see if your card is supported by the 9.4 Catalyst driver.

---

### Post by bebox on 2009-04-26
> **fmfrisch said:**
> I find the new Catalyst 9.4 quite buggy. Compiz does not run as smooth as before. There is this weird thing that happens when you maximize windows everything freezes for a second. Have no option but running it since it's the only version compatible with new Ubuntu 9.04. Please if someone has a solution to this please share!

Same here!

---

### Post by jamessnell on 2009-04-26
> **bebox said:**
> Same here!

I guess it performs differs in performance from one card to the next, my HD 2600 seems to perform at least as well as it did on 9.3, if not better. My frame rates in WoW has seemed to have been quite good. :)

---

### Post by theglowblue on 2009-04-26
> **Viper Daimao said:**
> My laptop has a radeon mobility x300 video card in it. I'm using 8.10 now with fglrx. 8.10 is the first time I've ever gotten Compizfusion to work. When I tried upgrading to 9.04 it warned me that my video card wouldn't be supported. 

My question, does this mean the video card just won't work for 9.04 and I have to stay with 8.10 or that I'll need to use a different driver and compiz isn't going to work with 9.04 but I can still upgrade?

Just did the upgrade on my IBM z60 laptop with the AIT mobility Radeon x300 and it looks like this card, and fglrx are not supported at the moment. 

X comes up fine and everything looks and works good. There is just no compiz. And I think the processor is doing a lot more of the screen rendering rather than the graphics card. 

I downloaded the current driver from ATI, but jaunty I do not think is listed for support yet, so the installer exits out. 

I plan on sitting tight for a couple weeks and see if the updated driver via apt or through ati comes out.

---

### Post by fmfrisch on 2009-04-26
> **jamessnell said:**
> Maybe check to see if your card is supported by the 9.4 Catalyst driver.

My card is a Radeon HD3650. What I can understand it's supported. It's only a year old model too. So don't really know why I'm having problems. I've noticed though that the majority of people having problems are on HD3xxxx cards..

---

### Post by jamessnell on 2009-04-26
Well, 9.04 is still QUITE new - maybe it's just a matter of enough ppl complaining a bit to ATI and letting a bit of time pass before that stuff gets squared away.

---

### Post by ssri on 2009-04-26
ATI's Catalyst 9.4 dropped support for R300-R500 cards, meaning 9.3 is going to be the last proprietary driver (:-({|=) that will support those cards (like ati's mobility x2300 on my 1.5 year old laptop :().  Furthermore, 9.3 only supports up to xorg 1.5, meaning I cannot use Jaunty (xorg 1.6) unless I can compile xorg 1.5 on it.  Again refer to ATI's list of supported cards for 9.4.  If yours is not on it, then I would not recommend upgrading to Jaunty unless you do not mind not having 3D acceleration or can manage to compile xorg 1.5 in jaunty.

---

### Post by nibbana84 on 2009-04-26
> **jamessnell said:**
> Well, 9.04 is still QUITE new - maybe it's just a matter of enough ppl complaining a bit to ATI and letting a bit of time pass before that stuff gets squared away.

I'm waiting from years for 3d working drivers. It shoud be enough. Now we can't have 2d as well.
"Ppl" as you say, would like to use the operating system they like, but they can't. They should complain more in my opinion.

---

### Post by jamessnell on 2009-04-26
> **nibbana84 said:**
> I'm waiting from years for 3d working drivers. It shoud be enough. Now we can't have 2d as well.
"Ppl" as you say, would like to use the operating system they like, but they can't. They should complain more in my opinion.

Well, there's reporting and then there's whining - not that I'm saying you're whining.

The issue is that ATI was consumed by a company (AMD) that's having a really hard time keeping itself together. We'd love to use Proprietary drivers as they tend to allow us to USE our stuff without the company having to divulge their few alleged secrets that I suspect they keep in order to milk an old idea for as much $ as possible. So, as it stands, if ATI/AMD is unwilling to provide support for their older products then it's just one more reason why I'm going to continue to go further out of my way to buy NVIDIA. I'm disappointed with ATI's performance on Linux since the start (though for many years I'd only ever buy ATI). The fact that they still seems to provide half assed support just furthers my desire to run with NVIDIA as their drivers seem somewhat better with Linux.

At the end of the day, they both kinda suck. And we all know it. If the issues remain long enough it'll just serve to reinforce there being a market for a company to do a better job either by providing great drivers or at least really opening up the details for third parties to make their own drivers.

It may take another 30 years, but I expect the day will come with technologies such as FPGAs will have evolved enough that open source communities can develop their own GPUs too and put an end to this time-wasting approach of mediocrity. 

It's either that, or we all start shelling out the $$ to get one of these companies to give a rats ***, even then, I suspect it'll take something of a zombie apocalypse to turn things around with them.

---

### Post by jflowers on 2009-04-26
> **spikoley said:**
> I just did a clean install with Jaunty with my X300 and Compiz runs great.  Is your card the same and what model is your laptop.   

```
lspci
```
Did it install the fglrx driver or the open ati driver?  I have the same video card and while running the open ati driver compiz does not work, but in Intrepid I could get compiz to run with fglrx?

Thanks.

---

### Post by chconnor on 2009-04-27
Dell Inspiron 6000 with ATI Mobility Radeon X300... predictably, it works but using reg'lar drivers. Occasionally glitchy graphics but functional. Haven't bothered trying fglrx given threads like this (used it fine with 8.10).

My questions:

- any way to get OpenGL to work or is that a non-starter?

- if ATI is dead to us, is there any chance that xorg 1.6 could be made to be compatible with the old ATI drivers? Is that line of inquiry even on the table?

-c

---

### Post by prem1er on 2009-04-27
My card is in my Sig and works flawlessly with 9.04.  I had so many problems with 8.04 and 8.10.

---

### Post by Viper Daimao on 2009-04-27
> **spikoley said:**
> I just did a clean install with Jaunty with my X300 and Compiz runs great.  Is your card the same and what model is your laptop.   

```
lspci
```

Dell Inspiron 6000 with ATI Mobility Radeon X300. I'll try out a live cd and see how it runs.

---

### Post by celem on 2009-04-27
My ATI video card's lspci is:
```
05:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series
```
Everything seemed to work with the Proprietary ATI Driver, even Compiz, until I selected System->Preferences->Display
This would lock up the system until it timed out as not responding. Once I removed the driver I had no further problems with selecting System->Preferences->Display.

I was going to the Display preferences because I noticed that firefox was bigger (showed less information) with my 1440x900 display than on the same type display on my Windows XP machine.

I am a bit hesitant to reload the ATI Proprietary driver again after this negative experience.

---

### Post by hgergo on 2009-04-27
I think sombody must write a petition and then send to ati that we need linux drivers or make it open source

---

### Post by xpix on 2009-05-10
I just want to share my exp and ask a questions

I have an Acer Aspire 5100 Turion64x2, 2G Ram and the stupid ATI Radeon Xpress 1100(ATI Technologies Inc RS482 [Radeon Xpress 200M]).

Finally I have native support for my wireless card and I really love the 9.04

My only problem is that I cannot watch flash movies in full screen. I guess it's a flash/video card issue.

I tried Adobe Flash, Gnash and Swfdec and I get the same behavior: slow performance in full screen(divx movies run ok in full screen)

I also switched to the 64bit version and ext4 but did not make a difference.

My question is: Is there something I can do to speed up my video card? 
Effects run ok on normal and extra settings

Thx

---

### Post by celem on 2009-05-10
You won't like my response. I gave up on ATI and removed my troublesome ATI Mobility Radeon HD 3600 Series and replaced it with an Nvidea card. All is now well - and fast. Actually, my ATI was also fast - just had the problems that I noted in my previous post.

---

### Post by Yellow Pasque on 2009-05-10
> You won't like my response.
Do whatever works for you. I prefer ATI hardware, but it's not like the company ever cared too much about the relatively insignificant Linux desktop market. They want OEM contracts and Windowz gamerz' $. Their real strategy on Linux is open-source. Yeah, they port their Windowz driver stack to maintain the illusion that they actually care, but they don't.

---

### Post by kemorc on 2009-05-13
ATI and AMD are so far behind right now...

But the only thing that I've done to finally get 9.04 stable... is I managed to get the driver from ATI/AMD's website to install.  No problems yet... *knock on wood*.

---

### Post by d_fiant_1 on 2009-05-16
I have always bought ATI and AMD products for the sheer reason of competition in the market and they have been great products...BUT after upgrading from Ubuntu 8.10 to 9.04 with my HD 2600 (Still supported) but it doesn't support Xorg 1.6 and haven't don't anything in 3 months to recify that situation...and the fact that they are stopping support for older cards that are STILL popular is extremely concerning...not to mention enough to piss off the most loyal of ATI customers and in eefect chopping of their noses to spite their own faces...because what they are doing to themselves is making Nvidia a much more appealing product for Linux users.

I for one have gone out and bought a new Nvidia graphics cards, so ATI can go and get stuffed for screwing over us Linux users.

---

### Post by NormanFLinux on 2009-08-03
The open source ATI drivers do work. It takes a little involved x.org.conf file editing to make Ubuntu boot with them. I don't think ATI will ever write new proprietary drivers for its legacy cards again. This three year old laptop with dual core Intel Centrino Duo has a Radeon X1300 Mobility chipset. Open source is definitely the way to go with older hardware. I run Kubuntu on it as KDE seems better suited to a large screen notebook.

---

### Post by ukuli on 2009-08-10
I have a problem with ATI Radeon X1250 on ACER Travelmate 5520 laptop. I have tried various ways of getting the drivers to work, such as installing them myself or adding a repository from Launchpad. Nothing seems to work. Ubuntu is 9.04.

Can anybody point to me an instruction that shows how to get the drivers to work? I cannot find anything that really works.

---

### Post by Yellow Pasque on 2009-08-10
> I have tried various ways of getting the drivers to work, such as installing them myself or adding a repository from Launchpad. Nothing seems to work. Ubuntu is 9.04.

Which driver? Open-source or proprietary?

---

### Post by Gorlist on 2009-08-10
only the open source drivers will work on the Acer 5520 with 9.04. Fine for basic apps. The only other solution is perhaps to shift back to 8.04?

---

### Post by Yellow Pasque on 2009-08-10
I used to have a 690G/X1250 and I found the radeonhd driver worked well, although the 3D performance was not the best.
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by bitra on 2009-08-10
> **hgergo said:**
> I think sombody must write a petition and then send to ati that we need linux drivers or make it open source

As far as I know, ATI website already has linux driver (contributed by the community, if I'm not mistaken). Do you guys know wether this driver should work with Ubuntu 9.04? --> [**ATI catalyst display driver for linux**]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English")

Information from the above link says:

> ATI Catalyst Display Driver
Version: 9.7 
Operating System(s): Linux x86; Linux x86_64

It also says:

> Description:
Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, or 7.4

* The display driver requires POSIX shared memory to be enabled on the system.
* Kernal Sources package is no longer required if Kernel Header package is installed.
* 32-Bit packages must be installed for 64-Bit Linux drivers to install or work.


I need the driver for my Radeon 3100 on my Toshiba Satellite laptop. I need your opinion, does it safe to download the driver?

Thanks

---

### Post by ukuli on 2009-08-10
> **Temüjin said:**
> Which driver? Open-source or proprietary?

I am using the open source driver. When I install the proprietary driver Ubuntu doesn't reboot any more. With open source driver every software that uses 3d graphics is really slow. And then there is the flicker problem described in this thread.

Do you have a link to proper instructions about how to install the proprietary driver without crashing the entire Ubuntu? The ones I have tried didn't work...

---

### Post by Yellow Pasque on 2009-08-10
ukuli, ATI does not support your GPU in Jaunty. You must use open-source drivers.

---

### Post by metallus on 2009-08-25
I have ati mobility radeon 3450 on an fujitsu-siemens esprimo mobile v6545. I installed the latest driver from amd.nvidia.com on Ubuntu 9.04 and it worked. this is how I have done it:
-must be root
-generate distribution specific packages. Use 
                  ./ati-driver-installer-9-8-x86.x86_64.run --listpkg
                  ./ati-driver-installer-9-8-x86.x86_64.run --buildpkg Ubuntu/9.04
                  you can use any version of the drivers on any supported distribution(but only this one works on ubuntu 9.04)
-install the packages (either with double-click on them oe with dpkg -i <package name> command). you cannot install them in other order than the correct one (because of the dependencies).
-reboot
-nou run again the install package and install from there using the graphical user interface (command: ./ati-driver-installer-9-8-x86.x86_64.run from a terminal)
-reboot and your'e done. if it does not work, write as root in a terminal: aticonfig --initial . reboot. good luck! if this does not work, than try envyNG utility.

---

### Post by jamessnell on 2009-08-25
Whoa, that made me do a double-take... Was that url a typo? ATI drivers from a subdomain of NVIDIA? :confused:

> **metallus said:**
> I have ati mobility radeon 3450 on an fujitsu-siemens esprimo mobile v6545. I installed the latest driver from amd.nvidia.com on Ubuntu 9.04 and it worked. this is how I have done it:
-must be root
-generate distribution specific packages. Use 
                  ./ati-driver-installer-9-8-x86.x86_64.run --listpkg
                  ./ati-driver-installer-9-8-x86.x86_64.run --buildpkg Ubuntu/9.04
                  you can use any version of the drivers on any supported distribution(but only this one works on ubuntu 9.04)
-install the packages (either with double-click on them oe with dpkg -i <package name> command). you cannot install them in other order than the correct one (because of the dependencies).
-reboot
-nou run again the install package and install from there using the graphical user interface (command: ./ati-driver-installer-9-8-x86.x86_64.run from a terminal)
-reboot and your'e done. if it does not work, write as root in a terminal: aticonfig --initial . reboot. good luck! if this does not work, than try envyNG utility.

---

### Post by madscientist032 on 2010-02-17
> **fmfrisch said:**
> I find the new Catalyst 9.4 quite buggy. Compiz does not run as smooth as before. There is this weird thing that happens when you maximize windows everything freezes for a second. Have no option but running it since it's the only version compatible with new Ubuntu 9.04. Please if someone has a solution to this please share!

just a quick btw on the subject:
I've been looking for a way to change between graphic drivers. Is there some sort of GUI? I dont have the time to go edit the xorg.conf everytime. Just wanted to do some test etc.

I have this same issue. Is there a fix?

Thanks in advance

---

### Post by Mark Phelps on 2010-02-17
This is a really old thread and your question is not really central to Ubuntu 9.04 and ATI driver support.

Your question is about video drivers in general.

Please don't hijack this thread but start your own thread, instead.  You'll likely get better responses that way.

---

