---
title: "Fullscreen glitch on Jaunty/FGLRX"
date: 2009-05-01
forum: Desktop Environments
---

### Post by bakhy on 2009-05-01
Hi!

After upgrading to Jaunty a couple of days ago, desktop effects, although generally working ok, are showing some strange glitches.

Some animations pause for a fraction of a second, which they didn't do on 8.10, and whenever an app is in fullscreen, and a window gets opened (for example, opening a popup menu in firefox, or Songbird or aMSN notification popups, or even tooltips..), the screen shows the desktop wallpaper for a short time, before going back to the fullscreen app. This is particularly annoying when watching videos. And this also didn't happen on 8.10.

Installing last month's Catalyst driver made no difference.

---

### Post by KhurramM on 2009-05-01
It seems, you have got old hardware.

Its the new X detection system, which is failing for older hardeware.

Try to put the working xorg.conf of your old ub, and see if it works.

Do back up original xorg.conf file first.

Hope u get this resolved.

---

### Post by bakhy on 2009-05-01
ATI Mobility Radeon HD 3470.. don't know how old that is :)

---

### Post by Operan on 2009-05-01
Whenever I maximized or switch to fullscreen a video player (Mplayer, Totem, VLC, XIne...), the screen immediately get black after few errors appears in console ( they disappears after 1,2 seconds ). Any keys doesn't work. The only thing I can do is reset my computer with power button. Please tell me what is error and how to fix it?
I'm using Jaunty, too. My machine is Dell Studio 1535 with ATI 3450 graphic card and graphic driver has been installed.

---

### Post by KhurramM on 2009-05-01
Hi Operon

Try on cli:

xrandr -q

try to reduce your XxY or the frequency, ***_that matches your monitor's display_***

use eg (but one of the values specified from xrandr -q):

xrandr -s 1024x768 -r 60 (just an example)

Hope this helps.

---

### Post by Operan on 2009-05-02
> **KhurramM said:**
> Hi Operon

Try on cli:

xrandr -q

try to reduce your XxY or the frequency, ***_that matches your monitor's display_***

use eg (but one of the values specified from xrandr -q):

xrandr -s 1024x768 -r 60 (just an example)

Hope this helps.
Thanks for your help. But it doesn't work for me!

---

### Post by Parp on 2009-05-02
I'm having the same issues (ATI HD3450), also when searching the forums I've found a lot of other people are having this problem. If I disable compiz it's better, but still a little laggy.. however it's better than 9.10 as at last I play video without flicker.. (I was only running on 8.10 on this machine a short while before upgrading to jaunty beta, my old machine was fine for all graphics as it was an Nvidia card...)

---

### Post by bakhy on 2009-05-02
Ok, I feel like I should maybe apologise :) I found this simple checkbox that fixed te darn thing.

In the CompizConfig tool, under "General Options", there's this option called "Unredirect fullscreen windows" (what a great name, btw ;)). Turning it off made fullscreen mode behave perfectly again.

Also, the animations seem to have improved a little after I've lowered the "Animation Time Step" option from 10 to 8 (that's under "Animations", "Effect Settings" tab), but I'm not sure if I'm not just imagining this one.

Anyway, sorry for abusing the forum with my noobness. Hope someone else finds this useful.

---

### Post by bryonak on 2009-05-02
Just posting to say thank you, bakhi!

I noticed the same while playing movies and calling the menu, but brushed it off as Compiz struggling with GNOME (which it is, in fact)...
Silly thing they turn such options on by default. Anybody knows what the benefits would be?

---

### Post by Operan on 2009-05-07
> **bakhy said:**
> Ok, I feel like I should maybe apologise :) I found this simple checkbox that fixed te darn thing.

In the CompizConfig tool, under "General Options", there's this option called "Unredirect fullscreen windows" (what a great name, btw ;)). Turning it off made fullscreen mode behave perfectly again.

Also, the animations seem to have improved a little after I've lowered the "Animation Time Step" option from 10 to 8 (that's under "Animations", "Effect Settings" tab), but I'm not sure if I'm not just imagining this one.

Anyway, sorry for abusing the forum with my noobness. Hope someone else finds this useful.
Unfortunately, it doesn't work for me!

---

### Post by VladimirCZ on 2009-05-08
There is a bug reported in launchpad:
"...notify-osd applet makes my screen blink for a second when an application is in full screen"
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/346187]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/346187")

---

### Post by frunns on 2009-05-23
> **Operan said:**
> Unfortunately, it doesn't work for me!

Probably because you didn't have the same issue. Hope you've found a solution that works for you though!

Great thread, just was I was looking for, hopefully it works for me.

---

### Post by itsjareds on 2009-09-17
> **bakhy said:**
> Ok, I feel like I should maybe apologise :) I found this simple checkbox that fixed te darn thing.

In the CompizConfig tool, under "General Options", there's this option called "Unredirect fullscreen windows" (what a great name, btw ;)). Turning it off made fullscreen mode behave perfectly again.

Also, the animations seem to have improved a little after I've lowered the "Animation Time Step" option from 10 to 8 (that's under "Animations", "Effect Settings" tab), but I'm not sure if I'm not just imagining this one.

Anyway, sorry for abusing the forum with my noobness. Hope someone else finds this useful.

I found this very useful, it's been bugging me for a long time whenever I tried to use F11 in apps. Works great. Thanks.

---

### Post by xsyne on 2009-10-29
Worked out great for me too, thanks.

---

