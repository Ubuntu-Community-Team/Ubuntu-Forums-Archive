---
title: "Qt theme issues"
date: 2011-11-17
forum: Desktop Environments
---

### Post by authentik on 2011-11-17
Hello, I have a fresh install of Lubuntu 11.10 and I have problems setting the qt theme not to stick out. No matter which option I select either program specific - like in Skype or system-wide via qtconfig - get the same ugly Qt3-esque theme, as seen in the attachment. Does anyone have an idea of how to resolve that?

---

### Post by Symod on 2011-11-27
I had the same problem, I even asked a question on [AskUbuntu]("http://askubuntu.com/questions/82590/why-dont-qt4-apps-in-lubuntu-pick-up-the-gtk-theme"), but luckily found an answer in Arch forums.

The solution is to install "libgnomeui" package from the repositories. The name in Ubuntu's repositories is libgnomeui-0. It will pull in a few dependencies, but it solved the problem for me (log in/out if necessary).

```
sudo apt-get install libgnomeui-0
```

You can see the list of dependencies [here]("http://packages.ubuntu.com/oneiric/libgnomeui-0").

This thread reminded me, I should probably file a bug about this since the solution is really not clear at all.

---

