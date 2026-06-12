---
title: "Compiz slow with sufficent hardware"
date: 2008-12-16
forum: Desktop Environments
---

### Post by Flippeh on 2008-12-16
Greetings!

I've been using Ubuntu 8.04 (x86) compiz without any slowdown before, with much weaker hardware than the one I own now, running Ubuntu 8.10 (AMD64). For comparism, let me list up the important parts I used before...

nVidia GeForce 8600 GT (Restricted driver installed)
AMD Sempron (1.6 GHz, single core)
Plug'n'Play CRT monitor, 19", 4:3 using 1024 x 786 resolution running on 85 Hz

... and now ...

ZoTac nVidia GeForce 9800 GTX (Restricted driver installed)
AMD Phenom 9850 (2.5 GHz, quad core)
Samsung SyncMaster 226BW monitor, 22", 19:10 using 1680 x 1050 resolution running on 60 Hz

As you can see, the hardware is a whole lot different (and in all cases better) than my last setup, but Compiz runs with only 40 +/- 5 frames per seconds, which lags quite a bit (very noticable).

I noted that before switching on the advanced desktop effects, the "Change resolution" window shows the current resolution setup correctly (resolution, frequency, color), while after activating it shows wrong information that seems to be changing sometimes (50/59 Hz, 640 x 480) which is not actually (luckily) applied. The nVidia X-Server displays it all correctly, tho.

I managed to solve the problem temporarily (unfixed after next restart), by wildly changing settings in the compiz settings manager "General Config", but I was not able to reproduce my frenzy-fixing.

The "fix" pushed my frame rate up too VERY high levels (I don't think I remebmer correctly, but I think I'm recalling 200 - 1000+, which I think is technically impossible as my display only has 60 Hz), and everything was about twice as fast as it used to be, really smooth and like it was meant to be displayed!

I hope I provided enough information, and if not, just tell me what else you'd need me to do to help you help me!

Edit: I just noticed the "Desktop Effects & Customization" category, which probably is more precise than this category. Sorry for that, I'm new and didn't see it the first time! Please feel free to move this thread!

Edit 2: Fixed it again. For anyone who has this problem: fire up your CompizConfig Manager, select "General Options", go to the "Display Settings" Tab and disable "Detect Refresh Rate" and boost up the Refresh Rate manually (I picked 200, just because I like being overkill.). Works, and it's even restart-proof!

---

