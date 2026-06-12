---
title: "Gutsy, ATI AIW 9800 pro, XGL, fglrx, Compiz, vnc, 100% cpu..."
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by Maddmaxx on 2007-11-06
Okay, through numerous attempts to repair the issue I can't seem to make it stop. There are too many threads running with different configurations, so I'd like to customize. I'm running an IBM P4 2.4 GHz on Gutsy with an All In Wonder 9800 Pro.  I have the latest ATI driver installed with the desktop effects enabled, and they work fine, when I start up, all effects work well... the only issue is that when I use vnc, the process XGL uses whatever remainder of cpu power that is left over from any processes, for example if vino-server or puseaudo or firefox-bin use 70% then xgl uses 30%, but if no other process is using the juice then XGL uses 99%. 

Here's the catch, I am aware that by using a remote desktop connection (vnc) with enhanced desktop effects running, it will tax the network to the nines, even though my network speed still isn't maxed out. It does in fact max out the CPU though. I like having the effects when I'm operating at home (works fine when not using vnc), but on the vnc connection when I'm away from home it has this issue. The issue then is when I'm away and operating vnc, just disabling desktop effects doesn't solve the problem. Is there a way I can make the vnc connection act as a very basic gnome screen while enabling effects on my home monitor? Even by switching back and forth, or using a different program to remote in? I wish I would have just left it alone, and since it everything works so well, i'm not about to go and reverse everything I did to get it working... I'll end up with a giant splitting headache! 

I hope you all get what I'm talking about, and I hope I gave enough information without being too confusing... Any help would be greatly appreciated!

---

### Post by Maddmaxx on 2007-11-17
bump?

---

### Post by CTho9305 on 2008-03-01
I see the same thing - when I connect to my session with a VNC client, one of my CPU cores gets pegged by Xgl.  Fortunately I have a dual-core CPU, so it's still usable, but it's not ideal (my PC also puts out a LOT more heat when that's going on).  HD 2900 XT with the the latest driver from ATI's website.

---

