---
title: "Don't auto update certain packages (apt-get)"
date: 2005-09-06
forum: Desktop Environments
---

### Post by loon on 2005-09-06
I had to install a much early wine so I could install Lotus Notes 6.5 without any of the problems 6.5 has with the latest wine.

Well, now I have the auto updater wanting to updat the wine packages on my system and that is a huge NONO considering this is a company machine with Ubuntu on it and my work on it.  I'd hate to go through the trouble setting everthing up with wine/notes again because of some automatic updates.

Is there a way to have the packaging system ignore packages needed for updates?

Thanks

- l00n

---

### Post by oofnik on 2005-09-06
You can just lock the version in Synaptic - highlight wine and go to Package -> Lock Version. That should do it I think..

---

### Post by Harleen on 2005-09-06
I don't know how to achieve this with apt-get. But that was the main reason for me to use aptitude. Beside a neat (text-based) front end it provides the possibility to hold packages at the current version by pressing "=" on the package name.

---

### Post by loon on 2005-09-06
Will it use the apt-get repos if I run that?

---

### Post by Harleen on 2005-09-07
[QUOTE=loon]Will it use the apt-get repos if I run that?[/QUOTE]
 Synaptic as well as aptitude are front ends for apt-get. So yes, they use the same repositories.

---

