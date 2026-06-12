---
title: "Hi, and shutdown issue"
date: 2006-01-09
forum: Desktop Environments
---

### Post by bikeman on 2006-01-09
Just wanted to say hi all, and thanks for this great resource.  I just installed 5.10 (relative newbie, but some experience with SUSE, Xandros and Fedora Core), and have spent the past week customizing the look and feel, using many great tips from these pages.  It now looks and runs beautifully, with one exception.

When I shutdown (I don't leave my home PC on all the time), it hangs at the following step:  Shutting down LVM Volume Manager.  I then have to turn off the computer manually or it will stay there forever.  It will then start again normally, but I would hate to damage the filesystem or anything by not shutting down properly.  I don't remember this happening in the beginning, so it may have happened after a tweak.  I have done things like add a splash screen and followed the thread about "making Ubuntu blue" if that helps.  I did try a forum search and a Google search, but found no answers, at least with the search terms I used.

If anybody can point me in the right direction to fix this I would greatly appreciate it!  Thanks.
Dan

---

### Post by bikeman on 2006-01-09
Well, I did find an answer, right here in the forums! :oops: 

I searched for general shutdown problems, not just the point where my desktop was freezing, and found this helpful thread:  [http://ubuntuforums.org/showthread.php?t=75314]("http://ubuntuforums.org/showthread.php?t=75314")

Turns out that one of the suggested fixes (add noapic  nolapic to the GRUB menu) worked like a charm.  So now Ubuntu and my PC are playing nice again.

My PC won't support MS Vista, and now my wallet won't either!  Thanks.
Dan

---

