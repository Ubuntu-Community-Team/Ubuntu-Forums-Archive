---
title: "ET downloads shut down."
date: 2007-06-11
forum: Gaming &amp; Leisure
---

### Post by LollYouSuckZor on 2007-06-11
Alright, Enemy territory.


Enemy territory uses a FTP download system, and anytime a server wants me to download something, ET crashes and closes.  I guess theres no way toi stop this?


The file types are: P3k? Something like that.

---

### Post by hikaricore on 2007-06-11
My guess is that you launched the game from the installer after installing the first time after installing with sudo?

Try this from terminal:

```
sudo chown username:username -R ~/.etwolf
```

Replacing **username** in both spots with your username.

Hope this helps,

--Aaron

---

### Post by asipi on 2007-06-13
Could be a solution, correct. Refer here if did not suceed.

One remark: ET using http methods for downloading missing files ;)

---

### Post by wishyjr on 2007-08-30
im having this problem also, but ive noticed that when i change any settings i get a message in the games console that it can't write to config file (or something -im away from my home pc at the mo to paste tha actual messge). Would changing the ownership (as per your command there) fix this as well?

---

