---
title: "Primary Domain Controller Issues"
date: 2006-09-13
forum: Desktop Environments
---

### Post by 64mgb on 2006-09-13
I did a fair amount of searching and have not been able to find an answer to this.  I've set up one of my Ubuntu boxes as a primary domain controller and it seems to be working ok.  I can log in to it from another Ubuntu box using "net rpc join" in a terminal session after I've logged in to the client machine.

Here's the issue.  I think one of the primary benefits (for me at least) is the ability to log in to any pc on my network (that is set up on the PDC) without the need to have a user account on the machine I'm logging in to.  The authentication should be done by the PDC and allow the user to log in if the PDC knows about them.  First of all, is this true (no sense going any farther if that is not correct)?  Secondly, how is this done with Ubuntu boxes?  I think I know how to do it on my Windows 2000 box (although I have not done it yet), but haven't seen a way to do it with Ubuntu.

Any ideas?

Thanks,
Rich

---

### Post by hellmet on 2006-10-03
yea any ideas??

---

