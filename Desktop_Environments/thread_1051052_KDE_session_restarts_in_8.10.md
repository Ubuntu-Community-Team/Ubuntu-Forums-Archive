---
title: "KDE session restarts in 8.10"
date: 2009-01-26
forum: Desktop Environments
---

### Post by TTFN on 2009-01-26
After upgrading from Kubuntu Hardy to Intrepid, my KDE session now wants to restart.  (not the computer, just the KDE session).  It will, at random, go to a black screen, then it will display some text too fast for me to read, then brings me back to the login screen.  I have found no common things going on when this happens.

At first I thought a bad upgrade, so I reinstalled my Hardy image and tried again.  Same thing.  Even a fresh install of Intrepid produced the same problem.  I checked video drivers, but no proprietary drivers were listed.  Thinking I may be on to something, I reinstalled my Hardy image and checked it, but no proprietary drivers were listed there either.

Next I tried installing Ubuntu 8.10.  This time, no crashes.  So it would seem that it is isolated to KDE.  However, I am more at home with KDE and would prefer to get that working, if possible.

I searched the forum, but did not come up with anyone having this same issue.  If this particular problem has been discussed, could you please provide the link.  Any help you could provide would be appreciated.

Thanks.

---

### Post by Monsieur Gonzalez on 2009-01-26
Hi!

Were you using kde4 before? I ask this because kde4 is changing very fast, and it happened to me that something plasma related was no longer working, and the only way I could enter my kde4 session was by deleting the plasma config files (in my machine, Kubuntu 8.10, located in .kde/share/config , and called plasma-appletsrc and plasmarc). !!IMPORTANT!! YOU HAVE TO DO IT FROM THE COMMAND LINE. DO NOT TRY IT IF YO DON'T FEEL COMFORTABLE WITH THE COMMAND LINE. BACK UP EVERYTHING JUST IN CASE!! 

Be aware you will loose any changes you've done to your "desktop" (or plasma-desktop), but you can easily modify it later.

---

### Post by TTFN on 2009-01-26
Thanks for your reply.

In Hardy I was using KDE 3.5 prior to my upgrade attempt to Intrepid.  Everything on the fresh Intrepid install (with all current updates) are at their default settings.

I will try your suggestion and see if it helps.  I will post the results.

Thanks, again.

---

### Post by TTFN on 2009-01-29
I have tried deleting the plasma config files as suggested, but did not make any difference.

I thought about trying to change the power management settings to see if there could be an issue with that, but I'm having trouble locating where to configure those settings.  I have found in the system services where I can enable/disable it, but no where to configure it beyond that.

Any suggestions?

Thanks.

---

