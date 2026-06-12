---
title: "Can't get full resolution on old LCD"
date: 2008-03-23
forum: Desktop Effects &amp; Customization
---

### Post by neil_black on 2008-03-23
Hi,

Well I got an old PC and thought it would be the perfect opportunity to install Ubuntu 7.10 and hook it up to my network. And I have to say, my first impressions are... brilliant!

The problem is, I have an old unbranded LCD display that supports 1024*768. But I can only get 832*624 working. If I select 1024*768, the LCD looses signal and says "Not Supported".

Its an AGP GeForce 4 MX 440 graphics card. I've enabled the restricted "NVIDIA accelerated graphics driver" but still no luck. I've also tried enabling "Sync To VBlank", again no luck.

When I used this LCD as a 2nd monitor on my Windows PC (with an ATI 1950 Pro card) I see the exact same problem. To get 1024*768 working on the old LCD in Windows, I have to enable "Composite Sync", then 1024*768 works fine.

Is there a comparable setting for Linux?

Thanks in advance.
Neil.

---

### Post by Ub1476 on 2008-03-23
I'm not a ndvidia owner myself, but have you checked the nvidia control panel?

---

### Post by neil_black on 2008-03-23
Ahh thank you! didn't realise there *was *nvidia settings. But a quick Google and I ran it from terminal with nivida-settings command.

Still not managed to get 1024*768 working. BUT, managed to get 1152*768 working! Very confusing, but not complaining.

I'd still like to understand why 1024*768 doesn't work though.

---

### Post by Ub1476 on 2008-03-23
It can probably be set by editing xorg but I guess a higher resolution is better?

```
gksudo gedit /etc/X11/xorg.conf
```

You should be able to find the section for the monitor and add 1024x768 as an resolution.

I suppose you already have looked in System>Administration>Screens and graphics..?

---

### Post by neil_black on 2008-03-23
Yeah, I can select 1024*768 ok, its just that the LCD doesn't like it, looses signal and reports "not supported" .

I was able to fix this in Windows by selecting "composite sync". Its strange that its just that resolution that it doesn't like.

I'll dig around some more.

---

