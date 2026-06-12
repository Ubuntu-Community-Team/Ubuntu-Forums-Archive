---
title: "How to uninstall gnome-shell from ricotz/testing and install from gnome team?"
date: 2012-06-27
forum: Desktop Environments
---

### Post by orange2k on 2012-06-27
I would like to uninstall gnome-shell installed by adding ricotz/testing repository and install the standard gnome-shell provided by the gnome team.

How to accomplish this? I've tried to uninstall gnome-shell and then to remove the repository. Then I tried to install gnome-shell again but I encountered problems: some packages were held back - so the terminal said.

What should I do to do it correctly?

---

### Post by markbl on 2012-06-27
See ppa-purge. Although be careful. I used ppa-purge some time ago to rid the ricotz ppa and lost all X/unity/gnome completely although I wasn't paying attention to what packages were going to be removed. However "aptitude install ubuntu-desktop gnome-shell" brought it all back. Generally I use aptitude to do this kind of stuff because it will provide alternative package removal/addition solutions which you can choose from.

I think the ricotz ppa is too unstable for anything other than experimental use. Just use the gnome3 team ppa.

---

### Post by orange2k on 2012-06-28
> **markbl said:**
> I think the ricotz ppa is too unstable for anything other than experimental use. Just use the gnome3 team ppa.

I noticed that too late. I used ppa-purge - it worked fine...

---

