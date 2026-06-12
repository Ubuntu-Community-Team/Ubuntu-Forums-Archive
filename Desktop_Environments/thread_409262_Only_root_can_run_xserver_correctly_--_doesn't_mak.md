---
title: "Only root can run xserver correctly -- doesn't make sense to me"
date: 2007-04-14
forum: Desktop Environments
---

### Post by JackD on 2007-04-14
I've been setting up some Edubuntu systems for games that would appeal to high schoolers (Tremulous, BZFlag, etc.) and I thought I might try and improve the video response time. Vega Strike is very slow on the systems (Compaq Evo N600c, PIIIs with .5 G RAM and ATI Mobility driver).

Well, optimizing the video turned out to be much trickier than expected and the consequence was a misconfigured xorg.conf.

I started in runlevel 1 and through dpkg-reconfigure xserver-xorg and X -configure got everything restored and the system works great ! But **only** for my root. 

When I login from any other account, the resolution is all off and the systems locks up (no going to CTRL-F1) 

I checked, and there is no .xinitrc file in the home directory of other accounts (or even in  the root).

So, I'm stuck. 

Any ideas on how to get my other accounts working with the X server?

---

### Post by JackD on 2007-04-14
Well, I made a sloppy fix because I'm too impatient to fix the root problem (not a pun). I copied out the files I wanted to keep, deleted my user account, and recreated it. Copied back in the files. Works fine, but it makes me feel more like a helpdesk troll than someone adept.

---

