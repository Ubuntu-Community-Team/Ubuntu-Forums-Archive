---
title: "Fix for sound problem on Soldier of Fortune"
date: 2006-11-13
forum: Gaming &amp; Leisure
---

### Post by jamyskis on 2006-11-13
Just thought I'd post my little fix for anyone who's having problems with the music continuing to play when exiting Soldier of Fortune. You'll probably find that restarting ALSA will just restart the music, and stopping ALSA, and then starting it a few seconds later will do the same.

The trick is to restart Enlightenment's sound daemon with:

```

killall -9 esd
esd

```

Bear in mind that the terminal won't prompt for another command as if it were waiting for something to finish, but closing the terminal window won't kill the daemon.

---

