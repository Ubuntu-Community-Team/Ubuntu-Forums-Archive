---
title: "problem installation CD ubuntu 8.10"
date: 2009-01-31
forum: General Help
---

### Post by kooijman on 2009-01-31
I received the installation CD for ubuntu desktop version rel. 8.10 (Oct. 2008 ) in the mail last week (probably mailed to me in mid-January, 2009; it says "wave 52" on the address label). When I installed the system from this disc I had issues with gnome that have apparently plagued other people also. I was able to resolve these issues (whatever the cause may have been) by updating the distribution yesterday with get-apt (it took two hours of downloading 225 MB of patches). So my problem is solved. 

However, my point is that these issues were apparently flagged and solved and still the defective distribution was sent out on the CD!
I know other people had the same issues, because I found this solution in a thread about gnome in the General Support forum. As the problem with gnome completely prevented me from using the system this must be especially frustrating for new ubuntu users. 

As I am not completely new to linux I rooted around a bit, trying to solve the problem myself and I found an even more disturbing gaping hole in the security. I went through the recovery process and so serendipitously found the root-prompt. This allowed me to inspect and alter the installed system without having to provide a root-password. This seems a dangerous "backdoor" into the system as "root" does not seem to be protected. Again, new users will not be aware of this potentially dangerous issue.

These issues may have been flagged before. I searched for posts, but did not find them. In case I am just rehashing old issues, I apologize. But then I wonder why nobody did anything about the CD?

---

### Post by Iowan on 2009-01-31
I doubt the (mailed) CD's get updated as often as the downloaded version - and the downloaded version may not keep up with all updates, so after installing the system, a rather lengthy update (especially on my dialup) is usually the first order of business.
The recovery process is generally available only from console.  I haven't tried it on the newer versions to know if is still available other than from CD.

---

### Post by kooijman on 2009-02-01
My point is that the CD is the entry point for newbies and the problem I encountered made the system completely unresponsive (a blank screen and not even ctrl-alt-del worked to abort the session). It would not occur to someone from the Windows-XP world that something simple like updating/upgrading the system would give the solution, nor would most new users know how to do this, as the CD comes without a manual. (It involved using a failsafe terminal and using the apt-get program which seems to be peculiar to the ubuntu distribution, neither of which would be obvious to a novice). I grant you that it is good practice to upgrade regularly, but that is beside the point in this case. 

I hope my complaint makes its way to the people who distribute the CDs, because I am sure in this form the CD turns off people needlessly from a system that is a decided improvement on the Red-Hat distribution I use on my old computer.

---

### Post by theozzlives on 2009-02-01
Funny, when I first started to use Ubuntu, from Windows XP, I just took to it naturally. You can "just upgrade" with the Alternate CD. Haven't seen any problems, except I don't have Kooka anymore.

---

### Post by kooijman on 2009-02-03
Experiences may vary. There is a CD being sent out that installs a system that is unresponsive after one logs in due to a problem with Gnome (as configured using this CD). I received that CD and so apparently did other people. Or I would not have found the posts, discussing the exact same problem, that helped me solve it. I have no doubt that in the past the installation CD did not have this flaw. Otherwise Ubuntu would certainly not be where it is now. But as I received this CD very recently I think the problem will grow in seriousness if it is not addressed. It requires luck and tenacity to find the relevant forum and most recipients, new to Ubuntu, will simply not know where to look. If the organisation thinks it is too expensive to do something about the CD, maybe an insert with instructions could be put in the envelope?

---

