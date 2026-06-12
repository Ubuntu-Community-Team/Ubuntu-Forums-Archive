---
title: "Removing Mozilla-browser."
date: 2006-07-03
forum: Desktop Environments
---

### Post by Blazeix on 2006-07-03
Hi. I recently installed the Eclipse Programming IDE, and as a dependency it installed mozilla-browser. I use firefox, so I have no need for mozilla browser. I tried to uninstall it, but it tries to remove eclipse when I try to remove mozilla-browser. Is there some way I can remove mozilla-browser without removing eclipse?

---

### Post by Ramses de Norre on 2006-07-03
When it's a dependency it probably uses some parts of mozilla-browser internally, so I don't think you can remove it without breaking eclipse.

---

### Post by glotz on 2006-07-03
Does eclipse have a forum maybe? They'd probably know.

---

### Post by Blazeix on 2006-07-03
Well, I went to the eclipse channel in IRC. They all said that its probably a problem with the package management system, and I should contact the package maintainers. I guess the next step would be to go ubuntu's [bugzilla](https://launchpad.net/distros/ubuntu/+bugs)? 



[QUOTE=IRC Channel Transcript]
<Blazeix> O.K. I have firefox, but I don't think I need mozilla. Is there a way to uninstall it manually? My package manager (apt-get) wants to uninstall all of eclipse if I try to uninstall mozilla.
<ashridah> ugh.
<rcjsuen> better talk to you distro
<Blazeix> o.k.
<ashridah> that's really something we can't help with, only the package maintainers can fix that. eclipse *should* be able to work with firefox, assuming your distro's version shipped with libxpcom and whatnot
[/QUOTE]

---

