---
title: "Splashy doesn't open"
date: 2008-12-11
forum: General Help
---

### Post by Dipper on 2008-12-11
I've removed usplash, per the suggestions that I've read on the board and I have installed splashy.  However, when I type "splashy" in the Run command, nothing happens.  Shouldn't a program open that allows me to choose the .so theme to use?  I'm not sure how to get this to work.  I am using Kubuntu 8.10.

---

### Post by Speed Demon on 2009-01-03
No siree Bob... you don't type "splashy" into the box. You need to use the GTK application (I know, I know) "startup-manager" to do this.
```
sudo apt-get install startupmanager
```
then launch StartupManager, and it'll detect splashy and allow you to manage themes.
You're welcome :P

---

