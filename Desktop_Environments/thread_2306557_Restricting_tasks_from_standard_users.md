---
title: "Restricting tasks from standard users"
date: 2015-12-16
forum: Desktop Environments
---

### Post by shalev.siso on 2015-12-16
Hi all,
New at ubuntu after years of windows experience :)

i'm looking to restrict most (or even just specific if not most) tasks from standard users (same as secpol.msc or domain GPO in windows), i.e: user won't be able to open terminal, system settings etc. I'm even thinking about the users not able to list and browse the file system.

Is there a central location for that? is it even possible?

I have noticed that a lot of options are not really available if the user is not sudoing but i really want it harden..



tnx in advance!

---

### Post by sudodus on 2015-12-16
Welcome to the Ubuntu Forums :-)

1. You can let those users log in to the ***guest account*** in Ubuntu. It will be very limited.

2. If you want further limits you can install a linux kiosk, which would allow users to use only a web browser (and nothing else). Examples: Porteus Kiosk and Webconverger. See this link: [linux-distros-for-kiosks](http://tuxdiary.com/2014/11/05/linux-distros-for-kiosks/)

---

