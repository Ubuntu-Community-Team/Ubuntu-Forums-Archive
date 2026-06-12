---
title: "Thinking of Buying a dell xps M1330"
date: 2008-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by searayman on 2008-05-06
I was thinking of buying the dell xps M1330 with Ubuntu installed. I have been using Ubuntu for a little over 4 years on my desktop and no my way around it pretty well, and really want a laptop.

So I have some questions concerning the basic xps m1330 before I buy it. I come stranded with a Intel® Integrated Graphics Media Accelerator 3100.

I wanted to know how that runs compiz fusion? Would I have any problems running it at all on that? Or should I upgrade to the nvidia for $100?

Also what is the better time like on the xps? It comes standard with a 37Whr Lithium Ion Battery (4 cell). How long would that batter last on one charge? Also how is it compared with the 56Whr Lithium Ion Battery (6 cell)

Thanks for all your help!

---

### Post by Mattaus on 2008-05-06
I'm living in Australia so this may not be 100% accurate but I think the machines are almost identically spec'd. Basically I myself am looking at purchasing a M1330 VERY soon and from my research I've learnt that it's defintely worth upgrading to even the base nvidia option for graphics so long as you intend on using it for something. If your not going to bother with Compiz or even run the very basics of games then the X3100 is fine, otherwise - get at least the nVidia 8400GS (or whatever the lowest option in America is) Not just performance but also ease of use as apparently the nVidia drivers are a little bit more friendly...

As for battery life I've read a number of reviews and the unit got some pretty good marks in that area. Obviously the larger battery will provide more time - its just up to you to make sure you have the right one on you!

This all been said my experience with Linux on laptops is non-existant and from what I've heard you need to take some measures to ensure the system runs as efficiently as possible. Nothing you can't find out about in these forums somwhere!

---

### Post by searayman on 2008-05-06
> **Mattaus said:**
> I'm living in Australia so this may not be 100% accurate but I think the machines are almost identically spec'd. Basically I myself am looking at purchasing a M1330 VERY soon and from my research I've learnt that it's defintely worth upgrading to even the base nvidia option for graphics so long as you intend on using it for something. If your not going to bother with Compiz or even run the very basics of games then the X3100 is fine, otherwise - get at least the nVidia 8400GS (or whatever the lowest option in America is) Not just performance but also ease of use as apparently the nVidia drivers are a little bit more friendly...

As for battery life I've read a number of reviews and the unit got some pretty good marks in that area. Obviously the larger battery will provide more time - its just up to you to make sure you have the right one on you!

This all been said my experience with Linux on laptops is non-existant and from what I've heard you need to take some measures to ensure the system runs as efficiently as possible. Nothing you can't find out about in these forums somwhere!

I don't plan on gaming much if at all. But i do plan on using compiz fusion, so will the intel one work just fine for me?

---

### Post by Mattaus on 2008-05-06
The intel chip set SHOULD work yes. I'd hold off a bit and see if anyone has experience with that chip first.

Just search the forums for anything to do with the X3100. I gaurentee someone will have asked the same question already. Actually I even did a while ago but for my needs it was too under powered so we never really discussed its compiz ability.

---

### Post by akniss on 2008-05-06
I have the m1330 and just upgraded to 4 GB of ram and installed 8.04 (32-bit) on it.  I have the X3100 graphics, and it runs compiz flawlessly with 4 GB of ram.   Even when I had 2 GB of ram and was running Gutsy, Compiz ran very well.

On the 4 cell battery, I get almost exactly 2 hours of battery life while doing normal stuff (internet browsing, word processing, wifi on the whole time).  I don't have the 6 cell battery, but on the 9-cell, I get a little over 5 hours, so I imagine the 6 cell battery would be somewhere in between.

---

### Post by notwen on 2008-05-07
The Intel X3100 is blacklisted in Gutsy, but works w/o any issue in Hardy.  My Inspiron 1420n has the X3100 chipset and I'm currently bypassing the blacklist and still using Compiz-Fusion, more for the expo effect than anything else, but this can introduce some video playback issues which can also be resolved w/ some minor settings change sin your preferred video player(I use VLC).  So I don't see any reason to upgrade your vid card if you're simply wanting Compiz-Fusion.  Just know that the X3100 will be using some of your system's memory.  I have 2GB of ram and never see graphical slowdowns for basic usage.(ie. surfing, media playback)  

My Inspiron 1420n has a 9cell battery that gets just over 4 hrs of usage.  I generally play music, surf and watch videos on my laptop and still manage 4 hrs give or take.  I would highly recommend upgrading the battery over the graphics if you had to choose.  

Hope this helps w/ your decision and I applaud you in supporting Dell's pre-installed Ubuntu systems.  You may want to contact a Dell CSR and see how soon the N-Series systems will start shipping w/ Hardy Heron to save yourself some work and worry regarding the Compiz-Fusion/Intel X3100 chipset/Gutsy issues.  Be sure to post back and update us on your status.  =]

---

### Post by AgudeloAndres on 2008-05-07
> **akniss said:**
> I have the m1330 and just upgraded to 4 GB of ram and installed 8.04 (32-bit) on it.  I have the X3100 graphics, and it runs compiz flawlessly with 4 GB of ram.   Even when I had 2 GB of ram and was running Gutsy, Compiz ran very well.

On the 4 cell battery, I get almost exactly 2 hours of battery life while doing normal stuff (internet browsing, word processing, wifi on the whole time).  I don't have the 6 cell battery, but on the 9-cell, I get a little over 5 hours, so I imagine the 6 cell battery would be somewhere in between.

Hi Akniss.

Would you show me how to configure Compiz-fusion on Ubuntu 7.10. ?? I have done everything to make it run , but it won't run on my Dell XPS M1330 with X3100 graphic chip.

Thanks in advance.

---

### Post by notwen on 2008-05-07
> **AgudeloAndres said:**
> Hi Akniss.

Would you show me how to configure Compiz-fusion on Ubuntu 7.10. ?? I have done everything to make it run , but it won't run on my Dell XPS M1330 with X3100 graphic chip.

Thanks in advance.

Try the following command in a terminal:

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

Restart X using ALT+CTRL+Backspace or a simple reboot works as well.  This can all be seen here on [Dell's Linux Wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility").  Refer to my sticky here in the Ubuntu Dell sub-forum.  Post back if you have any issues.  =]

---

### Post by akniss on 2008-05-07
> **AgudeloAndres said:**
> Hi Akniss.

Would you show me how to configure Compiz-fusion on Ubuntu 7.10. ?? I have done everything to make it run , but it won't run on my Dell XPS M1330 with X3100 graphic chip.

Thanks in advance.

Info can be found in this post:
[http://ubuntuforums.org/showpost.php?p=3614750&postcount=2](http://ubuntuforums.org/showpost.php?p=3614750&postcount=2)

---

### Post by zorba_the_greek on 2008-05-07
> **searayman said:**
> I was thinking of buying the dell xps M1330 with Ubuntu installed. I have been using Ubuntu for a little over 4 years on my desktop and no my way around it pretty well, and really want a laptop.

So I have some questions concerning the basic xps m1330 before I buy it. I come stranded with a Intel® Integrated Graphics Media Accelerator 3100.

I wanted to know how that runs compiz fusion? Would I have any problems running it at all on that? Or should I upgrade to the nvidia for $100?

Also what is the better time like on the xps? It comes standard with a 37Whr Lithium Ion Battery (4 cell). How long would that batter last on one charge? Also how is it compared with the 56Whr Lithium Ion Battery (6 cell)

Thanks for all your help!

I got this laptop and I am completely satisfied!!
I 've bought the nVidia Graphic Card and everything works perfect.
About the battery, buy the 9 cell (not even the 6 cell). The difference on money is too small and 9 cell battery can keep me working up to 4.5 hours sometimes...:guitar:

---

### Post by thorcik on 2008-05-08
and I get about 3 hours on the 6-cell, I have currently 2:45 left and charged in 88%, wireless on and brightness almost at lowest level.

---

### Post by limesmoothie on 2008-05-08
I've got this machine (product Red version) and have upgraded to the Nvidia. 

Its excellent, well worth the spend. When I bought it (late 07), we couldn't choose Ubuntu as an option here in the UK, so it came with Vista home premium, but that's no longer in use :)

I've got the six cell and usually get about 3 hours out of it. I didn't opt for the nine cell due to weight/bulk issues (maybe that was just my perception but I have to cart it around all over the UK).

---

### Post by nightfrost on 2008-05-09
Definitely go for intel X3100.
It runs compiz _very_ well. I mean, I run compiz on another laptop which has the age old 855GM chipset. The old laptop will not play games, but it sure can run compiz. As long as you don't need to play games (which I believe you stated that you don't), then support intel as they support open source.

Also, you will have longer battery life with an intel.

---

### Post by IamReck on 2008-05-09
This is the laptop I plan on getting... this thread was very help ful.  How is it from a weight standpoint with the 9-cell battery?

---

### Post by olavjunior on 2008-05-18
I'm thinking of the same thing, buying a Toshiba with integrated intel graphics. I wan't to run compiz, but it's also important that it can play hd-movies flawlessly. Is that a problem with intel graphics?

And are you sure it's not blacklisted in Hardy? [http://www.realistanew.com/index.php?s=3100](http://www.realistanew.com/index.php?s=3100)

---

### Post by IamReck on 2008-05-18
You have another option for a graphics card when buying an XPS M1330.  The 128MB NVIDIA® GeForce&#8482;  8400M Graphics Card.  I haven't heard anything about it though.

---

### Post by nightfrost on 2008-05-19
> **olavjunior said:**
> I'm thinking of the same thing, buying a Toshiba with integrated intel graphics. I wan't to run compiz, but it's also important that it can play hd-movies flawlessly. Is that a problem with intel graphics?

And are you sure it's not blacklisted in Hardy? [http://www.realistanew.com/index.php?s=3100](http://www.realistanew.com/index.php?s=3100)

I am 100% certain it's not blacklisted, as I'm using it right now :-)

---

### Post by olavjunior on 2008-05-19
> **nightfrost said:**
> I am 100% certain it's not blacklisted, as I'm using it right now :-)

Great! :) But how is it doing on movies? Do I need a seperate card like nvidia to watch hd-movies? I'm using my laptop to watch movies on a projector alot...

---

### Post by nightfrost on 2008-05-19
> **olavjunior said:**
> Great! :) But how is it doing on movies? Do I need a seperate card like nvidia to watch hd-movies? I'm using my laptop to watch movies on a projector alot...

That, I do not know. There's a HDMI port on the laptop, but I've never used it, and have no clue how it works under linux. Try google, I'm sure quite a few people running linux have bought this laptop.

---

### Post by olavjunior on 2008-05-19
I've googled a bit, and it seems that nvidia doesn't support hardware acceleration for playing movies, so it all depends on the cpu. So if that's the case, then I really don't need an nvidia card. Am I right? Feeling totally noobish on this

---

### Post by gkkg on 2009-04-02
Sorry if I resurrect a thread that has been dead for about a year now, but I would really like to get an answer for olavjunior's last question "it seems that nvidia doesn't support hardware acceleration for playing movies, so it all depends on the cpu. So if that's the case, then I really don't need an nvidia card. Am I right?"

Can anyone confirm this? Would there be any difference between Intel and Nvidia in terms of playing HD movies? Or using the HDMI port in general?

---

### Post by nwadams on 2009-04-02
i cant' speak for everyone else but i find watching movies and using the HDMI works fine with my intel chip (on my xps m1330)

---

