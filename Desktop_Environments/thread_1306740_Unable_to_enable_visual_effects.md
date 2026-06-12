---
title: "Unable to enable visual effects"
date: 2009-10-30
forum: Desktop Environments
---

### Post by dopple on 2009-10-30
For some reason, I am able to enable visual effects on my admin account, however I cannot enable them on another regular user account. I have enabled admin rights for that user but it still doesn't work. It says something like "Desktop effects could not be enabled".

I have no restricted graphics drivers listed to enable.

---

### Post by maxpathan on 2009-11-14
Bump.
Got the exact same problem.

---

### Post by AFarris01 on 2009-11-20
Me as well.

I was trying to set up my laptop with some demo-accounts to show off the customization capabilities of linux, and I ran into issues installing a AWN, because compiz couldn't be enabled on the second user acct (a regular user, no admin). 

I've worked around it for now by enabling metacity compositing, but I'd love to be able to use the fancier effects offered by compiz.

I get this problem when logging into the other user via the fast-user-switcher, but not when logging out of my account, and logging into that account from gdm, or logging into the account from a cold boot.

I also ran compiz-check on both accounts... on the admin account it reported no issues, but on the user account it reported that software rasterizing was enabled, and gave me a 'fail'. Looking into it...

Anybody have any ideas?

---

### Post by dopple on 2009-11-26
Bump

---

### Post by AFarris01 on 2010-01-19
Just to (hopefully) close up this thread, I discovered that my problem, at least, was a bug in the older intel graphics drivers. An update to the newest drivers (via an update to Ubuntu 9.10) has solved this issue for me.

---

### Post by andrea000 on 2010-01-19
Some Intel graphics drivers are blacklisted in compiz
running compiz in the terminal or running compiz check
should point this out but even blacklisted drivers can
be made to work or unblacklisted.

---

