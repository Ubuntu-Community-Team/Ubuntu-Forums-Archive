---
title: "now stuck in 640x480"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Flaystus on 2006-07-10
Fairly fresh install. I changed to the 686 kernal and loaded the nvidia driver and every thing was fine for a couple of days.

My last normal boot I just surfed the web a bit then rebooted and went to XP to play a game.

This morning the only video mode I can select is 640x480.

I checked the one config file that this forum said has the video modes in it and they are all listed.

What should I do?


Sadly this happened right after I told my friends how smooth everything had gone.  :(

---

### Post by jvictor on 2006-07-10
are u using a CRT ? If so , adding horizontal / vertical refresh rates to the Monitor section will help

---

### Post by Flaystus on 2006-07-10
yes its a CRT, but will adding the refresh rates make it suddenly come back as an option? Unless they were there before I can't see that making much sense.

---

### Post by jvictor on 2006-07-10
Well .. U can choose to try it or not .. it made sense to me to get things working .. I am not forcing u to add those lines :D

---

### Post by Jagot on 2006-07-10
You could try this:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Flaystus on 2006-07-10
I did try the reconfigue thing again. No help, that is if thats the same command they had me run at the end of the nvidia driver install.

Then I manually edited the xorg.conf (keep in mind I've ZERO clue what I'm doing) and notice the driver is still set the "nv".

So I guess my driver never really installed properly or something. I manually changed it to "nvidia" and on reboot couldn't even start X.

Thankfully my 2nd machine is up and taught me some quick Vi commands and I restarted.

Whats truely strange? I'm back to exactly where I started except now my video is normal again.

Has anyone ever seen something like this? The xorg.conf is exactly as it was when I started.


I guess what I want to know is. Why it happened if anyone knows so I can know what I did wrong or right and since apparently I'm STILL not using the correct driver how do I fix that also?

---

