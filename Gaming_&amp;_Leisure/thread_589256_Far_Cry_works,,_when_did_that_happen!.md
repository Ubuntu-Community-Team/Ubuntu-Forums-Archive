---
title: "Far Cry works,, when did that happen!"
date: 2007-10-24
forum: Gaming &amp; Leisure
---

### Post by mbradlcu on 2007-10-24
so after a completely painless upgrade to 710 and goofing around with wine it seems Far Cry works great! and on my not so new hardware.. thanks to ubuntu and the talented folks at the wine project...

---

### Post by Sockerdrickan on 2007-10-24
You should send the wine folks a mail!

---

### Post by weblordpepe on 2007-10-24
I think I'm going to spew. Far Cry works?!

---

### Post by crane on 2007-10-24
is this the same Far Cry I got like 5 FPS out of the last time I tried it?

---

### Post by Sockerdrickan on 2007-10-24
I've ran it without problems with nice FPS.

---

### Post by ELD on 2007-10-24
It seems Wine really has been making strides lately, everytime i check the database it seems more programs and games work out-of-the-box.

It will be interesting to see how transgaming and crossover do once Wine reaches maturity, their business would dissapear?

---

### Post by crane on 2007-10-24
Well, I can see what I'll be doing later!

---

### Post by Biskit64 on 2007-10-24
> **mbradlcu said:**
> so after a completely painless upgrade to 710 and goofing around with wine it seems Far Cry works great! and on my not so new hardware.. thanks to ubuntu and the talented folks at the wine project...
 Great news
  Could you post  how you got it to run ? Did you use the loki installer or are you running it as a windows app in wine ?

---

### Post by angry-broadcom-user on 2007-10-24
Great!
What version of wine are you running?

---

### Post by mbradlcu on 2007-10-24
as soon as I get home I'll verify what version of wine it is, but I just dis-upgraded to 710 so I'm guessing its what ever version is included,, O and I'm running 64bit too.. go ubuntu/wine go!
as for how I got it to install, I had a backup install off a windows version (I actually do own all my games) I just copied over the entire directory to my ~/ .. The game can be started by either clicking on the Farcry.exe in the nautilus file browser or via 'wine farcry.exe' in the CL,,, O 1 last thing I'm pretty sure I'm using a cd crack. BTW the frame rate is pretty good too, it's definitely very playable and my system is pretty old.
ok I just checked, I'm using  wine --version wine-0.9.46.

---

### Post by Lster on 2007-10-24
Wow! I've tried a couple of times but never managed to get it working at all. This really does sound great - I would love to hear your "guide" on the matter. :)

---

### Post by Lster on 2007-10-24
Well for those interested look at the Wine DB:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1743](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1743)

---

### Post by Biskit64 on 2007-10-27
I just gave it a try and it runs smooth as butter useing wine 0.9.47 only bug is a crash when you use mouse wheel.

---

### Post by Lster on 2007-10-28
I would be interested to here what you guys did to get it working!

---

### Post by bastiegast on 2007-10-28
I still get a segfault, has been that way in feisty too.

---

### Post by Wiebelhaus on 2007-10-28
> **weblordpepe said:**
> I think I'm going to spew. Far Cry works?!

lol

---

### Post by Biskit64 on 2007-10-28
I just installed it as a windows app in wine, applied the latest patch.
And bam it works great, 
I  Just used the windows installer.

my system Specs
 Athlon 64 4000+
 ubuntu 7.10
  nvidia 6600gt
  sb live audigy 2
 2 gigs of ddr

---

### Post by Crafty Kisses on 2007-10-28
> **mbradlcu said:**
> so after a completely painless upgrade to 710 and goofing around with wine it seems Far Cry works great! and on my not so new hardware.. thanks to ubuntu and the talented folks at the wine project...

That's weird!

---

### Post by mbradlcu on 2007-11-05
> **bastiegast said:**
> I still get a segfault, has been that way in feisty too.

after removing and re-installing ~/.wine I needed to download msvcr71.dll,,, ??? and another .dll (sorry I'm not at my machine right now) but running wine farcry.exe on the CL standard out showed what was missing. Hopefully if you install those files you'll be working like I am.. hope it helps..

---

### Post by bastiegast on 2007-11-05
> **mbradlcu said:**
> after removing and re-installing ~/.wine I needed to download msvcr71.dll,,, ??? and another .dll (sorry I'm not at my machine right now) but running wine farcry.exe on the CL standard out showed what was missing. Hopefully if you install those files you'll be working like I am.. hope it helps..

Will try that, thanks!

---

### Post by weblordpepe on 2007-11-06
Damnit it just does not want to work for me.
I've got latest Ubuntu & wine, but I have an ATI card. A Radeon 9600 with restricted drivers. I'm not even going to attempt the open-source drivers.

I am running ATI driver version 8.37.6. I know there's a later version but I can't figure how to install it without totally destroying X.

---

### Post by mbradlcu on 2007-11-06
Hi weblordpepe,
can you start FarCry.exe using the command line and post what you get in the terminal? I'd like to see what wine bombs out on.. also a quick shot in the dark but if you run in a terminal
```
  glxinfo | grep Yes
```
do you get
>  direct rendering: Yes

I don't run an ati card but I suspect the game/or_wine needs to see direct rendering "yes"


thanks!

---

### Post by weblordpepe on 2007-11-06
When I run FarCry.exe from the terminal I get this:
> fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias -720, std (d/m/y): 18/03/2007, dlt (d/m/y): 30/09/2007
Segmentation fault (core dumped)


And I have this information from **glxinfo | grep Yes**:> direct rendering: Yes

I really want to run Far Cry :(
Wine version is **wine-0.9.46**
My **fglrxinfo** says:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.0.6473 (8.37.6)


And  **cat /proc/version** shows: > Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007

Help :(

---

### Post by mbradlcu on 2007-11-07
ok that's totally u.g.l.y! and a quick google brought up this [http://source.winehq.org/source/dlls/ntdll/time.c]("http://source.winehq.org/source/dlls/ntdll/time.c")
which is waaay over my skill level,, anyway if you haven't tried to remove/purge wine,, and rm -rvf ~.wine ... I would start there. 
Does any other wine apps work? can you run winecfg?
since you have direct rendering at least that's good news.

---

### Post by weblordpepe on 2007-11-07
Everything works beautifully except for far cry :(
Yeah I saw that ntdll/time.c file too. Way over my skill level as well. I wish I could just delete the error line. Although I tell ya what - I'm not sure that the time thing is what I should be concerned about. I don't think the time thing is a stop-error.

I'm gonna try deleting the .wine and see if it helps.

---

### Post by weblordpepe on 2007-11-07
AAAAAAAAaaaaaaaaaaaaaahh!!! IT WORKS!!!

Deleting the .wine directory did the trick!!! I love you. Lets get married. No wait. Then I would have less time for Far Cry.:guitar:

---

### Post by mbradlcu on 2007-11-07
excellent! thanks for the update.. I was playing it last night and man it's still a blast,, have fun.

---

### Post by weblordpepe on 2007-11-08
naaaaaaananannnannananananaanananannaanaaaaa awesome!!! :guitar:

---

### Post by Rafadagaffer on 2007-11-08
Gonna try install this now :guitar:

---

### Post by Lster on 2007-11-08
I know what you mean! Far Cry is the best game I have **ever** played... I'm currently trying out Crysis on Windows Xp which also rocks - although I have to turn down the graphics a bit.

Maybe it's time for a new computer! :)

---

### Post by weblordpepe on 2007-11-09
Yay a new game for Linux  :D
So now we got Quakewars and Far Cry on linux in the past few weeks. :)

---

### Post by mbradlcu on 2007-11-10
you know hl2_e2 and portal play great, they're pretty recent. I'd like to see cod4 work,, it's close.. but

---

### Post by weblordpepe on 2007-11-10
Rad.
So what major titles do we have under our belt then?
Steam-
Half Life 2 / HL2 E2
Doom 3  / Quake 4 / Quakewars
Far Cry
Portal
Call of Duty 1/2
WoW
And Unreal 3 coming up soon?

---

### Post by mbradlcu on 2007-11-10
here's a quick view of my games folder but there's soo many titles out there,,
Call of Duty                        Star Wars Republic Commando  legends
Call of Duty 2                      WoP                          planeshift
Devastation                         alienarena2006               quake3
FarCry                              btrl_demo                    quake4
GTKradiant_svn                      doom3                        serioussam2
Medal of Honor Pacific Assault(tm)  duke3d                       tribaltrouble
Painkiller                          eliteforce                   tribes2
PenumbraEp1Demo_org                 enemy-territory              ut2004
PlaneShift                          etqw                         ut_org
Prey                                gtkradiant                   wolfenstein
Savage                              kingpin                      x2-demo

---

### Post by Vadi on 2007-11-10
> **weblordpepe said:**
> Damnit it just does not want to work for me.
I've got latest Ubuntu & wine, but I have an ATI card. A Radeon 9600 with restricted drivers. I'm not even going to attempt the open-source drivers.

I am running ATI driver version 8.37.6. I know there's a later version but I can't figure how to install it without totally destroying X.

Actually I definitely think you should give them a try, I use them, and they perform better than the ati ones.

---

### Post by weblordpepe on 2007-11-11
But they so slow and game's dont work properly. Doom3 doesn't even show specular hilights  :/

---

### Post by mbradlcu on 2007-11-11
are you talking about running doom3 under wine? I run it with the native binary, reason I ask is that my time demos run in the 70s with everything up.. not sure about the feature you mention but it looks good to me.

---

### Post by weblordpepe on 2007-11-11
The native binary.
If you use the open-source driver then doom 3 runs at half the speed, and doesn't show specular hi-lights.

---

### Post by ELD on 2007-11-11
> **weblordpepe said:**
> Rad.
So what major titles do we have under our belt then?
Steam-
Half Life 2 / HL2 E2
Doom 3  / Quake 4 / Quakewars
Far Cry
Portal
Call of Duty 1/2
WoW
And Unreal 3 coming up soon?

I would hardly class them as under our belt unless wine works for flawlessly for  95% of people for the non native ones.

---

### Post by weblordpepe on 2007-11-11
Well they work. Enough. And people play them...so why not?

---

### Post by anaconda on 2007-11-12
> **weblordpepe said:**
> Yay a new game for Linux  :D
So now we got Quakewars and Far Cry on linux in the past few weeks. :)

hmm... I had farcry running without problems in ubuntu Dapper (6.06) so I wouldn't say it is a new addition...

The installer didnt work then, but when copied from windows partition, adding the few missing .dll files and registry settings and something. it run perfectly..

---

### Post by weblordpepe on 2007-11-12
Oh!
Okay :)
Well I installed the demo using Wine, and then tweaked it & it runs great now. I also did the same with Max Payne demo too if anyone was interested. That runs flawlessly.

---

