---
title: "probs with multiple user accounts for desktop, switch user"
date: 2014-11-27
forum: Desktop Environments
---

### Post by bzipitidoo on 2014-11-27
I've found problems on Lubuntu 14.04 with trying to use two or more user accounts on the desktop.   This is an area that needs more polish.  The first user account is the only one in which everything works.  Accounts for desktop users created after installation can't access audio, and fight the 1st account for access to flash drives.

I thought the sound problem might be a permissions issue.  The 1st user can record and play sound.  The 2nd user can't.  The 2nd was not in any groups except its own and nopasswdlogin, so I added it to adm,cdrom,audio,dip, and plugdev.  I included audio even though the 1st user is not in audio.  Sound still does not work for the 2nd user.  Need more thoughts on what to do to get sound working for the 2nd user.

The problem with a flash drive is that if I have the 1st user logged in, and use "switch user" so the 1st user stays logged in while I use the desktop under the 2nd user.account, and then plug in a flash drive, the system tries to mount the flash drive twice, once for each user.  Both users get warning or error messages, and the 2nd user can't use it until I clear all the messages.

---

