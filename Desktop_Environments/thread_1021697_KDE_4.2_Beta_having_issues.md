---
title: "KDE 4.2 Beta having issues"
date: 2008-12-25
forum: Desktop Environments
---

### Post by Mewshi on 2008-12-25
Hello!

Oh my girlfriend's machine (running the 4.2 Beta), there are no window decorations, and programs don't show up in the taskbar.  Where should I start for troubleshooting.

---

### Post by Wille on 2008-12-26
> **Mewshi said:**
> Hello!

Oh my girlfriend's machine (running the 4.2 Beta), there are no window decorations, and programs don't show up in the taskbar.  Where should I start for troubleshooting.

Try removing the ~/.kde directories to get a clean slate.

---

### Post by rudihawk on 2008-12-26
Update your system could also help, to get the latest packages.

---

### Post by GameManK on 2008-12-26
Sounds like kwin isn't running.  What happens if you try to run it from a konsole?

---

### Post by uboltun on 2009-04-24
I had a similar problem. After upgrading kwin stoped loadin and complained about a missing library libkephal. This fixed the problem for me:
sudo aptitude install kdebase-workspace

it suggested to upgrade a bunch of kde packages including the kde windows manager to 4.2 and removing kdeplasma-addons.

---

