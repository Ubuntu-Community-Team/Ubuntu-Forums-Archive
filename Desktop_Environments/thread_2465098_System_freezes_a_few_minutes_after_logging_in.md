---
title: "System freezes a few minutes after logging in"
date: 2021-07-22
forum: Desktop Environments
---

### Post by lister171254 on 2021-07-22
I'm using Ubuntu for my Music PC 
AMD Ryzen 5 with Radeon capabilities (see attached)
[ATTACH=CONFIG]288856[/ATTACH]
and after recently upgrading to Ubuntu 21.04 I have found the following issue. This issue did not occur straight after the upgrade, but I found this after the latest update.

The problem is that the entire system freezes a few minutes (usually after 8-12 minutes) after I log in. When I say it freezes, I mean that no keyboard input is accepted, I cannot get in via ssh, but the screen is still displayed.

The only way out of this is to reboot.

The system (and other) log(s) shows unprintable characters when this happens, so I have no idea why this happens. 

This happens in both Wayland and XOrg (see attached).[ATTACH=CONFIG]288858[/ATTACH][ATTACH=CONFIG]288859[/ATTACH]

The one time this doesn't happen is when I boot into recovery mode and resume the normal boot.  In this case the Graphics is identified as llvmpipe and the system is (and stays) stable. [ATTACH=CONFIG]288860[/ATTACH]

---

### Post by Geoff_Lane on 2021-07-22
Your attachment failed to show.

Freezes are often caused by memory issues.

Possible remedy is initiate or increase if already being used the SWAP file space.

[https://bitlaunch.io/blog/how-to-create-and-adjust-swap-space-in-ubuntu-20-04/](https://bitlaunch.io/blog/how-to-create-and-adjust-swap-space-in-ubuntu-20-04/)

Geoff

---

### Post by lister171254 on 2021-07-27
Sorry for the late reply, but it took a while to 
investigate this further.

To eliminate any hardware issues, I booted the Live CD and everything work as expected; no freeze after 5 hours

I then booted the system as normal, but logged in as a different user and this also worked as expected; no freeze after 5 hours

After looking at the (main) differences between the two accounts I found that the one that 'freezes' the system auto starts a nextcloud synchronization at login in. While the files to synchronize are in the hundreds of GB, there are few changes.

The other thing I found was that for some reason, autostart had three entries to start the nextcloud client. I haven't checked what happens in this circumstance with the Nextcloud crowd, but am guessing that when I logged in, it started 3 sync jobs, which completely saturated i/o, which looks pretty much like a freeze.


Thanks for the memory suggestions.

I have
```
llist@OurMusic1:~$ free
              total        used        free      shared  buff/cache   available
Mem:       14334492     1688156      460360       73224    12185976    12227964
Swap:      19531768        2060    19529708

```

Which according to the link you provided isn't quite enought for hibernation.

---

### Post by ActionParsnip on 2021-07-28
If you make a fresh user in command line (press CTRL + ALT + F1 on the login page. Login there and make the account). Is it OK if you login as that user?

---

### Post by oneplus321 on 2021-08-04
[B][COLOR=#000000]Freezes are often caused by virus or you can re-start your system.
[/COLOR][COLOR=#daa520]*dickens and his carol*[/COLOR][COLOR=#000000]
[/COLOR]*[https://www.writestories.site/](https://www.writestories.site/)*[/B]

---

### Post by ActionParsnip on 2021-08-04
Test RAM health using Memtest86 from GRUB (or similar)

---

