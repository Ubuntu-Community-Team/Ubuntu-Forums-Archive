---
title: "Desktop versus Alternate ISO issue... NFS mounts in fstab"
date: 2009-06-04
forum: General Help
---

### Post by MarkusAurelius on 2009-06-04
I'm not sure where I should be going with this or how to go about this...

Here it goes:

I have 4 x86 machines and 1 PowerBook G4 (PPC).I've been on Ubuntu since 7.10 and this is the first time I came across this.

When 9.04 came out, I downloaded the Desktop ISO and it installed just fine on the x86 machines.  For the PowerBook, I installed the Alternate ISO, as I had issues with 8.10 Desktop ISO and all was OK with the Alternate ISO 8.10. So, I installed the  PowerBook with the Alternate ISO.

However, on the PowerBook, for some strange reason, the NFS shares never mounted at boot time on the PowerBook...  I searched the forums, and although some of the stuff was quite old, there was nothing specific to 9.04 and regardless of what I tried, it did not solve the problem.  Knowing very well that the PowerPC version of Ubuntu beyond 7.10 is not officially supported, but is put together by a bunch of good folks, I'm very happy to see that 9.04 even did come out, so I can't complain.  I "solved" the issue with a quick script to do a simple "mount -a" once logged in and it solved the  problem...  at the time.

Now, on one of the x86 machines, I tried some other distribution, but at the end of the day, preferring Ubuntu, I re-installed Ubuntu 9.04, but since it is no big deal with USB boot, I installed it with the Alternate ISO.

Lo and behold, I had the same problem with the NFS mounts through fstab!!! Could it be the ISO as it was the same problem as experienced on the PPC???

So, I went ahead, and re-installed 9.04 on the x86 with the Desktop ISO and the NFS mounts worked just fine... 

Humm... So, I decided to re-install the PowerBook with the Desktop ISO... and to no surprises at  all, NFS mounts through fstab now work flawlessly on the PowerBook.

So, it would seem most likely that the Alternate ISO for 9.04 is NOT quite up to par...

My question, would this be considered a bug and if so, what are the procedures to get this fixed?

Truly Yours,

MarkusAurelius

---

