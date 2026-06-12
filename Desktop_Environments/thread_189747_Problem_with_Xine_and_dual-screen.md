---
title: "Problem with Xine and dual-screen"
date: 2006-06-05
forum: Desktop Environments
---

### Post by markkun on 2006-06-05
This problem appeared as I upgraded breezy to dapper. When I play a video (AVI/DVD) in my monitor everything is fine. When I move my mouse to my tv screen that is 32" and from there I start Kaffeine (or MPlayer) and open any AVI or DVD, player crops most of the picture's image away.

I think Xine takes my screen size from monitor 1 that is 1280x1024 and uses that to play video in my monitor 2. So result is that part of the picture is missing.

My setup is Ati radeon 9600 with dual-screen. Xinerama option doesn't work perfectly, so I don't use it. So basically I have one computer splitted to two desktops.

Does anyone know how to fix this?!

---

### Post by markkun on 2006-06-06
I altered xorg.conf so that xinerama worked (buggy though)... still nothing. Also I added monitor size to xorg.conf and that didn't help.

I really begin to be out of ideas how to fix this. If it is even fixable for normal users. Can I use Kaffeine with anything else than xine?

---

### Post by markkun on 2006-06-08
anyone?

Didn't even help when I switched my monitor to 1024x768...

---

### Post by markkun on 2006-06-13
Ok.. I fixed this by myself..

Problem was that VideoOverlay can't be on in both screens. As I set VideoOverlay "off" for my monitor, now everything works great.

Hopefully this solves someone else's problem too as I spent so many hours solving it. Very easy solution, but took a very long time to figure it out..

---

### Post by sparkplug on 2006-06-14
Thank you,I had the same problem,now fix it.:p

---

### Post by tstadler on 2006-06-14
Better than my work around :-) I opened one Xine with no display visable and then when I opened a 2nd xine up with the same media I would have a display. Lived with that for a month HEHE

---

### Post by manubing on 2006-11-24
I just registered just to say you thanks!

---

### Post by nir78 on 2006-11-25
Way to go man!!!
I was about to format my sys. as I had no idea what the problem was...
tnx a lot!

P.S.
I thing this should go straight to the "Tips and Tricks section" :KS

---

