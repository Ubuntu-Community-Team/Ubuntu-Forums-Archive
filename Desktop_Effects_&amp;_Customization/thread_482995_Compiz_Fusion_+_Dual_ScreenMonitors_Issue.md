---
title: "Compiz Fusion + Dual Screen/Monitors Issue"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by wiijii on 2007-06-24
Good afternoon all. I've been using Ubuntu on my desktop for a few months, and only now have come across a problem that I haven't been able to find an answer for anywhere else! 

I've just upgraded from Beryl to Compiz Fusion, and everything is (technically) working fine, but I have a problem with my dual screen set up. and I'm not sure if it's due to Fusion just working differently, or because I'm missing something. 

I have the desktop cube and desktop rotate working, and can initiate it with a middle click (although, annoyingly Fusion processes the middle click as a cube rotate even if the cursor is over another app - rendering middle click otherwise useless), but the 'cube' does not appear as one large cuboid anymore. Instead I have two separate cubes, one on each screen - but they are different sides of the same cube, i.e. one cube is rotated 90 degrees further than the other, giving the appearance of two separate screens. Does that make any sense? If I increase my virtual desktops to more than 2 I start getting strange multi-sided desktops.

My normal flat desktop is fine, with TwinView set up to have one large desktop across both monitors. However, I want that double-screen to form one side of a cube, not for each screen to represent one side of the same cube. 

Right, that's long winded enough I think - if any clarification is needed, please let me know. If you need an example of what I mean, it's how Beryl looked with dual screens (there was an option in Beryl manager to have one large cube) - I'll try and find a screen somewhere. 

Thanks, 
Thom

---

### Post by hounddog32 on 2007-06-24
Exactly the same issue here - I loved having one huge cube with beryl and it will annoy me not to have that option.

---

### Post by rev_b on 2007-06-24
It's a known bug.

[http://forums.opencompositing.org/viewtopic.php?f=49&t=752&sid=d166a21f7bd047d75856e2a4eeb03e6b](http://forums.opencompositing.org/viewtopic.php?f=49&t=752&sid=d166a21f7bd047d75856e2a4eeb03e6b)

---

### Post by feest on 2007-06-25
okay a known bug, but is there any workaround for it?

---

### Post by emitchlpd on 2007-06-25
I've just figured out how to get one wide cube in Compiz (Nvidia Twinview).

I'm using the CompizConfig Settings Manager. In the Display settings, you want to disable "Detect Ouputs"  and enter ONE output manually. This is what I have:

1600x1200+0+0,1600X1200+1600+1

There are a couple of things going on here. For one, having a *single* output is what gives you one cube. Having the 1600+1 (instead of 1600+0) is what prevents the cube from becoming 8 sided.

Please replace my "1600X1200" with the appropriate resolutions for your displays. 

Hope this helps!

---

### Post by mavila on 2007-06-25
Ill look into that... sounds plausible, and I was having the same type issues. I actually switched back to Beryl as I found that the settings were frustrating to get going. I could get the sides down to four, but that was a "two sided" cube... and the way that it acted was very different from what Ive grown accustomed to in Beryl.

Question though, in Beryl we had the option to show TWO independent cubes each rotating their respective screens in sync when doing a rotation... we could also do one large cube (this is in the BerylSettingsManager / DesktopCube / MultiMonitor mode setting, either one BIG cube or multiple cubes. Anyone figure out how to do this in Compiz? (I get the impression that this is the known issue).

Thanks

---

### Post by Vil on 2007-06-25
> **mavila said:**
> Ill look into that... sounds plausible, and I was having the same type issues. I actually switched back to Beryl as I found that the settings were frustrating to get going. I could get the sides down to four, but that was a "two sided" cube... and the way that it acted was very different from what Ive grown accustomed to in Beryl.

Question though, in Beryl we had the option to show TWO independent cubes each rotating their respective screens in sync when doing a rotation... we could also do one large cube (this is in the BerylSettingsManager / DesktopCube / MultiMonitor mode setting, either one BIG cube or multiple cubes. Anyone figure out how to do this in Compiz? (I get the impression that this is the known issue).

Thanks

Currently, using the default way (with the 8 sided "cube") works that way for me, showing the appropriate face of the same "cube" on each monitor. I rather like it, honestly.

---

### Post by mavila on 2007-06-25
Vil - are you displaying TWO eight sided cubes with the entire wide desktop... or two FOUR sided ones (with the right / left displays split onto each cube)? Im trying to get TWO four sided, with the respective right / left displays to show. Beryl does it nicely - although it is time to get back to compiz

Thanks

Matt

---

### Post by damcito on 2007-06-26
im also want TWO cubes like beryl did

---

### Post by feest on 2007-06-27
> **emitchlpd said:**
> I've just figured out how to get one wide cube in Compiz (Nvidia Twinview).

I'm using the CompizConfig Settings Manager. In the Display settings, you want to disable "Detect Ouputs"  and enter ONE output manually. This is what I have:

1600x1200+0+0,1600X1200+1600+1

There are a couple of things going on here. For one, having a *single* output is what gives you one cube. Having the 1600+1 (instead of 1600+0) is what prevents the cube from becoming 8 sided.

Please replace my "1600X1200" with the appropriate resolutions for your displays. 

Hope this helps!

okay, it works, but maximising a windows now give one giaat window over two screens, can is solve this or is this a permanent side effect?
I also would like to know if it's possible to activate cube rotation but when you release it that the cube stays in place until you give it the instruction to activate the selected desktop (like ctr alt scrollclick in beryl) is this possible?

---

### Post by wiijii on 2007-06-28
Cheers for the info guys, seems like we might be getting somewhere. 

What about this damn middle-click registering everywhere on the screen, instead of just when you click on the desktop? Any ideas? At the moment middle-click copying/pasting is more important than a spinny cube =- but the spinny cube looks so much better! I need both! 

Cheers,
Thom

---

### Post by dannyboy79 on 2007-08-10
my problem is that the secondary screen is WAY FASTER than the primary one. I mean for drop down menus anyway. I can click on any dropdown menu, either in a program, within the upper panel, or anyone you can think of and count one one-thousand, two one-thousand and then it'll finally appear! BUT that's only on the primary display. 

So what I did ws reverse all the zero's and one's within my zorg.conf so that the secondary  screen woiuld appear on my main Flat Panel Monitor and that solves it BUT when I minimize a program it doesn't go to the lower panel, I mean it does show them being minimized to the lower right corner of the panel but they aren't showing them within the panel, I can use the ring switcher to pick a window but that's not the point.

I would just like to have my primary screen be back on the monitor in front of me and not have this hiorrible menu drop down slowness. ANy suggestions?

Here's my xorg.conf
[http://www.pastebin.org/370](http://www.pastebin.org/370)

and I use the Flat File Config for compiz. I don't know where it is if I could paste that I would. Oh, I use Feisty even if my profile still says Dapper.

---

### Post by Phesto on 2007-11-18
I'm using nvidia's twinview with two monitors and the previous workaround with compizconfig settings manager works fine all but the previous maximize problem. Just curious if anyone has found a solution to the maximizing across all the screens problem? I've been checking out this forum and the Compiz Community Forums and haven't found anything yet.
Thanks

---

### Post by bitfoo on 2007-11-28
I'm running Compiz-Fusion 0.6.3, and in the CCSM you have the option under Desktop Cube to have multiple cubes, one giant cube, or automatic for your multi output mode.

---

### Post by theyost on 2008-01-01
(In case not answered earlier)

In CompizConfig Settings Manager (need to apt-get.. not installed by default)

"Desktop" area -> Desktop Cube -> "General" Tab select "One big cube" in "Multi Output Mode"

:guitar:

---

### Post by t3hi3x on 2008-01-02
> **dannyboy79 said:**
> my problem is that the secondary screen is WAY FASTER than the primary one. I mean for drop down menus anyway. I can click on any dropdown menu, either in a program, within the upper panel, or anyone you can think of and count one one-thousand, two one-thousand and then it'll finally appear! BUT that's only on the primary display. 

So what I did ws reverse all the zero's and one's within my zorg.conf so that the secondary  screen woiuld appear on my main Flat Panel Monitor and that solves it BUT when I minimize a program it doesn't go to the lower panel, I mean it does show them being minimized to the lower right corner of the panel but they aren't showing them within the panel, I can use the ring switcher to pick a window but that's not the point.

I would just like to have my primary screen be back on the monitor in front of me and not have this hiorrible menu drop down slowness. ANy suggestions?

Here's my xorg.conf
[http://www.pastebin.org/370](http://www.pastebin.org/370)

and I use the Flat File Config for compiz. I don't know where it is if I could paste that I would. Oh, I use Feisty even if my profile still says Dapper.

Mine too. It does the exact thing you are talking about. I noticed that it isn't with just pop up windows, its when any new object is created.

Does anyone have a work around for this?

---

