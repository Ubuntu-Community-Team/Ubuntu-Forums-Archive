---
title: "dynamic multi display management"
date: 2010-01-03
forum: Desktop Environments
---

### Post by ultiphoenix on 2010-01-03
hey guys, i want to start a discussion, or actually i would like to know if there is anything like this out there or in development and if not i think there should be. i feel that one of the areas that ubuntu still lacks majorly is when it comes to handling multi display.

most people these days are using notebooks and are moving around a lot, and if your like me working as a software dev you need to be able to work from home running a different external display next to your internal, then when you get to work you need to maybe run two external displays or maybe a totally different display next to your internal, sometimes you'll need to connect to a projector in a meeting and do a demo.

At the moment, there is no easy way to do this unless you have a half an hour everytime to configure your displays manually, which goes without saying that its not quite what anybody is looking for.

i'm looking for something that works similar to OSX's display manager. where you plug in a screen and poof, its there. and then mayb you can configure what your system should do when that specific monitor is plugged in and it will remember that configuration. so for instance you have a internal 15" with a res of 1440x960 then you want to plug in your 1080p 24", so boom it picks it up but its not configured yet. so it jus mirrors by default, then you decide ok, when this screen is pluggd in, i want it to extend my desktop onto it, and make it the primary monitor. ok cool so its set, so now when you plug it out, your system detects that your display setup has changed, then does a recheck of your active displays, and sets up the appropriate configuration, in this case only the internal is available so it will just go back to the internal, setting it back as the primary and moving all the windows that was on the external back to the internal.

i think this would be a invaluable feature for a mobile professional.

Does anyone have any ideas or know of any active projects on the subject?

---

### Post by ultiphoenix on 2010-01-03
i've been researching on this and it seems that there was some work done about a year ago, [https://wiki.ubuntu.com/DisplayConfigGTK](https://wiki.ubuntu.com/DisplayConfigGTK), but was dropped it seems. xrandr 1.2 added all the support we need for hot plugging displays, i dont get why they dropped it.

i'f someone can shed some light on this, it would be awesome

---

### Post by krige on 2010-10-18
> **ultiphoenix said:**
> i'm looking for something that works similar to OSX's display manager. where you plug in a screen and poof, its there. and then mayb you can configure what your system should do when that specific monitor is plugged in and it will remember that configuration.

I am interested in the same thing. That's the default behavior in Windows too. As a matter of fact it is the behavior anyone would normally expect. I am surprised I am forced to configure it again and again every time I plug in an external monitor. There is not even much of a discussion about the topic: it seems very few people are using Ubuntu on a laptop with an external monitor.

---

### Post by ardunarda on 2010-10-18
i use external display but nvidia x server settings is enough for me. When i plugged new display just i opened it and configure my new display as twinview

---

### Post by krige on 2010-10-18
> **ardunarda said:**
> i use external display but nvidia x server settings is enough for me. When i plugged new display just i opened it and configure my new display as twinview

Do you mean you don't need to configure it every time you plug in a new display?

I have an ATI graphic card and I am forced to configure it every time I plug an external display using ATI Catalyst Control Center.

---

### Post by ardunarda on 2010-10-18
yes you have to configure it every time plug it but it is ten second configuration, i think it is acceptable

---

### Post by krige on 2010-10-18
> **ardunarda said:**
> yes you have to configure it every time plug it but it is ten second configuration, i think it is acceptable

It takes more than 10 seconds with the ATI Catalyst Control Center and the operation may be quite uncomfortable depending on the position you put your laptop in (e.g. behind the external monitor, on a shelf below the desk).

Anyway the point here is that computers are supposed to help humans with repetitive tasks: having to configure every time you plug in an external display is simply unacceptable. What's more, if Windows and OSX gets configured automatically, I don't see any reason why Ubuntu shouldn't too.

---

### Post by devilliers123 on 2010-11-04
Seems few people know of    grandr

Check it out

---

