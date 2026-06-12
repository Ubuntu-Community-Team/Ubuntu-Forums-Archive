---
title: "Synaptic Package Manager Start up error :("
date: 2006-07-31
forum: Desktop Environments
---

### Post by chamlyn on 2006-07-31
I get this message (after a crash/forced reboot)

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

So I go to Terminal and I run the dpkg thing and it says I need to be a superuser to run it.  How do I tell it I'm the super user?

Thanks
CB Hamlyn

---

### Post by chamlyn on 2006-07-31
Sorry, I didn't think to look up Superuser, I only searched on the error message #-o 

So I type in "su" and it asks for a password but won't accept the only password I set for the only user I have on here.  And it won't accept a blank password either.  I triple checked my CAPS lock and still nothing.  Is Superuser different than Administrator?

Sorry, this should probably go into the beginner section?

Any help would be appreciated

---

### Post by chamlyn on 2006-07-31
Figured it out.  Sorry to drag everyone through my mental exercises, it's late, I'm tired, I probably should've just done all this tomorrow! anyway...

sudo dpkg --configure -a

is how you fix it.  Followed by entering the user password.

Thanks for reading =P~

---

