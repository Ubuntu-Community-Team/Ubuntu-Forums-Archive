---
title: "Ubuntu Server 8.04.2 Release Timeline"
date: 2009-01-07
forum: General Help
---

### Post by ralish on 2009-01-07
Hello,

I was hoping someone here could give me some information regarding the expected release timeline of Ubuntu Server 8.04.2. I've been scouring the web for good information regarding its release schedule but have come up with conflicting information. The launchpad ([https://launchpad.net/ubuntu/+milestone/ubuntu-8.04.2](https://launchpad.net/ubuntu/+milestone/ubuntu-8.04.2)) lists the release as 2009-01-01 (in the past), yet the wiki ([https://wiki.ubuntu.com/HardyReleaseSchedule](https://wiki.ubuntu.com/HardyReleaseSchedule)) lists it as 2009-01-22. Could anyone please clarify, even with just a general timeframe, what myself and others should be expecting?

I ask as I'm eager to deploy a Ubuntu Server and shall be basing it off Ubuntu Server 8.04 x64 being an LTS release. I've been led to believe that 8.04.2 fixes some issues with the kernel clocksource mechanism that can result in timing and stability issues under virtualised instances, which is relevant to me, as I shall be running it under VMware ESXi. I am aware that these issues can be circumvented by passing some boot args to the kernel, but if 8.04.2 is just around the corner, I'm happy to wait. If on the other hand it's a month or more away, then I'd rather just start off on 8.04.1 and upgrade at some point in the future.

This VMware KB article also provides some details, including an (incorrect?) statement that the issue will be fixed in 8.04.2:
[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1007020](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1007020)

I apologise if some of my information is not accurate, but I've had a hard time trying to sort out the good information from the bad.

Thanks for any advice!

---

### Post by sdennie on 2009-01-07
I'm not sure what the real release date is but, 8.04.X releases are really just timestamped releases of 8.04.  What I mean by that is if you install 8.04 and then get all the available updates, you are now running 8.04.1 (and something that probably very much approximates 8.04.2 based on the dates you've provided).  If the problem you are describing is supposed to be fixed in 8.04.2, it means that it's fixed in a fully updated 8.04.1 and 8.04 as they are just different names for the same release.

---

### Post by ralish on 2009-01-09
Thank-you very much for the clarification, it has cleared up my understanding of Ubuntu release labels significantly.

It sounds like I have little reason to wait for the 8.04.2 release, and so shall get started straight away using an updated 8.04.1 release.

Thanks again for the help.

---

