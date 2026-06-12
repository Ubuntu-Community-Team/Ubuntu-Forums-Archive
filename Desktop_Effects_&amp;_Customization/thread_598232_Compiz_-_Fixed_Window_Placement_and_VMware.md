---
title: "Compiz - Fixed Window Placement and VMware"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by m0f on 2007-10-31
Hi all,

  I'm trying to get a vmware Windows XP session to start into Side #4 of the cube, but can't seem to get it to work.  Running vmware server 1.04 w/ Gutsy.

  Xprop reports the following :

name=vmware
title=Windows XP Professional - VMware Server Console
class=Vmware

Regex Matching is enabled and in Fixed Window Placement, under Windows with fixed viewport I have tried the above three separately with X viewport position set to 3.

After much mucking around I tried it with the Calculator (title=Calculator) and it started in the 4th desktop like  it should, so it appears the problem is specific to the vmware window.

vmware is being started with the following command (and appears to work perfectly, but always starts on the #1 desktop)

vmware -l -x -q -m "/var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional.vmx"

I've searched around but was unable to find anyone with the same issue.  Anyone have any idea what I'm doing wrong ?

Thanks

---

### Post by sites on 2008-02-28
I was just having the same problem & found this thread so i'm reviving it.

If anyone has insight on this issue, please illuminate us with the light of your wisdom.

---

