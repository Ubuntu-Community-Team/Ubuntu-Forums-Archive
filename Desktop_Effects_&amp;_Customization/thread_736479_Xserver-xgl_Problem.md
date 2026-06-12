---
title: "Xserver-xgl Problem"
date: 2008-03-26
forum: Desktop Effects &amp; Customization
---

### Post by munceenuts on 2008-03-26
Whenever I try install xserver-xgl to get compiz and the visual effects and stuff to work I log out and then log back in get the gnome-settings-daemon error. I tried tons of ways to fix it and nothing works so I always end up removing xgl.

Is there anyway to fix this? I really want to use the visual effects.

And btw I'm using Hardy Heron.

---

### Post by unoodles on 2008-03-26
it is possible to use desktop effects without having the xserver-xgl package installed.
you can unblacklist your video card.
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

---

### Post by munceenuts on 2008-03-26
Hm.. I tried that and I got the white screen again, and then logged out and tried it again and the same thing happened.

---

### Post by gavinjb on 2008-03-26
What Card are you using I have never had any problems using XGL with ATI cards, my only thought is could it be Heron which is the problem, after all it is currently in beta.

---

### Post by munceenuts on 2008-03-26
ATI Radeon 9550,

I actually had this problem with 7.10 but it was unfixable. With Heron I can at least remove xgl and keep using ubuntu.

---

### Post by munceenuts on 2008-03-27
I just booted up and the screen was white with a big black box in the middle and then went completely white. And when I logged off it showed me the wallpaper right before it logged off.

It did this for even the Gnome Failsafe too.

I just don't think Ubuntu likes me.

---

### Post by Ub1476 on 2008-03-27
Have you installed a driver from System>Administration>Hardware Drivers?

---

### Post by munceenuts on 2008-03-27
Yes.

---

### Post by Ub1476 on 2008-03-27
You removed XGL too, right? The driver from Hardys repos doesn't need XGL. Or you can remove it and use Envy to fetch the driver, which surely doesn't need XGL.

---

### Post by munceenuts on 2008-03-27
Yeah I did. I can't seem to use compiz without it though. When I have it I get the gnome-settings-daemon error and it removes my fonts and themes and makes my computer a little slower but I can use the visual effects and AWN for some reason.

---

### Post by misterhead on 2008-03-28
I was able to follow this

[http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support)

and get it to work in 7.10 and 8.04. (8.04 was tricky)

had overheating problem in 8.04, though, had to go back to 7.10.

My laptop has a radeon mobility x600.

---

### Post by munceenuts on 2008-03-30
Every step worked except for the 12th one. 

When I try enabling Visual Effects it gives me the "Desktop effects could not be enabled" message.

Oh and I switched back to 7.10.

---

### Post by munceenuts on 2008-03-31
I finally got it to work!

EDIT:

Anyone know why this happens sometimes, though?

[IMG]http://img167.imageshack.us/img167/8630/screenshotcompizconfigsfl8.png[/IMG]

---

### Post by misterhead on 2008-04-01
My older ATI card will do some really trippy stuff, if I REALLY push it with effects and resolution. (more so  when "transparency" is involved) Sometimes to the point of locking up while dragging a window. And of coarse the whole "overheating" thing but that was only with Hardy. Fans just spin more in Gutsy than XP to compensate, but it hasn't overheated, just done weird display stuff like what you got, or lock up.

---

