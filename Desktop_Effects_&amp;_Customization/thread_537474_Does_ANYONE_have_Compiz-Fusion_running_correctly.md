---
title: "Does ANYONE have Compiz-Fusion running correctly?"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by amadeus266 on 2007-08-28
I have had to reinstall my system 4 times and block certain updates just to have a functional system with or without eyecandy. I have an ATI AIW 9200 and before the updates from trevino's repo on the 19th everything worked great. Now nothing, not even beryl will run and I keep having random black screen lockups on a clean install that never happened before. I sure hope Gutsy works out better than this. I really don't want to have to go back to windows. YUCK!

---

### Post by michael37 on 2007-08-28
> **amadeus266 said:**
> I have had to reinstall my system 4 times and block certain updates just to have a functional system with or without eyecandy. I have an ATI AIW 9200 and before the updates from trevino's repo on the 19th everything worked great. Now nothing, not even beryl will run and I keep having random black screen lockups on a clean install that never happened before. I sure hope Gutsy works out better than this. I really don't want to have to go back to windows. YUCK!

Compiz is now broken for me with the latest update.  Compiz crashes, and windows lost deocrations.

---

### Post by psmar on 2007-08-29
i have an older nvidia card running Compiz-fusion and I did have a problem for about a week due to one of there updates, but since then Its come better then before complete with the new bells and whistles.

It might just be taking a little bit longer for the ATI group to catch up

---

### Post by psyopper on 2007-08-29
I have a really nasty habit of removing the repos from my sources.list when I get a functional, stable, usable Fusion. Granted I don't get updates, but considering that it is functional, stable and usable, why update it?

I do realize this doesn't answer your question. However, if you are having issues after a clean install with no CF then I wonder about the current life expectency of your video card?

---

### Post by hyperair on 2007-08-29
I'm using Trevino's repository's version and I have it running fine here.

---

### Post by njknight on 2007-08-29
Yep - I'm also using Trevino's repository's and my Compiz Fusion is set up and running great

---

### Post by amadeus266 on 2007-08-29
> **psyopper said:**
> 
I do realize this doesn't answer your question. However, if you are having issues after a clean install with no CF then I wonder about the current life expectency of your video card?

True, I may be having hardware problems. Both of cd drives seem to be having problems as well. This machine is only 2 years old but the vid card is closer to 4. What nvidia card are you using? I have an old  Nvidia Riva TNT2 that has 3d capability.

---

### Post by Inxsible on 2007-08-29
I have a NVidia 7600 GeForce Go 256MB and I run Compiz Fusion without issues from Trevino's repos.

Granted there were a few issues a while back, but everything seems to be in order now. Vorian discourages use of Trevino's repos, since its 3rd party. but Amaranth's repos don't have all the plugins that Trevino has.(at least that was the case when I installed from Amaranth's repos) With all the updates that you get every week, maybe Amaranth's repos are as good or even better.

---

### Post by FuturePilot on 2007-08-29
Everything running fine here with a Nvidia GeForce 6600 256MB
There were a few small issues with some of the updates, but nothing that prevented me from using CF.

---

### Post by michael37 on 2007-08-29
> **michael37 said:**
> Compiz is now broken for me with the latest update.  Compiz crashes, and windows lost deocrations.

Update.  Compiz is now running fine after a complete uninstall (including all preferences) and reinstall.  

However, I am seriously considering switching from unstable Trevino to more stable [Amaranth  repositories](https://help.ubuntu.com/community/CompositeManager/CompizFusion?highlight=amaranth)

---

### Post by Rupertronco on 2007-08-29
Vorian's repos are also always stable (not always the newest plug-ins) but I've never had a problem with an update.

---

### Post by Inxsible on 2007-08-29
> **michael37 said:**
> Update.  Compiz is now running fine after a complete uninstall (including all preferences) and reinstall.  

However, I am seriously considering switching from unstable Trevino to more stable [Amaranth  repositories]("https://help.ubuntu.com/community/CompositeManager/CompizFusion?highlight=amaranth")

If you do, let us know if it has all the plugins that you have in Trevino's :)
and also report back on its stability

---

### Post by Magneticgravity on 2007-08-29
Is Amaranth more stable then? Arent they both third party?

---

### Post by Inxsible on 2007-08-29
> **Magneticgravity said:**
> Is Amaranth more stable then? Arent they both third party?
Trevino is 3rd party. Amaranth is a developer and maintainer for Compiz in Ubuntu development. His repos are also the ones, being/will be used for Gutsy. He has simply backported them, so people with Feisty can use them. So he is not really 3rd party.

---

### Post by michael37 on 2007-08-29
Speaking of Trevino's repos, I upgraded to 0.5.5 using his plugins and I lost Aquarium and 3D window (although I gained Cube Gears plugin).  Anybody else had this experience?  I am certain I am using Trevino's repos since Amaranth provides "stable" 0.5.2 CF.

---

### Post by Inxsible on 2007-08-29
> **michael37 said:**
> Speaking of Trevino's repos, I upgraded to 0.5.5 using his plugins and I lost Aquarium and 3D window (although I gained Cube Gears plugin).  Anybody else had this experience?  I am certain I am using Trevino's repos since Amaranth provides "stable" 0.5.2 CF.

By aquarium, if you mean a school of fish inside your cube then yes, I still have it. I have the 3d Windows too and Cube Gears too. Although I don't use the Cube gears and the aquarium.

Are you saying that you don't see the plugins at all in CCSM, or just that you can't activate/deactivate them?

---

### Post by Magneticgravity on 2007-08-29
> **Inxsible said:**
> Trevino is 3rd party. Amaranth is a developer and maintainer for Compiz in Ubuntu development. His repos are also the ones, being/will be used for Gutsy. He has simply backported them, so people with Feisty can use them. So he is not really 3rd party.

Would you recommend Amaranth over Trevino?

---

### Post by michael37 on 2007-08-29
> **Inxsible said:**
> By aquarium, if you mean a school of fish inside your cube then yes, I still have it. I have the 3d Windows too and Cube Gears too. Although I don't use the Cube gears and the aquarium.

Are you saying that you don't see the plugins at all in CCSM, or just that you can't activate/deactivate them?

I no longer see the latter two plugins in CCSM.  

Am I missing any packages? I am running amd64.

```

$ sudo dpkg -l | grep compiz
ii  compiz                                     0.5.5~git20070827+jbs0                 OpenGL window and compositing manager
ii  compiz-core                                0.5.5~git20070827+jbs0                 OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2~git20070827+jbs0                 Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-main                 0.5.2~git20070827+jbs0                 Collection of Compiz Fusion plugins for Comp
ii  compiz-fusion-plugins-unsupported          0.5.2~git20070822+jbs3                 Collection of plugins for Compiz - Unsupport
ii  compiz-gnome                               0.5.5~git20070827+jbs0                 OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.5~git20070827+jbs0                 OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2~git20070827+jbs0                 Plugin and configuration tool - Compiz Fusio
ii  libcompizconfig-backend-gconf              0.5.2~git20070821+jbs1                 GNOME Backend for the Compiz Configuration S
ii  libcompizconfig0                           0.5.2~git20070825+jbs1                 Settings library for plugins - Compiz Fusion
ii  python-compizconfig                        0.5.2~git20070824+jbs0                 Python bindings for the Compiz Configuration

```

---

### Post by Inxsible on 2007-08-29
> **Magneticgravity said:**
> Would you recommend Amaranth over Trevino? I can't really say. I use Trevino's as of now, because the last time I used Amaranth's there were a number of missing plugins that I had gotten used to.

But it won't take Amaranth to get up to speed with all the plugins. Maybe, I'd switch then but then again, Trevino might come up with some ultra cool things too.

Its all about choice. Use the one you feel comfortable using.

---

### Post by Inxsible on 2007-08-29
> **michael37 said:**
> I no longer see the latter two plugins in CCSM.  

Am I missing any packages? Unfortunately, I am at work ;)

So I am away from my Ubuntu machine. I will check my packages tonight and post back. But in the meanwhile, do you have compiz-fusion-plugins-unofficial installed?

there is also one with "unsupported" in the package name. [COLOR=Red]EDIT: I see you have the unsupported installed[/COLOR].

---

### Post by amadeus266 on 2007-08-29
Thank you all for your input everyone. I am going to test my hardware again and try another fresh install and try Amaranth's repo and see what happens. But there is a possibility that my machine is dying and I'll be stuck with windows on my other machine until I can afford to fix this one up again. Anyone here using 64bit? If so, is it worth trying it. My machine is an AMD Athlon 64 1.8GB.

---

### Post by amadeus266 on 2007-08-29
It seems that will work for me for a while. Hardware is having problems (2 dead cd drives, 1 dead fan) but it is running. Thanks again everyone.

---

### Post by michael37 on 2007-08-30
> **amadeus266 said:**
>  Anyone here using 64bit? If so, is it worth trying it. My 
machine is an AMD Athlon 64 1.8GB.
Yep, 64-bit here.  Ubuntu kernel, Xgl, Compiz, Firefox, Thunderbird, name it, all 64-bit :guitar:

---

### Post by rafaelinux on 2007-08-30
It's working perfectly for me.
Installed from latest repositories. Ubuntu 7.04
Using an amd x1150 (onboard video), and it goes really smooth...
----
Well, that's now.. but it was a hell to install it, just having xgl server to start over my ati driver was a pain, but.. after that, ... it went smooth..

BTW, did you notice any cool performance boost on 64bit?
I have a X2 3800..

---

