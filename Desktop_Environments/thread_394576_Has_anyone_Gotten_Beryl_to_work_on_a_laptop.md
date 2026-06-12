---
title: "Has anyone Gotten Beryl to work on a laptop?"
date: 2007-03-27
forum: Desktop Environments
---

### Post by tsmonaghan on 2007-03-27
Just wondering. I have a laptop running dapper. Thanks!

---

### Post by nsleiman on 2007-03-27
as far as i know there are plenty users using beryl on their laptops:

take a look at 

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

and

[http://ubuntuforums.org/showthread.php?t=393679](http://ubuntuforums.org/showthread.php?t=393679)

---

### Post by ctt1wbw on 2007-03-27
Yep, I gots Beryl working on my HP dv8000 with an ATI Radeon 200m under Ubuntu 6.10 and also working on an IBM Thinkpad T30 with an ATI Mobility Radeon 7500 running Fedora Core 6.

---

### Post by floke on 2007-03-27
Works fine on my Tecra A8. Intel 945GM display driver. Even with rain etc.

:)

---

### Post by szantaii on 2007-03-28
Sure, Beryl is working on my Lenovo 3000 N100 (Core2Duo T5500, Intel GMA950).

---

### Post by ctt1wbw on 2007-03-28
> **Steve.K said:**
> Works fine on my Tecra A8. Intel 945GM display driver. Even with rain etc.

:)

You know, speaking of this rain thing...  I tried it on my ATI 200m and it didn't work.  Any special thing I have to do or something?  I would like to see that.

---

### Post by igknighted on 2007-03-28
> **tsmonaghan said:**
> Just wondering. I have a laptop running dapper. Thanks!

With Dapper it will be difficult.  If beryl is your bag, I would try Edgy or Feisty when it comes out.  With Dapper you must use XGL, which is (1) a pain to set up, and (2) Doesn't let your run apps like google earth or anything else 3d.  If you have an ATI card it doesn't really matter as XGL is your only option anyway, but if you have nvidia or intel on your laptop, then look into upgrading.

---

### Post by hairy on 2007-03-28
i'd possibly avoid with nvidia as well, unless it's a fairly new laptop. i tried beryl and compiz on a toshiba sattelite pro m10 (not the best of hardware granted, but at least I thought it would make a nice ubuntu machine) and ran into lots of problems. 

that machine has a geforce 420 2 go (i think considered legacy by nvidia. at least i couldn't get 9755 to work with it. 9631 did though. consider using envy if your not happy installing drivers the hard way) 

9775/9631 support GLX_texture_from_pixmap, but lots of people (including myself) had big issues with it. once video memory runs out all new windows dont have any content (normally looking black, but i even had empty windows!). on that card video memory runs out very quickly heh. A way around that is to force the card to copy textures from memory (select copy from advanced beryl options | rendering path, start compiz with the --indirect-rendering option), but I have seen reports stating that this simply delays the problem rather than solves it. a little searching around will give a wealth of information

indirect rendering will probably give a poor user experience with the sort of laptop you'll have with a old nvidia card. if its not new then I don't hold up much hope of you getting it working, since nvidia seem to be putting their time into vista and other problems (understandable but still lame)

intel chips on the other hand seem quite happy! (if anybody wants a really easy setup, try a packard bell gn45-032. some people don't like packard bell but i dont come across many broken ones. i was kind of disappointed by the number of things i didn't have to hack in heh). currently using a intel 945gm, which is doing a good job of it.

---

### Post by eentonig on 2007-03-28
Intel 945GM display driver on a HP nc6220.

Works perfect under Feisty

---

### Post by mcduck on 2007-03-28
Asus A6Ja with Mobility Radeon X1600, worked great with Dapper and works even better now with Edgy :)

But I had Ubuntu & Beryl in mind when I was selecting the laptop.

---

### Post by ali4949 on 2007-03-28
Did someone say Beryl on Thinkpad T30 with ATI Radeon 7500... excellent news.. since i am running dapper right now and want to wait till the fiesty release is official  I will wait . But once I have upgraded to the new release I ll post my experiences on here. 
System specs..
ATI radeon M 7500 16MB 
Pentium 4 M 1.6 GHz
768 MB PC2100

---

### Post by eitan_a on 2007-03-28
I have the cutting-edge svn Beryl running great on my Sony Vaio VGN-N130G.  It has an intel integrated 945 video card, which is good for linux as the drivers are already open sourced.

---

### Post by A.I. BOT on 2007-03-28
I have beryl-svn running on a Dell Latitude D600 using the ati driver (my card is ATI Mobility Radeon 9000).

---

### Post by russellc on 2007-03-28
I've got Beryl (trevino's repo) running beautifully on my Macbook Pro (Core Duo 2.0 GHz model) which uses the ATI Mobility Radeon X1600 video card.

---

### Post by enlightened on 2007-03-28
I have beryl running nicely on my laptop sony VGN-FE14sp (core duo 1.66, Geforce Go 7400)

---

### Post by NikoC on 2007-03-29
Beryl running smoothly on a sony vaio VGN-S4HP here (nvidia 6200 go).

---

### Post by T31 on 2007-03-29
I got beryl working excellent on fujitsu siemens amilo pi1505  intel GM 950, really fast :)

feisty repos

---

### Post by nrs on 2007-04-01
How is the performance on the Intel cards? I remember trying to use Beryl with my Radeon 7000, 8500, 9600 with the open source drivers & aiglx and the performance was absolutely horrible. The 9600 performed decently with XGL and ATI's proprietary drivers. 

While I'm accustomed to running Beryl on a 6600GT I'm willing to settle for something that renders everything smoothly without any choppiness. This isn't for gaming. 

Is my best bit just to look for a higher end laptop with a decent nVidia card? Or will Intel chips such as the 945 more than suffice?

---

### Post by trevelyn on 2007-04-01
Beryl works great on my recently purchased MacBook!  well, the "Rain" feature wont work but the 3d desktop switching is smooth.. :D

---

### Post by rainwalker on 2007-04-01
What is the SVN Beryl thing? I keep seeing it everywhere but I don't know what it is

---

### Post by greg.hagen on 2007-04-03
SVN Beryl works great on an HP zv5000 and an old Thinkpad x24. It works REALLY well on the old thinkpad, despite the crappy Radeon M6 card.

BTW, SVN means that they are checking it out of the Beryl subversion (svn) software repository. This is the super-bleeding-edge-unstable version. It crashes more often, but we get to see all the cool features before anyone else, like the desktop wall thingie.

---

### Post by Chrisj303 on 2007-04-03
Beryl runs flawlessly on my Macbook - it even runs of the ubuntu ultimate 1.2 Live CD!

---

### Post by trippinnik on 2007-04-03
Yeah it working quite well for me too, Ati M6 LY 8mb card.  In a lot of ways it's faster than using Metacity.  But I did need Xorg 7.2 and the lates Mesa, xorg.conf needed some tweaking too.

---

### Post by ali4949 on 2007-04-10
Hey greg
you said you have beryl running on a IBM Thinkpad T23, I have T30 and was wondering if you could give me some pointers on what are the neccesary steps to install it and make it work. My system specs are IBM T30 , 768 MB RAM, ATI Radeon Mobility 7500 16MB VRAM. Running Edgy, or if anyone else can help me.. I have been reading the forums and there seems to be so much information about XGL AIGLX FGLRX and so on.... which ones do i need to install, which ATI driver, or open source driver. Any ways ne help would be greatly apprecaited
thanks in advance

---

### Post by pingpongboss on 2007-04-11
> **rainwalker said:**
> What is the SVN Beryl thing? I keep seeing it everywhere but I don't know what it is

rainwalker, you could start by going here [http://ubuntuforums.org/showthread.php?t=279456&highlight=Trevi%F1o+beryl](http://ubuntuforums.org/showthread.php?t=279456&highlight=Trevi%F1o+beryl)

---

### Post by bodhisattva on 2007-04-14
I am attempting to get beryl working on a thinkpad t22 if a t23 can do it I am fairly sure my t22 will.   right now I am having hell with the white screen problem.  I f anyone has any tips it would help a lot, thanks a bunch all.

---

### Post by eragorn on 2007-04-14
Beryl working well on an Acer Aspire 7100 with intel 945 chipset.  I am also using the svn repositories , however somewhere along the way I lost all of my eye candy and haven't been able to get it back.  Prolly have to do a fresh install unless someone has a better idea.

---

### Post by anachreon_ on 2007-04-14
Beryl 0.2 works great on my Dell Inspiron 9300 with GeForce Go 6800.  A few niggling problems here and there, but overall very stable.

---

### Post by ali4949 on 2007-04-15
I did get it to work on my T30 with 16MB VRAM but the fonts were getting really choppy. coudnt get the cube effect to work.. I uninstalled it for the time being and will try again with fiesty fawn. One question though.. does having more system ram help increase the performance of beryl/compiz or is totally dependant on the video ram and GPU rendering the effects.
thanks

---

### Post by qamelian on 2007-04-15
> **igknighted said:**
> With Dapper it will be difficult.  If beryl is your bag, I would try Edgy or Feisty when it comes out.  With Dapper you must use XGL, which is (1) a pain to set up, and (2) Doesn't let your run apps like google earth or anything else 3d.  If you have an ATI card it doesn't really matter as XGL is your only option anyway, but if you have nvidia or intel on your laptop, then look into upgrading.

Just stumbled on this thread and I gotta say this info is completely wrong. I've used Beryl on my laptop with an ATI Mobility Radeon 9000 IGP since Dapper. XGL is most assuredly not necessary; it works fine with AIGLX and the open-source ATI/Radeon drivers. And Google  Earth also ran fine as did other 3D apps.

---

### Post by greg.hagen on 2007-04-15
> **ali4949 said:**
> Hey greg
you said you have beryl running on a IBM Thinkpad T23, I have T30 and was wondering if you could give me some pointers on what are the neccesary steps to install it and make it work. My system specs are IBM T30 , 768 MB RAM, ATI Radeon Mobility 7500 16MB VRAM. Running Edgy, or if anyone else can help me.. I have been reading the forums and there seems to be so much information about XGL AIGLX FGLRX and so on.... which ones do i need to install, which ATI driver, or open source driver. Any ways ne help would be greatly apprecaited
thanks in advance

i have it running on an x24, but it sounds like the hardware is similar. There are plenty of great guides on the beryl website and in the forums. I can give you pointers if you get stuck. I recommend the open source drivers and AIGLX. Both are in Ubuntu Edgy and above. Using AIGLX and the opensource drivers is the easiest and fastest way to get it working if you have an ATI card. I've added this thread to my subscriptions so just post here if you hit a snag.

---

### Post by nanog on 2007-04-15
beryl 0.2 is very pretty on my dell e1405 and  toshiba A70

---

### Post by NeoTaoistTechnoPagan on 2007-04-24
Just installed on my Compaq Presario C304NR with Intel 945GM/GMS/940GML video. Very impressive!

Side note - this system is running from an external USB HDD - wifey will not let me put *nix on the main since she's stuck on mickeysoft.


Hail the Holy Motherboard!

Polk Linux Users Group
[www.mypc.is-a-geek.com](www.mypc.is-a-geek.com)

---

