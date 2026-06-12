---
title: "Fglrx performance issue in quake4 and 3d games"
date: 2006-11-19
forum: Gaming &amp; Leisure
---

### Post by Icarosaurus on 2006-11-19
I've just been able to install Quake 4 in my Edgy, following the directions found here:
[http://zerowing.idsoftware.com/linux/quake4/]("http://zerowing.idsoftware.com/linux/quake4/")
Now, my fglrx, 8.28 works fine, DRI is enabled and everything should be fine.

Sound works better than in windoz, but graphics is a little slower and, above all, graphics quality is not as in windoz...it seems textures are not detailed, even when i set details to "high"

My question is this: is there some tweaking in xorg.conf or elsewhere that i can do to make things go better???

I've got an ATI Radeon 9600ez...

---

### Post by Muty-bg on 2006-11-21
HI I have a mobility radeon 9700 in my alienware notebook, and so far it has been a real nightmare for me. The screen turns white on logout/login/restart. But the system looks responsive on the background, because I can connect to it with ssh. Only restart turns the screen back to normal. Same with suspend.  Also gamses seem to run properly sometimes and sometimes they work awfuly. Like if I start ut2004 and play it runs with 40-50 fps. Reboot start it again and it's running with 10-15. I'm verry pissed at ati. I'm trying to slove this for months and with every new driver release it's  the same. I tried it with 3 different distros(gentoo, Slackware, Ubuntu) and absolutly the same. I've spammed their customer support numerous times and the only thing I get as a reply is a link to the driver download page. I really hope that AMD will put some order. And I really hope the rumors I hear about opening the specifications for radeons to be true. 

I know I'm not helping you very much but atleast you are not alone.

---

### Post by scotty2hott2k on 2006-11-22
i think its ati drivers tbh, norotiously bad drivers for linux, if you want to game nvidia is the only way forward.

---

### Post by rekahsoft on 2006-11-22
> **scotty2hott2k said:**
> i think its ati drivers tbh, norotiously bad drivers for linux, if you want to game nvidia is the only way forward.

unfortunately this is true :( fglrx (ati's horrible proprietary driver) is not up to par. There are only two current solutions to your problems:
1. install the latest driver from ati (fglrx 8.31.5) and hope for some performace improvements
2. buy nvidea graphics cards

Long term solutions:
1. Since ATI has been bought by AMD it looks like many improvements will be made on the linux front. Let AMD know. AMD might open-source fglrx. Until so support Open-source solutions (the mesa drivers). Although the open-source drivers may not be as good as fglrx you are supporting open-source and the development of better open-source software. If you are a developer capable of contributing then contribute. Push AMD to open-source fglrx.

---

### Post by Icarosaurus on 2006-11-23
Of course, fglrx runs bad...
I noticed that making Quake4 choose the video settings itself solved the problem of bad texture quality.
I'd like to try UT2004 under linux 'cause it runs very very smooth in windoz and I like it very much.
The best way for running Quake4 for me is 640x480...running UT2004 1024x768 and over at maximum graphics causes non problems at all...

Anyway, yes, we all hope that AMD will solve the problem, seen that linux users number is growing each day.

rekahsoft: I'm afraid of trying the new drivers...I had troubles with 8.30 on  setting video modelines and...using Windoz as a Wintendo, for now is not bad for me. But it really seems that gaming is the last wall before making linux occupy all my disk partitions :-)

But the question is:
**what's the best xorg.conf setting for an ATI radeon 9600?**

Bye all, and thanks for your replies!

---

