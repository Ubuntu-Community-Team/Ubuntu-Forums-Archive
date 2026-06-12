---
title: "Something very strange has happened... hosts fille &amp; network conf modified randomly??"
date: 2006-08-25
forum: Desktop Environments
---

### Post by BrianK on 2006-08-25
This is a slightly desparate situation...  My Ubuntu 6.06 server (actually, it's running Desktop) recently powered down because the UPS it's on ran out of juice.  I believe it powered down politely, but can't be sure.

Since it's come back up, some things are different.  

* resolv.conf was empty.  I had to run the network-admin tool to update it.
* my hosts file (/etc/hosts) has changed.  Some of my computers are no longer in it - not all of them, but some.  For example, I have computers named element21 - element42 (in addition to others).  About half of them are missing from the hosts file.  They were positively there before the powerdown... as a matter of fact, they were there until about 15 minutes ago.

About 15 minutes ago (this machine came back up from the power-down about 2 hours ago), something happened.  Now the license server that runs on this machine in question is no longer serving licenses & can't be restarted.  My render manager (which runs from this machine) no longer recognizes the missing machines between element21 & 42 - just shows an IP address (as I would expect if they were removed from the hsots file).

  My whole business is based on software that is licensed by this machine & I have to deliver a BIG project on Monday & another on Tuesday with no company tech support between now and Monday.  The license server issue appears to be related to this networking oddity... licenses work when run locally, but not when checked out remotely

What the heck is happening?

I don't have ssh pointing to the machine in question. I've checked the auth logs on my ssh machine & the server to see that no one besides myself has logged into the server.  I don't know what happened, but something happned about 15 minutes ago that, if not solved, could cost me thousands of dollars.  Panicing a bit... but still holding it together.

Someone please help.  :)

---

