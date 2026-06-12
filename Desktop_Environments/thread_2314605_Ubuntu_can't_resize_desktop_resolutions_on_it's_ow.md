---
title: "Ubuntu can't resize desktop resolutions on it's own?"
date: 2016-02-22
forum: Desktop Environments
---

### Post by gordan-vrbanec-vepar on 2016-02-22
Why is this still an issue?

I'm not trying to be and a-hole, i genuinely want to know. Windows did this since 95, and yet ubuntu doesn't change it automatically when plugging in a lower resolution monitor. It just goes to sleep and the system is inaccessible.
So why can't ubuntu and variants resize the desktop resolution accordingly? Is there a reason for this? Does it have to do with the kernel or desktop enviroment?

Last night i installed lubuntu on my 1920x1080 monitor, set it up for baisc internet and office work and gave it to my mom to bring to work. They of course don't have large monitors there so they can't boot up the system.
Or rather it boots up, it's just too high resolution for the monitor to display. And of course it has to be something urgent for them to do, and now the computer is out of my reach and i can't fix it.

Can i fix it at all? Even if i was there? Besides bringing it home and hooking it up to my resolution then manually setting a lower one? I probably should have done that in the first place, but i didn't know that i have to do that in 2016 on a modern OS...
Can i tell them what to do over the phone? Bear in mind, these are not computer savy people so i don't think any amount of console commands i tell them will be understood or done.

Lubuntu version 15.10 is installed...

I mean, why, just why? It doesn't seem to be that big of a problem to do in the kernel... Or does this entirely have to do with the desktop enviroment?

So, any help would be apreciated, if possible "urgent" (not that anything'll be fixed today as it seems) but whatever.
Also, if anyone can explain to me why linux can't adjust the resolution according to the monitor, that would be great. Is it distro related so i can avoid a particular distro (like lubuntu) in the future? I only installed lubuntu because it's an older computer and lubuntu worked great there. Better than XP and 7 which were previously installed there...

---

### Post by BazBear on 2016-02-22
I don't know, but maybe it could be the X11 display server's fault? She's getting long in the tooth, and that's why Wayland and Mir are being developed.

---

### Post by gordan-vrbanec-vepar on 2016-02-22
So basically, i need to get the computer back to my monitor and set the resolution manually then? :/

And you're right, it's probably the X11 display server... I totally forgot about that.
Idk, it's kinda weird for a modern OS to even have this problem. That's one of the things that it's keeping linux from being used more i think. I mean i love it, it's just that, i can understand why people don't want to deal with basic stuff like that in an overly complicated manner...

Because now, if i were to try to change the resolution on another monitor i'd probably need to get into grub and set some boot options or whatever. Now how do i explain that to people? Especially ones that just want a system that works.

Anyway, thanks for the insight. I'll read up on Wayland and Mir, i hope they do a better job than X11 (which is i gues we can safely say - outdated at this point)...

I'm still open to suggestions as to what to do in this particular situation...

---

### Post by buzzingrobot on 2016-02-22
There's a "Monitor Settings" entry in the menu (Preferences->Monitor Settings") that may help.  Lubuntu is sparse in terms of niceties. 

Much depends on the video card and the actual display. LCD displays have a single, fixed, optimal resolution.

---

### Post by gordan-vrbanec-vepar on 2016-02-22
Yeah, that would be great if they could see the desktop at all. The monitor went to sleep immediately after X was loaded apparently... There were some screen flickers here and there before but then it went to sleep. I know how to set the resolution when i'm on the desktop, it's just that, there is no desktop, all blank, and the monitor is sleeping.

Anyway, i just talked to them on the phone. I figured, it's probably loaded and stuck at login screen so i told them to write the password and hit enter. Nothing happened (or so they thought) so i told them to reset the computer.
And it kinda worked. It probably booted into desktop, then it recognised the resolution from there, and after a reset, everything was normal. Weird that it didn't automatically change it when it got to the desktop, or even before, at the login screen but it seems to be working now.

It still bugs me that this is even a thing on a modern os. I know this is lubuntu and it's very minimalistic and whatever, but it runs on a same kernel as Ubuntu and all it's variants. Had i done this in the newest Ubuntu, it would be the same. Because i had this problem before. I don't understand how a persistent live USB can work on any resolution, splash, login and all, but as soon as you install it it suddenly can't change resolutions anymore. Maybe i'm wrong, maybe it's just lubuntu's problem, maybe Ubuntu works just fine switching to a monitor's resolution, but still, this is not the first time i saw this issue, and i can't believe it's still and issue today... 

Oh well... It's "fixed" so i'll change the title to solved. I'd still welcome some discussion on what exactly is causing this behaviour, i'm interested in hearing what the problem is...

---

