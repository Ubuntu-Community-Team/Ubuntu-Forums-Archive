---
title: "ANOTHER login loop Ubuntu 13.10. Checked permissions and usual suspects..."
date: 2014-03-12
forum: Desktop Environments
---

### Post by thezman007 on 2014-03-12
Hello everyone and thanks in advance for your help.

I have been running Ubuntu 13.10 for a few weeks now (maybe longer) with no real problems to speak of. I (foolishly) decided I should try to use AMD's drivers in order to get better streaming video. I downloaded their latest driver 13.12 and installed it via the terminal. Immediately after installing my drivers it tells me there were errors and that I need to reboot. I reboot and get a blank screen. After some work I manage to purge the fglrx driver issues and revert to the original file/driver. Now, I have a login loop. My computer will boot up fine, I enter the password to decrypt my disk, and then right when the login screen should come up the monitor enters power saving mode... However, if I Ctrl-Alt-F1 to a tty, then BACK to Ctrl-Alt-F7 I can see the screen for some reason. So here is what I've tried:

-Logging in as Guest (loops)
-Uninstalling/Reinstalling AMD drivers (loops or no video)
-Using an earlier kernel via GRUB (loops)
-Using recovery mode (no video)
-Checked permissions on .Xauthority (loops)
-Checked permissions on /tmp (loops)
-Adding a user (loops)
-Installing GDM (loops)

I have searched quite a bit and nothing seems to work for my particular situation... The only errors I'm seeing are DKMS related while installing and uninstalling AMD's drivers.

.xsession-errors says 

```
XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
       after 17 requests (17 known processed) with 0 events remaining.
```

Can someone point me in the right direction?

---

### Post by thezman007 on 2014-03-13
This is my business's machine. Bump :)

---

