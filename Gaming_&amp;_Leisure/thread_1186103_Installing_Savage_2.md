---
title: "Installing Savage 2?"
date: 2009-06-13
forum: Gaming &amp; Leisure
---

### Post by Jimleko211 on 2009-06-13
I downloaded the 64-bit version, which downloads as a .bin file.  How do I install it?

---

### Post by Chemical Imbalance on 2009-06-13
Try right-clicking on it and go to Properties, Permissions, and check-mark "allow executing as a program".

Then just double-click on the file.

It should work, though I've never installed this game in particular.

---

### Post by Sealbhach on 2009-06-13
I Iinstalled the 64-bit version a few days ago.

After you've run the installer, you will need to run the "dedicated_server.sh" .

You'll find it in /usr/local/games.
```

cd /usr/local/games/Savage2
./dedicated_server.sh

```You probably need to run it as root, if so, do "sudo su" before launching the script.

[http://gwos.org/doku.php/guides:64bit:savage_2](http://gwos.org/doku.php/guides:64bit:savage_2)

This guide says you need to run the updater as well:

./savage2_update.bin

But I don't think I did that myself, I don't think it's vital to get the game running.

.

---

