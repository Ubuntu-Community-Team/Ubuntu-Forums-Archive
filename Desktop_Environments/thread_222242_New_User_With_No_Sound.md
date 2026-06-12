---
title: "New User With No Sound"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Protazoid on 2006-07-24
So after downloading and installing the Ubuntu 6.06 alternate installer (I heard it works better with wlan), and installed the various packages to stream movies, read pdf files, get flash and java working, etc. (I later found out about automatix and easy ubuntu, but at least I learned alot :D ).
I had wanted to share my new found ubuntu system with my mom, whom I made a non-sudoer user account for.  But when I loaded up her user, she had no sound.

Any ideas?

---

### Post by Rashid584 on 2006-07-25
Common problem it seems.

Try changing the permissions for /dev/snd to 666 and root:audio and same for all the files in the directory.

I did that, now kmixer "works" for the second user, but when they try to play any files with xmms for exampler, it gives an alsa error :S (but the red X has gone)

-Rashid

---

