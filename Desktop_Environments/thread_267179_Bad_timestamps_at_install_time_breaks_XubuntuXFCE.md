---
title: "Bad timestamps at install time breaks Xubuntu/XFCE?"
date: 2006-09-28
forum: Desktop Environments
---

### Post by phibxr on 2006-09-28
I've had this problem occur for me twice in two days now. The procedure I've followed is this:

1. Boot the LiveCD
2. Click install
3. Choose the correct time zone, but forgetting to check if the clock is set right
4. Going through the install and rebooting.
5. Noticing the clock is off, synchronizing it.
6. Sudo gives 'timestamp to far in the future', when i do 'sudo aptitude install xubuntu-desktop', so I reboot and do a 'sudo -k', which was offered as a solution in an earlier thread.
7. Now I am able to 'sudo aptitude install xubuntu-desktop', and it installs cleanly.

Now, when it is installed, though, there are no icons in the settings pane. The icon files are there, and in all sizes, but XFCE seems to refuse using them if the timestamp is off.

Could this be corrected with some automatic tool to repair timestamps? For now, I've just done reinstalls and set the clock right at once, and then it works flawlessly.

---

### Post by aysiu on 2006-09-28
For setting the time in Xubuntu, you might want to check out [this thread](http://www.ubuntuforums.org/showthread.php?t=162376).

For the timestamp thing, have you tried rebooting?

---

