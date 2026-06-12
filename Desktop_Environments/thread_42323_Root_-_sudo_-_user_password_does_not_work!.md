---
title: "Root - sudo - user password does not work!"
date: 2005-06-17
forum: Desktop Environments
---

### Post by nataraj on 2005-06-17
I have installed Ubuntu 5.04 from the installer cd using expert intsall in the primary slave. I have a AMD (32) processor, and windows xp installed in the primary master disk. The GRUB loader also works fine as is my xp.  when i installed Ubuntu i entered a password for my root account  and i entered another user also. when i log into gnome through my user account, and when i try network settings i was asked for root password. when i enter it i get a message that the password is incorrect. if i enter the user password it says the user is not in the sudoers list.
i thought i had mistyped my root password and so i reinstalled Ubuntu but i had the same result.
The third time i reinstalled without entering a root password. even now i'm not able to  to any admin work - the message says "child terminated with 1 status".
Can you please guide me how to proceed - i'm not able to connect to the net as the adsl modem is not yet installed.

---

### Post by Xian on 2005-06-17
Read [THIS](http://www.ubuntuforums.org/showthread.php?t=33084) for more information.
You need to add your username to the sudoers file.

Just use the recovery boot mode to get to a command prompt.
Then issue the visudo command and make the appropriate edits.

---

### Post by nataraj on 2005-06-18
Thanks, this worked great. Thank you

---

