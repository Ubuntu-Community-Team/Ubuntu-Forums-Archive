---
title: "Can't install gnome3-session"
date: 2011-05-14
forum: Desktop Environments
---

### Post by Thoddy on 2011-05-14
I installed gnome-shell from the respective PPA on my 11.04 ubuntu installation and I have problems running this combination smoothly! Sometimes when I log in I get Metacity windows and no Gnome session, sometimes I get the correct Gnome3 session...

I guess that somehow the packages I have installed on my system got mixed up.

Anyway: when I try to "sudo apt-get install gnome3-session" I get the following error:
> The following packages have unmet dependencies:
 gnome3-session : Depends: gnome-session-bin (< 2.33) but 3.0.1-0ubuntu1~build2 is to be installed
                  Depends: gnome-session-common (= 2.32.1-0ubuntu20) but 3.0.1-0ubuntu1~build2 is to be installed
E: Broken packages


Any ideas how I can resolve that??

---

### Post by Andrew V Dedkov on 2011-06-21
The same question.

---

### Post by bmbaker on 2011-06-22
try logging into gnome classic and open up synaptic and goto edit>fixbroken packages and then apply
and try installing it from synaptic :-)

---

