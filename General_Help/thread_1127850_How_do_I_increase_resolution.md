---
title: "How do I increase resolution?"
date: 2009-04-16
forum: General Help
---

### Post by Midnight Marauder on 2009-04-16
I'm very new to Ubuntu. After installing Ubuntu, I went to System > Preferences > Display, and that's where I could change resolutions. I "accidentally" changed my resolution to a small display, and a textbox popped up that I don't remember what it said, but it had "virtual display" or something like that. Now, I'm in this smaller resolution, and when I come up to System > Pref. > Display, all my other resolutions, besides my current one and smaller, are not available!
How do I go back to my old resolution?

---

### Post by jrdonnaruma on 2009-04-16
```
sudo dpkg-reconfigure xserver-xorg 
```

That will reconfigure the Xserver and reset your resolutions to defaults. You may have to reinstall your video drivers after doing this.

---

### Post by Midnight Marauder on 2009-04-16
Ok, thanks a bunch!

---

### Post by jrdonnaruma on 2009-04-16
Your Very Welcome! :-)

---

