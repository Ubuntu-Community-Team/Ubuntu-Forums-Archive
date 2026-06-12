---
title: "Pinball project for linux."
date: 2011-03-03
forum: Gaming &amp; Leisure
---

### Post by ynneb on 2011-03-03
I am a keen user of [Visual pinball]("http://www.vpforums.org/index.php?showforum=7"). Unfortunately this means I have to continue to use Win XP.
I am trying hard to become a full time user of Ubuntu, but there are certain softwares that continually draw me back to Windows.

The source code for [Visualpinball]("http://www.vpforums.org/index.php?showforum=7") has now been made [open source]("http://sourceforge.net/projects/vpinball/").
There are 33,000 registered VP members on a VForum that is only 2 years old.This demonstrates the interest.

Is it possible to port the code into Linux?
Surely this would be a boon for Ubuntu?
Please dont point me to Emilia Pinball, I am aware of it already.

I would love to see a linux pinball emulator that is the absolute superior pinball emulator available. Not been a coder myself, how would I get such a project off the ground?
The users build the actualtables and distribute them. VP is just the player and desiging platform only.

[Check out this video sample of what I am talking about...]("http://www.youtube.com/watch?v=44WfGT0ElVk")
[http://www.youtube.com/watch?v=44WfGT0ElVk]("http://www.youtube.com/watch?v=44WfGT0ElVk")

---

### Post by pieman711 on 2011-03-03
Can't really say much about the port but have you tried installing it under WINE? It's not the ideal solution but may stop you having to boot windows until the project gets off of the ground.

---

### Post by ynneb on 2011-03-03
Thanks for your response Pieman. I was afraid this post might end up in the abyss within 24 hours.You bumped it nicely for me.

I did try it under Wine and it fails completely.
I was actually hoping for a ported version that people got excited about, and promoted it as a gaming flagship for linux. :)

---

### Post by iheartubuntu on 2011-03-03
ynneb, Future Pinball works great using Wine and is also used by many who use Visual Pinball.

Do you have a 3D video card that can support FP? You can check by opening a terminal and typing:

```
glxinfo | grep direct

```

If 3D is working it will say "direct rendering: Yes"

Install info of FP in Ubuntu here:
[http://fprelease.free.fr/fpwine/](http://fprelease.free.fr/fpwine/)

TONS of incredible pinball tables here:
[http://www.pinsimdb.org/fpreleases/](http://www.pinsimdb.org/fpreleases/)

EDIT: 
here is the Future Pinball site: [http://www.futurepinball.com/](http://www.futurepinball.com/)

Also, the GoPinball forums should help you if you have any probs.

[http://www.gopinball.com/forum/](http://www.gopinball.com/forum/)

---

### Post by ynneb on 2011-03-03
Thanks for your response iheartubuntu.
Yes I have used FP but the physics are not at good as VP
Not only this,FP is not open source and requires WINE to operate.
I really do like the open GL aspect of FP though.
I was hoping for a new and #1 pinball format written especially for Linux that combined the best of FP and VP and was also open source.
How do I go about getting programmers interested in doing this?
Any ideas?

---

### Post by iheartubuntu on 2011-03-03
Im guessing its too big of a project for an indie team to put together. There is also not a lot of interest in a pinball game (compared to say WoW or Call of duty).

If you want to give FP a try still the current download is here:

[http://www.gopinball.com/media/FuturePinballSetup_v1.9.1.20101231.exe](http://www.gopinball.com/media/FuturePinballSetup_v1.9.1.20101231.exe)

Older versions of FP would expire, but not this version above.

It installed fine for me with the current release of Wine without having to follow any special steps from the above links. The GoPinball site is great with many of the same tables as you use in VP. Its about the best case scenario for Ubuntu users who dont want to use Windows anymore. Sorry cant be much more help.

---

### Post by tommcd on 2011-03-04
There is already a pinball game in the Ubuntu repositories: [http://packages.ubuntu.com/maverick/pinball](http://packages.ubuntu.com/maverick/pinball)
I have the Emilia-Pinball installed on my Lubuntu 10.10 32bit install and it works very well. It might not be as fancy as Future Pinball or some of the others; but it is a native linux pinball game and it is available right now.

I still like playing pinball. I am old enough to remember the time when there were no video games of any kind. This is the time even before the Space Invaders and Asteroids games came along. In those days pinball was the only game in town.

---

### Post by Perfect Storm on 2011-03-04
There's also Roll'em Up for Linux.

---

### Post by thenickrulz on 2011-03-04
This would be cool!!!:D

---

### Post by ynneb on 2011-03-04
I have created a dedicated forum to help revive Linux Pinball.
Please help support the project by registering. You will then be notified of all new developements.

[http://linuxpinball.freeforums.org/index.php](http://linuxpinball.freeforums.org/index.php)

Regards Benny

---

### Post by LinuxFox on 2011-03-04
I never played Visual Pinball, but I might play it from time to time if there was a pinball game for Linux.  I really enjoy pinball games, so if there was something for Linux, I wouldn't mind playing it.

I know there's Emilia Pinball, but I wasn't too crazy about it when I tried it.

---

### Post by Bölvaður on 2011-03-04
Went through the code and their license and think it smells of windows guys that do not write portable code. I have no experience with visual studio but this project seems to be focused as that is the only IDE that you are supposed to use. Could be portable though, only skimmed over the code

---

### Post by ynneb on 2011-03-04
Thanks for taking a look at the code Bölvaður.
Maybe the code can be used as a concept only for a new cross platform version?

---

### Post by Bölvaður on 2011-03-06
> **ynneb said:**
> Thanks for taking a look at the code Bölvaður.
Maybe the code can be used as a concept only for a new cross platform version?
im not saying it might not be possible to rewrite few parts of the code to make everything work. I just dont have enough experience with what they are using and only skimmed over the code and noticed how obvious it was they are relying on visual studio only.

---

