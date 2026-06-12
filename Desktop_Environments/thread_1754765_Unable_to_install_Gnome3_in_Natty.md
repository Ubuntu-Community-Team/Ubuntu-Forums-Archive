---
title: "Unable to install Gnome3 in Natty"
date: 2011-05-10
forum: Desktop Environments
---

### Post by lamb123 on 2011-05-10
Hi,

Started with up to date machine.

i followed this:

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell gnome-session

```

running dist-upgrade gave me a small error to which I could click cancel or report bug, I clicked cancel but dist-upgrade finished successfully.

but when I try to run "sudo apt-get install gnome-shell gnome-session" I get following error:
```
eading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gnome-session : Depends: gnome-session-bin (< 2.33) but 3.0.1-0ubuntu1~build2 is to be installed
                 Depends: gnome-session-common (= 2.32.1-0ubuntu20) but 3.0.1-0ubuntu1~build2 is to be installed
 gnome-shell : Depends: gir1.2-mutter-3.0 (>= 3.0.0) but it is not going to be installed
               Depends: gir1.2-telepathyglib-0.12 but it is not going to be installed
               Depends: gir1.2-telepathylogger-0.2 but it is not going to be installed
               Depends: gjs but it is not going to be installed
               Depends: libgjs0b (>= 0.7.11) but it is not going to be installed
               Depends: libmutter0 (>= 3.0.0) but it is not going to be installed
               Depends: gnome-icon-theme-symbolic (>= 2.91) but it is not going to be installed
               Depends: gnome-themes-standard (>= 2.91) but it is not going to be installed
               Depends: gir1.2-gkbd-3.0 but it is not going to be installed
               Depends: gir1.2-polkit-1.0 but it is not going to be installed
               Depends: gir1.2-upowerglib-1.0 but it is not going to be installed
               Depends: mesa-utils but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
halp

---

### Post by lamb123 on 2011-05-10
apt-get -f install

helped it seems :D:D

---

### Post by sondo2121 on 2011-05-10
You may want to try what it mentioned (apt-get -f install gnome-shell gnome-session) then see what happens.  Did you try that?

EDIT: Looks like you beat me to the post :)

---

### Post by An Sanct on 2011-05-10
And how is gnome3 not like Unity? :)

---

### Post by lamb123 on 2011-05-10
pretty sweet actually, a little weird but can get used to it i think

---

