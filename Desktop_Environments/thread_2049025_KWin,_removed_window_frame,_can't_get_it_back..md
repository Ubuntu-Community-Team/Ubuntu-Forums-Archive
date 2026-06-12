---
title: "KWin, removed window frame, can't get it back."
date: 2012-08-27
forum: Desktop Environments
---

### Post by HrKristian on 2012-08-27
Hi!
I was peeved by having a window border around my Spotify client, it looked weird as the design is made to be frameless.
Thus, I did what any sensible person would, I fixed my own problem.

Now Spotify seems completely removed from KWin, it doesn't show up in alt-tabs etc.

I could really use a command to reset the KWin settings for a specific (removing and purging didn't help), or a helpful nudge in the direction of the related config file.

I tried googling, but, it seems no-one's had the issue of just one program missing the frames, and not being able to get them back.

---

### Post by rotave on 2012-08-28
Not sure how to fix your problem, but the config files for kwin are located in:

/home/<user>/.kde/share/config/kwinrulesrc
and 
/home/<user>/.kde/share/config/kwinrc

you could either delete the files or try to edit them manually.

---

### Post by HrKristian on 2012-08-28
Thank you, kwinrulesrc contained specific application settings, deleted the two entries about Spotify and rebooted and it's back to original settings :)

---

