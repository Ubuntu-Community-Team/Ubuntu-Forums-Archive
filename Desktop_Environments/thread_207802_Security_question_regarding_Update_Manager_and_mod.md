---
title: "Security question regarding Update Manager and modified sources.list"
date: 2006-07-02
forum: Desktop Environments
---

### Post by willconant on 2006-07-02
I'm completely new to Ubuntu and rather new to debian. At the suggestion of dozens of How-Tos out there, I've ended up modifying and adding to my /etc/apt/sources.list. How does Ubuntu choose which packages to prompt me to download using the automatic Update Manager? Does it accept automatic updates from every apt source in my list? If so, does this pose a security concern?

Thanks in advance for any help!

-Will

---

### Post by Matthew Bartram on 2006-07-02
Rather than modifying your sources.list, you could go to synaptic: settings -> repositories -> add -> custom
I don't know what difference this makes, except that when I tried to install the ekiga repository for breezy, that worked, whilst adding to sources.list didn't.

I think that the automatic update only looks at certain repositories, but I can't find where this is set. I'm not sure - I'm new to this as well. In any case, if either synaptic or the automatic update are asked to install something that isn't authenticated, then it will warn you first, and ask you if you really want to install it.

---

