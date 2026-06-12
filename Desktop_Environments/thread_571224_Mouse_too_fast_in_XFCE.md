---
title: "Mouse too fast in XFCE"
date: 2007-10-09
forum: Desktop Environments
---

### Post by Ubunthree on 2007-10-09
Hi all,

My installation is the regular Ubuntu (Feisty) with GNOME. A while back I installed the XFCE desktop to try out a lighter weight environment. I found that it fit my needs better than GNOME, so I now use it as my default.

A few days ago I had to replace my mouse, and got an inexpensive laser type, just a standard three-button with scroll wheel. The mouse is very precise and smooth, much better than my old one except for one minor thing. My issue is that this mouse runs faster than the old one. With GNOME's mouse configuration, the slowest cursor speed setting will slow it down to a comfortable speed, but in XFCE the slowest setting is still a bit too fast for what I need.

So, the question: Is there a line in a config file somewhere that I can manually edit to cut the cursor speed down below what the GUI control will reach? I am using my old mouse in the meantime.

Thanks for any help you all can give me.

---

### Post by kerry_s on 2007-10-09
in terminal> xset m 1/1
if that works put it in the startup
you can use 1->4
man xset 
for more info

---

### Post by Ubunthree on 2007-10-09
Thanks for the quick reply!

The terminal method seems to work, but unfortunately the 1/1 setting appears to be no slower than the GUI setting will get me. I tried settings like 0.1/0.1 just to see if it would work, but of course it didn't. I can have both the old mouse and the new one connected at the same time, so I have an easy choice at least.

A couple of things I'm curious about:

Using xset in the terminal changes the mouse behavior, but doesn't change the positions of the sliders when I call up the GUI mouse settings the next time. How do the two interact? I thought of setting the GUI sliders at a higher speed, doing xset, and then pulling the sliders down again to see whether that would cut the speed further, but no.

What do you mean by "put it in the startup?"

This and the lack of a good driver for my Canon printer are the ONLY issues that I've run into with the whole Ubuntu system. I guess the reason I'm still a bit of a noob after running this for about a year is because I've had so few problems to deal with.

Thanks again.

---

### Post by kerry_s on 2007-10-09
xset is like the system defaults. type> xset -q <and you can see the settings.

i messed with it a little more, try> xset m 1/6 1
i guess i was wrong about the 1->4.

```

    To set mouse acceleration and threshold:
         m [acc_mult[/acc_div] [thr]]    m default

```

autostart is in your settings menu.

---

### Post by Ubunthree on 2007-10-09
Excellent. The 1/6 1 setting actually seems to be about right for the new mouse. It's usable now. And I added the command to my autostart. Thanks!

Now some curiosity-fueled observations:

The **xset m** option slows it down, but does so in an odd way. Reading the **man xset** page tells me:
[INDENT]The parameters for
the mouse are ‘acceleration’ and ‘threshold’. The acceleration
can be specified as an integer, or as a simple fraction. The
mouse, or whatever pointer the machine is connected to, will go
‘acceleration’ times as fast when it travels more than ‘thresh&#8208;
old’ pixels in a short time.[/INDENT]
So at this setting, the speed is reduced to 1/6 of default whenever the mouse is moving, basically. If I do **xset m 1/6 4** instead, the cursor speed is reduced to 1/6 of default whenever the mouse moves *faster* than 4 pixels- per- whatever- time- interval- it- uses. This means that the screen cursor's travel, relative to the mouse's motion, will speed up when the mouse slows down, which is the opposite of what I would expect. I can reverse this by using an integer rather than a fraction for the acceleration, but then the minimum speed will not be reduced. So if I use **xset m 5 20** for instance, the cursor's speed will jump from 1 up to 5 whenever the mouse's speed exceeds 20. What I would like ideally is for the cursor speed to start at 1/6 and jump up to 1. There doesn't seem to be a separate parameter for the minimum speed, though, at least from what I understand.

Keep in mind that my new mouse is a freak, and these numbers may be totally out of line for other mice. A setting like **xset m 3 15** is fine for my old mouse (MS Basic Optical), which is ridiculously sluggish at the **1/6 1** setting.

Thanks again!

---

### Post by kerry_s on 2007-10-10
yeah, i don't think linux takes into account the newer mice with 1000+dpi which picks up even the littlest movement. mines a microsoft model:1016 with i think 800dpi so it's just right at the stock settings.

---

