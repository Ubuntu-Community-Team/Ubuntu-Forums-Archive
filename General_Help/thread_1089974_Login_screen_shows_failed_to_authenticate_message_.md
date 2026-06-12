---
title: "Login screen shows failed to authenticate message immediately"
date: 2009-03-07
forum: General Help
---

### Post by endersnewhope on 2009-03-07
i apologize if this is in the wrong section.

I have a recently installed ubuntu 8.10 gnome desktop.  while trying to set it up so the password for the keyring would no longer be asked on every boot up through the guide here:

[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

I had to uncheck my login automatically selection, and I also unchecked the timed login box.

now when I boot up normally it immediately shows up with failed to authenticate message and clicking ok only brings the message back up.

I tried booting into the recovery mode, then going to the prompt and doing the login command and using my credentials to login.  then startx.  That boots the graphical interface, but failed to initiate hal error pops up as well as a switch user acounts failed to load message.

when using startx in root mode, I do not have anything show on my screen but can hear the login sound played.

thank you for any help, it would be very nice to not have to re-install but if that is the only option I would like to know that as well.

---

### Post by dcstar on 2009-03-07
> **endersnewhope said:**
> i apologize if this is in the wrong section.

I have a recently installed ubuntu 8.10 gnome desktop.  while trying to set it up so the password for the keyring would no longer be asked on every boot up through the guide here:

[http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/](http://ubuntu-tutorials.com/2007/07/12/automatically-unlocking-the-default-gnome-keyring-pam-keyring/)

I had to uncheck my login automatically selection, and I also unchecked the timed login box.

now when I boot up normally it immediately shows up with failed to authenticate message and clicking ok only brings the message back up.

I tried booting into the recovery mode, then going to the prompt and doing the login command and using my credentials to login.  then startx.  That boots the graphical interface, but failed to initiate hal error pops up as well as a switch user acounts failed to load message.

when using startx in root mode, I do not have anything show on my screen but can hear the login sound played.

thank you for any help, it would be very nice to not have to re-install but if that is the only option I would like to know that as well.

Read the rest of that blog, there are instructions for fixing this.

---

### Post by endersnewhope on 2009-03-07
Thanks, I was just learning how to change that file back from the recovery console.  I read down in the comments when i made the change, but not far enough it would seem.

---

