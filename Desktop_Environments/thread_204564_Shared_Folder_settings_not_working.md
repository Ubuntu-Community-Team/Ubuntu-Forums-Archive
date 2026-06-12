---
title: "Shared Folder settings not working"
date: 2006-06-27
forum: Desktop Environments
---

### Post by electroconvulsive on 2006-06-27
Hi Im sharing files using Samba between 2 different linux distros and a windows machine. I have correctly set up my samba config file and had shares working between both of my machines last night. Today I turned them both on and the ubuntu shares were not visible from the other machine. When I went into my Shared folders panel it did not appear and when I added it again it did not save. Has anyone else come across this and how do I solve it?

[COLOR="Red"]Solved problem, dont need shared folders to run samba shares[/COLOR]. Firestarter settings to blame. Fix = [COLOR="RoyalBlue"]Firestarter: edit>preferences>advanced options>uncheck "block broadcasts from external network"
[/COLOR]
I think this may be useful to anyone having the same problem so I will leave it up for a while.

---

