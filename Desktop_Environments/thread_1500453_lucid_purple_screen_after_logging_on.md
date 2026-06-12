---
title: "lucid: purple screen after logging on"
date: 2010-06-03
forum: Desktop Environments
---

### Post by systemgod on 2010-06-03
I upgraded from 9.10 to 10.04 2 weeks ago. After a day or so I suddenly couldn't logon anymore.  The pc boots, I get the userlist and can enter my username and password, then the userchooser dissappears but the background stays purple and nothing happens anymore.  I can still move the mouse and switch to text console but I don't get my desktop.  This happens for any user even a new user I created from the command line just to test this.  In the end I assumed I messed something up during the upgrade and reinstalled the pc from scratch using Ubuntu 10.04 32-bit.

I was happy for almost 2 weeks but now suddenly I get exactly the same problem. No matter which user account I try I just can't logon (graphically) anymore.  Rebooting the system doesn't help.
When I run top on a text console I don't see anything hogging the cpu. There is nothing obvious blocking anything. I can't find any clue in /var/log/* or ~/.xsession-errors. I can logon still in text mode as a regular user, my homedir is there, everything looks ok. (Note: I'm writing this on my pc at work so I don't have the logs with me)

1 thing I did notice is that a (few) boots before this started happening autofs suddenly didn't start anymore at boot time (my homedir is mounted from a NAS via NFS).  I had to manually start autofs as root to be able to get to my homedir. However this seems to be ok now, automount is running and my homedirs are available. I tried making a new user with a local account just to rule out network issues but even this user can't logon.  So the automount issue may be totally unrelated.

Anybody seen this before?  Any ideas what to try next?  I have no intention of reinstalling my pc every few weeks :(

Thanks in advance,

Nico

---

### Post by systemgod on 2010-06-04
Hmm,

turned out the problem was due to my Internet connection.  One of the cables of my cable modem got loose so my firewall couldn't get an Internet ip-address.   However I'm very surprised that a failing Internet connection would keep me from logging on completely. I would at least expect a decent timeout.

Nico

---

