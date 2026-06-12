---
title: "[SOLVED] No sound in Nexuiz after upgrading to Ubuntu 8.10"
date: 2008-11-11
forum: Gaming &amp; Leisure
---

### Post by Linux user 66 on 2008-11-11
In Ubuntu 8.04 64-bit, the game Nexuiz worked without any problems. After I made a fresh installation of Ubuntu 8.10 64-bit and installed Nexuiz, I have no sound in the game.

Any ideas as to what I can do to fix this?

---

### Post by Sprocket_dk on 2008-11-11
Same as me. I found that pulseaudio was the cause. Check out the link dude:

[http://linux.blogs2k.com/2008/11/01/fix-for-no-sound-issue-in-ubuntu-810-intrepid-ibex/]("http://linux.blogs2k.com/2008/11/01/fix-for-no-sound-issue-in-ubuntu-810-intrepid-ibex/")

---

### Post by glotz on 2008-11-11
Start it from the command line, see if it spouts out any hints. I personally killed pulseaudio a long time ago as it offers me nothing of use.

---

### Post by Linux user 66 on 2008-11-11
> **Sprocket_dk said:**
> Same as me. I found that pulseaudio was the cause. Check out the link dude:

[http://linux.blogs2k.com/2008/11/01/fix-for-no-sound-issue-in-ubuntu-810-intrepid-ibex/]("http://linux.blogs2k.com/2008/11/01/fix-for-no-sound-issue-in-ubuntu-810-intrepid-ibex/")

That fixed it! Thanks!

---

### Post by Sprocket_dk on 2008-11-12
To make the change permanent: [http://ubuntuforums.org/showthread.php?t=973637]("http://ubuntuforums.org/showthread.php?t=973637")

---

