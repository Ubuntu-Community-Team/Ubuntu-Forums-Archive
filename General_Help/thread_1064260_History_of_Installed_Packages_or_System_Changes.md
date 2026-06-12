---
title: "History of Installed Packages or System Changes?"
date: 2009-02-08
forum: General Help
---

### Post by wall0645 on 2009-02-08
Hi, my Ubuntu 8.04 desktop has as of this morning started freezing up very often.

Is there a way to view a history of changes made to the system, or a history of packages installed, so that I can possibly undo whatever I did that started causing these freezings?

To be a little more descriptive of what the freezing is like... it happens when I have a few things going at once, maybe a couple windows of Firefox with multiple tabs each, or something like that, and then some graphical irregularities start occurring. Patterns of pink and light green/blue lines or boxes start appearing everywhere. Very quickly this leads to a lockup of the windows, with the mouse still able to move. Eventually the mouse too freezes up. Ctrl+Alt+Backspace ineffective. Hard shutdown the only way out.

Please help. Mainly looking for the possible histories, or maybe like "recent packages installed" list or something... but if anyone has an idea about the cause of the freezes, that would be great too. Thank you!

---

### Post by plucky on 2009-02-08
> Is there a way to view a history of changes made to the system, or a history of packages installed, so that I can possibly undo whatever I did that started causing these freezings?


**System > Administration > Synaptic Package Manager > File > History** will show you what has been updated on your system.

If it is a kernel update causing the problem,you could boot an earlier kernel from the Grub boot menu.Also check if a new video card driver has been installed.


Good Luck

---

### Post by drs305 on 2009-02-08
For packages installed or removed outside of synaptic, you can look at:
*/var/log/apt/term.log*

Synaptic's log will show only activity initiated by Synaptic. The term.log records activity by APT, inclucing apt-get, aptitude *and* Synaptic (although not nearly as easy to read).

---

### Post by mavior on 2009-02-23
> **wall0645 said:**
> Hi, my Ubuntu 8.04 desktop has as of this morning started freezing up very often.

Is there a way to view a history of changes made to the system, or a history of packages installed, so that I can possibly undo whatever I did that started causing these freezings?

Please help. Mainly looking for the possible histories, or maybe like "recent packages installed" list or something... but if anyone has an idea about the cause of the freezes, that would be great too. Thank you!



I think you can solve with apt-log [http://mavior.eu/apt-log](http://mavior.eu/apt-log).
It will give you a fine-grained control over your logs.

It will solve also the follow problem:

> **drs305 said:**
> For packages installed or removed outside of synaptic, you can look at:
*/var/log/apt/term.log*

Synaptic's log will show only activity initiated by Synaptic. The term.log records activity by APT, inclucing apt-get, aptitude *and* Synaptic (although not nearly as easy to read).

---

