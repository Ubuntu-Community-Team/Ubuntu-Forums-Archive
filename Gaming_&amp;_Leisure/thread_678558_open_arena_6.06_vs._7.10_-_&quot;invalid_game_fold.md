---
title: "open arena 6.06 vs. 7.10 - &quot;invalid game folder&quot;"
date: 2008-01-26
forum: Gaming &amp; Leisure
---

### Post by transporter_ii on 2008-01-26
I have two 7.10 systems and a 6.06 that I can't upgrade because the ATI video driver on the 6.06 system stops 3d rendering between 6.06 and 7.10 (unfixed bug!).

I started an open arena server on a 7.10 system. Both 7.10 clients can join right up. I downloaded Open Arena 0.7.0 on to the 6.06 system, and it runs fine but can't join the running server on the 7.10 system because it gets an "invalid game folder" error. I looked up the error and the solution is that it must be the latest version.

Fine, I patch it to 0.7.1., and I get the same error.

Can anyone with a 6.06 system even join a server running on a 7.10 system?

I was all set to play open arena with my kids, but what I ended up doing was wasting about 4-plus hours of time trying to get OA to actually work...

I even copied the baseoa files from the 7.10 system to the 6.06 system...but had no luck with that.

---

### Post by transporter_ii on 2008-01-26
I was able to get an OA server going in a manner that both Ubuntu 7.10 systems and the 6.06 system could join.

Basically, what I did was take the OA download that I put on the 6.06 (because it doesn't have a .deb package for it), and move it to both the 7.10 systems. I then started the server on the 6.06 system and had all of the OA clients join it.

I'm certainly no expert on any of this, but I would say that I either didn't apply the OA upgrade patch correctly to the copy I downloaded, or there is some difference between the Ubuntu 7.10 .deb package install of OA / openarena-server and the version you can download from [http://www.openarena.ws/](http://www.openarena.ws/). 

I'm not sure either way, but as soon as I got the same version on all three systems, it fired right up.

I'm kind of thinking that if someone has a mixed Ubuntu environment and want to play OA, they might be better off just downloading it and installing it instead of trying to add it through the package manager...but that's just me.

Or better yet, they could release a package for 6.06 that installed the exact OA version as the 7.10 package!

Transporter_ii

---

