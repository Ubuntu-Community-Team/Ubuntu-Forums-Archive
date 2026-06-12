---
title: "Depencies subtitleeditor sysv-rc-conf"
date: 2006-10-05
forum: Desktop Environments
---

### Post by cd-r80 on 2006-10-05
Installing sysv-rc-conf. I got depencies error:

What to apt-get to go on?
Yes I left finishing subtitleeditor, but why it complains now?

apt-get install sysv-rc-conf
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  subtitleeditor: Depends: libglademm-2.4-1c2a but it is not going to be installed
                  Depends: libglibmm-2.4-1c2a but it is not going to be installed
                  Depends: libgtkmm-2.4-1c2a but it is not going to be installed
                  Depends: iso-codes (>= 0.49-1ubuntu2) but it is not going to be installed
  sysv-rc-conf: Depends: libcurses-ui-perl but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).

---

### Post by rdmorton2 on 2006-10-19
I seem to have the same problem, although I did try ‘apt-get -f install’ and it did not seem to fix the problem.

Any other ideas?

---

### Post by cd-r80 on 2006-10-24
Late answer. I installed .tgz

---

