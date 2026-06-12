---
title: "Portal 2 Won't Start, Beta Enabled"
date: 2014-03-14
forum: Gaming &amp; Leisure
---

### Post by zecharixs on 2014-03-14
I'm running this on a Chromebook Pixel with Crouton and did force s3tc enable to true, and I enabled the beta on Portal 2 and Steam works fine.
But Portal 2 opens a window that says Launching Portal 2 then the window just closes and nothing happens. Please help. I've waited so long for Portal 2 to come to Linux.
Do I have to enable some codec, install a driver, or what?

---

### Post by oldrocker99 on 2014-03-14
Try running it from the command line:

```
cd "~/Steam/SteamApps/common/Portal 2" (or wherever it is on your system)
./portal2.sh
```

and post the results.

Portal 2 beta runs great on my desktop; I haven't tried it on my Acer C7 running Chrubuntu. Portal (the original) does run on Chrubuntu.

---

### Post by zecharixs on 2014-03-14
I tried that. No luck. It keeps telling me no such directory exists even though I actually copied the exact directory from my file manager. Opening the terminal from the file browser and running ./portal2.sh results in a similar error:
Failed to load the launcher (libuuid.so.1: cannot open shared object file: No such file or directory
This makes no sense as clearly the directory exists.

---

### Post by spectatorx on 2014-03-15
Remove portal2.sh file and after it in steam verify game cache files.

---

### Post by fourthaya-8 on 2014-06-18
I don't know about the original poster, but I was having that exact issue and spectatorx's advice fixed it for me! It took about the amount of time it takes to download the game, but it worked afterward and the game runs SO great! :) Thanks for the advice!

---

