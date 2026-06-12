---
title: "Watching video through HAL DRM (Flash related)"
date: 2015-04-01
forum: Gaming &amp; Leisure
---

### Post by Ertai87 on 2015-04-01
Hi guys!  I need some help getting Flash to work on my Ubuntu install.  Specifically, I'm trying to watch video on a site that uses some sort of Flash DRM called HAL.  I understand the problem is basically that the Ubuntu Flash plugin (even the one on Chrome) doesn't support HAL, while the Windows one does.  I read about a workaround using a plugin called Pipelight, which I installed, but unfortunately to no avail.  It's possible I configured Pipelight wrong, but I followed a guide so I think I did it right.  Can someone help me debug this issue?  There's some TV programs I'd like to watch through official sources rather than having to find sketchy 3rd party sites and deal with the issues that arise with those.

Thanks!

---

### Post by ajgreeny on 2015-04-01
I do not have any experience with pipelight but I have added the ppa for installing the zombie HAL package
[https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal](https://launchpad.net/~mjblenner/+archive/ubuntu/ppa-hal)

Give that a try and see if it helps; it certainly allows me to watch 4oD, an online TV catch-up service in the UK, which without HAL just gave a continuous spinning icon but no video.

---

### Post by Ertai87 on 2015-04-04
I added the PPA and installed the package (I only installed the package, i.e. "sudo apt-get install hal", I didn't do anything else), but it didn't work.  Here's what I tried, and the results; maybe I'm doing something wrong that you can help me with:

Website used: ctv.ca, watching a confirmed unlocked video:

1) Firefox, Pipelight disabled: Would not play (claimed I needed a Flash update).
2) Firefox, Pipelight enabled: Would play ads, would not play main video.  Instead I got a black screen when the ads ended, although before the ads started it showed a scroll bar for the video, indicating the video had loaded.
3) Chrome, Pipelight disabled: Would not play (Flash update).
4) Chrome, Pipelight enabled: Would not play (Flash update).

When I tested it before (a couple days ago when I made this thread) it would play the ads in Chrome whether Pipelight was enabled or not.  However it appears CTV has updated their site since then (it has a new UI), so it could be that too.  Any suggestions would be more than welcome =D

(That said, I recently started a new job IRL and I'm super busy with that, so I may not respond for a couple days if a new suggestion comes in...sorry about that :( )

---

### Post by kerry_s on 2015-04-04
went there, tried some vids, there geo region locked, otherwise they looked like they would play. i'm using chrome, didn't install nothing.
i would suggest trying a vpn to get you in the right geo region

---

### Post by Ertai87 on 2015-04-04
> **kerry_s said:**
> went there, tried some vids, there geo region locked, otherwise they looked like they would play. i'm using chrome, didn't install nothing.
i would suggest trying a vpn to get you in the right geo region

Unfortunately discussing this vein of conversation further is apparently against the CoC of Ubuntu Forums.  Can I contact you some other way to discuss this? (Sorry mods, I hope this is alright please don't lock my thread again T_T)

---

### Post by kerry_s on 2015-04-04
> **Ertai87 said:**
> Unfortunately discussing this vein of conversation further is apparently against the CoC of Ubuntu Forums.  Can I contact you some other way to discuss this? (Sorry mods, I hope this is alright please don't lock my thread again T_T)

how about i just point you to the docs. [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

google is going to be your best friend on this.

---

### Post by Ertai87 on 2015-04-04
> **kerry_s said:**
> how about i just point you to the docs. [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

google is going to be your best friend on this.

There are complicating factors that I'd like to discuss with you off this thread, if you wouldn't mind.  I'm not sure that solution will work for my situation; it's likely it will, but before I do that and assume it'll just work I'd like more information I can't ask about here.

---

### Post by Bucky Ball on 2015-04-04
*Thread closed.*

It appears you already know why. From the Code of Conduct.

> We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings. 

Please respect this and post no further regarding this activity. Thanks.

---

