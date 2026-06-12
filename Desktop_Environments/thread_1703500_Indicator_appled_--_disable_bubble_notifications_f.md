---
title: "Indicator appled -- disable bubble notifications for email"
date: 2011-03-09
forum: Desktop Environments
---

### Post by mic47 on 2011-03-09
I want to disable bubble notifications for new emails (but I still want indicator applet to change color when email arrives). Those notifications distracts me a lot, so I want remove them.

Is it possible? I was only able to disable the evolution notification at all, but that is not exactly what I want.

---

### Post by Krytarik on 2011-03-09
Depends on the settings of your e-mail client/applet. "Notify-OSD" is just the messenger. ;-)
Which one are you using?

---

### Post by mic47 on 2011-03-09
I use evolution

---

### Post by Krytarik on 2011-03-09
> **mic47 said:**
> I use evolution
I somewhat expected that, thanks. Did you check its options?

---

### Post by mic47 on 2011-03-09
yeah, I wrote it in my first post:-)

There is plugin named Mail Notofication with one reasonamble option: generate a d-bus message. If it is off, then Indicator applet does not know about new email (and did not change color as new email arrives). But if it is on, then it also generate the bubble notification. 

However, there is a plugin named "Evolution indicator", I have it enabled, but it apparently did not do anything.

I was unable to find any further settings. Are there any?

---

### Post by Krytarik on 2011-03-09
Ok, thanks for the clarification. Since I don't even have Evolution installed anymore, and didn't ever use it, I don't know what plugins and options it offers.

But I will do a websearch and see if I can help you despite of that.

---

### Post by Krytarik on 2011-03-09
I found a bug report regarding "Evolution Indicator":
[https://bugs.launchpad.net/evolution-indicator/+bug/436755](https://bugs.launchpad.net/evolution-indicator/+bug/436755)

Does it apply to your system? To check it you have of course to disable the "Mail Notification" plugin.

---

