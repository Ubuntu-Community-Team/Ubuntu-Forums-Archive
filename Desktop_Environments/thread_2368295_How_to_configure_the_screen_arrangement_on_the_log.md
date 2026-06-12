---
title: "How to configure the screen arrangement on the login screen?"
date: 2017-08-09
forum: Desktop Environments
---

### Post by im0nkey on 2017-08-09
Dear community,

after years of only using linux systems for servers (I'm not an  expert)  I decided to give Ubuntu/Kubuntu another chance to replace  Windows. 


  I have got a multi monitor setup. One display is connected via HDMI   and my primary display is connected via Displayport. The configuration   of the display arrangement after the login screen works fine, but it is   not applied to the the login screen. [IMG]https://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]

  I researched a lot to fix this problem, but did not find an   appropriate solution. The threads and articles I found are outdated or   does not apply to the standard Ubuntu/Kubuntu installation. Also, this   problem is present in Ubuntu and Kubuntu 16.04. I tried both.


  As far as I read this bug is present in Ubuntu/Kubuntu/etc. since a   long time. I don't want to complain, but how can such a big bug not be   fixed in such a long time in a distribution which wants to replace   Windows as desktop operating system? I don't want to be rude, because   most people are improving linux and Ubuntu in their free time, it's just   that I can't understand it.


  Anyway, their are solutions for this problem using lightDM, but   correct me if I'm wrong. LightDM is not used in standard installation of   Ubuntu/Kubuntu, right? Nevertheless I tried to fix this via lightDM  and  did not work for my, but after removing lightDM again, the display   arrangement was fixed... So I guess their has to be appropriate  solution  for this problem and I hope someone can explain it to me and  all the  user other user, which have this problem.


  Greetings 
im0nKeY

---

### Post by deadflowr on 2017-08-09
> LightDM is not used in standard installation of Ubuntu/Kubuntu, right? 
Ubuntu and Kubuntu are two completely different things.
Ubuntu does use lightdm, but Kubuntu may not. (seems to change depending on the weather, I think it currently uses sddm, or maybe they went back to kdm?)

So determine which you are actually running, Kubuntu or Ubuntu.
Then it may be easier to figure out a solution.

It would also be helpful to know the release version, as in is it 14.04 or 16.04 or 17.04?
(Setup changes can happen, so where one release may have one way of doing things, the next release may have changed that)

---

