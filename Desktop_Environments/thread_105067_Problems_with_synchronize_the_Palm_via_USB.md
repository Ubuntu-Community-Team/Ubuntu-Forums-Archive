---
title: "Problems with synchronize the Palm via USB"
date: 2005-12-17
forum: Desktop Environments
---

### Post by pito on 2005-12-17
Hello...
I do have problems with synchrinizing my Palm with the 5.10 ubuntu. It worked OK on Fedora Core3 for over a year. Now Ihave switched to Ubuntu. Very nice Distro but the palm-pilot stopped to work.

I see that /dev/ttyUSB0 and /dev/ttyUSB1 are created when the the Palm Pilot is connected.
I use UDEV utilities and I see that it create correct /dev/pilot automatically every time the pilot is connected.

In the /var/log/messages I see all the stuff correctly initialized.
The problem is that when I Sync the Palm nothing happends.
dplsh -p /dev/ttyUSB0       is not working
dplsh -p /dev/ttyUSB1       is not working
dplsh -p /dev/pilot              neither works

/sbin/lsmod shows usbserial as stated on some TODOs lists.


I did try the GNOME UI for pilot but with the same negative result.

Any clue ? MAybe some one of you has the same problems ?
Is there any possibility to debug/log things on line and see what is happening ?

Best Regards
PiTo

---

