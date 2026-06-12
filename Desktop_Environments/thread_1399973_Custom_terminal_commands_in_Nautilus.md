---
title: "Custom terminal commands in Nautilus?"
date: 2010-02-06
forum: Desktop Environments
---

### Post by Christian Knudsen on 2010-02-06
With Thunar in Xubuntu I was able to add my own custom right-click terminal commands, but I don't seem to be able to do this in Nautilus? I was able to add a command in Thunar that would automatically make a list.txt file with all the files in the current directory ("ls > list.txt"), which is really helpful for some work I'm doing. Is it possible to do this with Nautilus in Ubuntu? I tried nautilus-actions, but that only seems to allow you to call another program, not call terminal commands.

---

### Post by VCoolio on 2010-02-06
You can do so with [Nautilus scripts]("https://help.ubuntu.com/community/NautilusScriptsHowto?highlight=%28%28NautilusScriptsHowto%29%29"). Put them in ~/.gnome2/nautilus-scripts and make them executable.

---

### Post by Christian Knudsen on 2010-02-06
Thanks! I'll give it a try.

---

