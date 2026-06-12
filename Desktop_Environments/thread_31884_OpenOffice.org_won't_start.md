---
title: "OpenOffice.org won't start"
date: 2005-05-05
forum: Desktop Environments
---

### Post by Ndlovu on 2005-05-05
I've been using Hoary happily since it's official release, and suddenly OpenOffice.org won't load up. I can't think of anything that's changed since I last used it about a week back. The first time I got the error was when I tried opening a word (.doc) document from Thunderbird.

The splash screen appears, followed by a cryptic error message: "The application cannot be started. RegisterServices, configureUcb". When I click OK, the process soffice.bin starts taking up about 90% of CPU resources.

I've tried loading OOo as a different user, and then it doesn't even show the splash screen (but it does say something like "Starting OpenOffice.org writer" on the task bar for a brief time).

I tried reinstalling OOo, which didn't seem to affect the behaviour at all. I got this error message when trying that (not sure if it's related):
dpkg: error processing /cdrom//pool/main/o/openoffice.org/openoffice.org-bin_1.1.3-8ubuntu2_i386.deb (--unpack):
 unable to stat `./usr/lib/openoffice/program/libtplx645li.so' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)

Any help would be appreciated, OpenOffice.org is my core productivity application, and I'd love to tell people that it's better than MS Office. As long as it's not working, colleagues will be less inclined to migrate.

Thanks,
Rudi

---

### Post by Ndlovu on 2005-05-05
Okay, I've sorted out the problem by completely removing and reinstalling OpenOffice.org in Synaptic. Still no idea what caused it.

---

