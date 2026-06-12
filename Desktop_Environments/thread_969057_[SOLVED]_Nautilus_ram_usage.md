---
title: "[SOLVED] Nautilus ram usage"
date: 2008-11-03
forum: Desktop Environments
---

### Post by fabertawe on 2008-11-03
Hi folks,

Could someone please launch System Monitor on logging into Gnome and tell me if they have 'nautilus --no-desktop --browser' using 128MiB? Shouldn't Nautilus be running without '--no-desktop --browser' for the desktop? Surely that ram usage is excessive (it also steadily rises).

I've done a clean Intrepid install of '/' whilst retaining my Hardy '/home' partition.

Thanks!

---

### Post by tuxxy on 2008-11-03
Nope just have nautlius running at 36MB

---

### Post by fabertawe on 2008-11-03
Thanks for checking tuxxy. It's now up to 319.4!! Sounds like I need to clean out the Gnome settings somewhere. So much for a clean install! :rolleyes:

---

### Post by solitaire on 2008-11-03
Mine is sitting at 53.7 Mb. It usually jumps up to +150Mb after 6 hours or more, if i open up folders with lots of thumbnails. Think it might cache Thumbnail images in memory.

---

### Post by tuxxy on 2008-11-03
Is it the same every boot or can you kill the process

---

### Post by solitaire on 2008-11-03
It's the same every time.  I've only got 512Mb of ram but it does not seem to slow my system down much.

For me Firefox sits at 198Mb and Thunderbird is around 158Mb

---

### Post by fabertawe on 2008-11-03
I discovered the memory hog... 'twas 'nautilus-clamscan'. Removing that got memory usage down to 38MB. I rarely use it anyway and had already written my own nautilus-action previously.

Sorting out Nautilus itself was a little more convoluted. I quit it from a terminal with 'nautilus -q', instructed session manager to remember running applications (or lack of in this case) and logged out. Having determined that Nautilus was no longer running on login I then added a new entry to 'Sessions' consisting simply of 'nautilus'. I now get memory usage of 28.2MB on startup. I notice that memory usage builds up when running browser windows (obviously!) but isn't released when they're closed. I'm guessing this is the same for everyone though.

---

