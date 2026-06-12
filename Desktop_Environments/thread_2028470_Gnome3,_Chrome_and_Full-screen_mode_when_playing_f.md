---
title: "Gnome3, Chrome and Full-screen mode when playing flash video"
date: 2012-07-18
forum: Desktop Environments
---

### Post by SteveWilliams on 2012-07-18
Hi!

I recently went from Unity to Gnome3 and since then, I've been unable to view flash movies in full screen mode when using Google Chrome (stable). When I try to click the full-screen button, the video flashes and remains inside the browser. I've tried turning on the option to use the system title bar and borders (and off again), and my Chrome is definitely up-to-date (Version 20.0.1132.57)

I've tried using Firefox which works, and I'm absolutely stumped where to start troubleshooting this issue.

If I log in using Unity (rather than Gnome3), it works fine.

Thanks
Steve

---

### Post by Frogs Hair on 2012-07-18
I just tested Crackle and Youtube on the Gnome Shell and video quality at full screen was very good. I am using the same build. Do you have any blocking extensions ? If so disable them and restart the browser and try again.

---

### Post by SteveWilliams on 2012-07-18
Yeah, I disabled all of my Chrome extensions (only use 5 of them) and gave it a go, same result.

I also tried disabling that only Gnome3 shell extension (Alternative status menu extension) which also still didn't resolve the problem.

---

### Post by markbl on 2012-07-18
> **SteveWilliams said:**
> I recently went from Unity to Gnome3 and since then, I've been unable to view flash movies in full screen mode when using Google Chrome (stable).

It's not your move to gnome 3 (gnome shell) which has done this. it is because google chrome just recently (v20+) has switched to their own pepper player and it is currently a little immature/buggy. They have done this because Adobe have dropped development of flash player for linux so the pepper player will be the only one moving forward in the future. You can probably get around your present problems by disabling the pepper player (PPAPI) in chrome://plugins temporarily and fall back to the adobe version (NPAPI). That has fixed this same problem, and flash issues, for me. Long term things should get better and you can switch back. See [http://www.phoronix.com/scan.php?page=news_item&px=MTEyNzc](http://www.phoronix.com/scan.php?page=news_item&px=MTEyNzc).

---

### Post by SteveWilliams on 2012-07-19
> **markbl said:**
> It's not your move to gnome 3 (gnome shell) which has done this. it is because google chrome just recently (v20+) has switched to their own pepper player and it is currently a little immature/buggy. They have done this because Adobe have dropped development of flash player for linux so the pepper player will be the only one moving forward in the future. You can probably get around your present problems by disabling the pepper player (PPAPI) in chrome://plugins temporarily and fall back to the adobe version (NPAPI). That has fixed this same problem, and flash issues, for me. Long term things should get better and you can switch back. See [http://www.phoronix.com/scan.php?page=news_item&px=MTEyNzc](http://www.phoronix.com/scan.php?page=news_item&px=MTEyNzc).

Thanks for the heads up! I was completely unaware of this change to Chrome. I'll give this a try right now.

Thanks!

---

### Post by lovinglinux on 2012-09-12
> **markbl said:**
> ...They have done this because Adobe have dropped development of flash player for linux so the pepper player will be the only one moving forward in the future...

I would say Adobe dropped the development of Flash for Linux because of it's deal with Google. Is not like Google is doing us a favor picking up the development of an abandoned plugin. They announced the end of support for Flash Linux at the same time they announced Google would continue to develop it via Pepper API.

---

