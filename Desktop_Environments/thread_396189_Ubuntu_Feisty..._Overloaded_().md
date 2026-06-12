---
title: "Ubuntu Feisty... Overloaded (?)"
date: 2007-03-29
forum: Desktop Environments
---

### Post by october1917 on 2007-03-29
There are many things in the new Ubuntu that i expect to see. Although there are some other that confuse me a little bit:

1) I have already the Wine installed. But the new Ubuntu comes with a Wine clone built-in (called Wine2). What should be done if i upgrade? Will it see the installed Wine and skip the Wine2 or after the upgrade i'll have two installations?

2) There are some applications that come with GNOME such us Totem, Rhythmbox, Evolution and many more. Some of them i think cannot be uninstalled (for example Totem). When i untick Totem in Synaptic, it says that it will uninstall also gnome-panel, gnome-desktop and some others. Am i wrong? Is there a way to uninstall them?

3) Anyway i have uninstalled some of them (Rythmbox, Thunderbird, Egika, Sound Juicer and some more) in my 6.10 and i don't want to automatically reinstall all these during the upgrade. What can i do to avoid this?

---

### Post by luisromangz on 2007-03-29
I don't know about Wine2, but about the other questions, well lets see

2) No, there is no reasonable way in which you can remove these packages if they are needed by a package you want to keep installed.

3) You should upgrade having installed the ubuntu-desktop package, and well it will reinstall some of the programs you have already uninstalled, so you will have to remove them again.

---

