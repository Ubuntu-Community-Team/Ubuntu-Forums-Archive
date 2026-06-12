---
title: "krunner (Alt+F2) does not see my $PATH after upgrade to 12.10"
date: 2013-07-07
forum: Desktop Environments
---

### Post by street spirit on 2013-07-07
I just upgraded from Kubuntu 12.04 (LTS) to 12.10.

Before the upgrade, krunner would recognize a custom $PATH set in .bashrc, but this seems to work differently now.

In my .bashrc, I adjust the $PATH to include /home/username/bin. This works as usual in konsole and other terminals, but not when I try to run something from ~/bin with krunner. A little testing suggests that KDE isn't reading any .bash* config files at startup (anymore?).

Has this behavior been changed?
And how do I get krunner to see my custom $PATH now?

---

### Post by street spirit on 2013-08-14
For the record, this question was answered on [the KDE forums]("http://forum.kde.org/viewtopic.php?f=66&t=111948").
Summary: put a .sh file with the necessary paths in ~/.kde/env.

---

