---
title: "How to remove submenu from Gnome MainMenu?"
date: 2012-05-30
forum: Desktop Environments
---

### Post by jacobain on 2012-05-30
Hello everyone,

I'd like to know how to remove one submenu from a Gnome Main Menu... I was using Windows for a long time, so I'm rather used to have something similar to "Start" menu.

I'm using Gnome Classic, but I removed the default Applications|Places menus and substituted them with one MainMenu icon on my bottom gnome panel. Perfect.

More modifications are necessary for me - I find the messaging menu on the top panel useless (well, I find it useless at all), so it's out too. But - to my surprise - it appears in the MainMenu in a form of submenu. On my home computer I'm using Ubuntu 10.04 and have managed to get rid of this submenu somehow, but it's a few years back and I don't recall how I did it.
On my notebook I have freshly installed Ubuntu 12.04 and I can't find how to get rid of this submenu here.
I thought it has something to do with indicator-messaging stuff, so I cleansed that. Missed.

Been searching through the Google for over an hour, but with no success. 

Can anybody advice me how to erase this bloody thing from my system?

Thanks in advance...

---

### Post by Frogs Hair on 2012-05-30
Try the command and logout-in or restart. I used this on gnome 2 prior to using a mail client. The indicator still has the same name.   ```
sudo apt-get remove indicator-messages
```

---

### Post by jacobain on 2012-05-31
> **Frogs Hair said:**
> Try the command and logout-in or restart. I used this on gnome 2 prior to using a mail client. The indicator still has the same name.   ```
sudo apt-get remove indicator-messages
```

I tried this before posting - didn't help. The submenu is still there... Tried to remove more indicator-related stuff I considered useless, but to no avail. :-?

---

### Post by jacobain on 2012-06-15
This is still an unsolved mystery... :-k

---

