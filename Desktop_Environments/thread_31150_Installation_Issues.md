---
title: "Installation Issues"
date: 2005-05-02
forum: Desktop Environments
---

### Post by Linux_Noob on 2005-05-02
I keep getting this message when i try to install the bittornado-gui

[B]raymond@ubuntu:~$ sudo apt-get install bittornado-gui
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bittornado-gui: Depends: bittornado (>= 0.3.7-1) but it is not installable
                  Depends: libwxgtk2.4-python but it is not going to be installed
E: Broken packages[/B] 

This has happened with several packages Ive wanted to install, this is only an example. Ive edited my sources.list to include all repositories but it didnt help.

Can anyone help??

---

### Post by nemin on 2005-05-02
[QUOTE=Linux_Noob]
This has happened with several packages Ive wanted to install, this is only an example. Ive edited my sources.list to include all repositories but it didnt help.[/QUOTE]
Just a guess, did you run ```
sudo apt-get update
``` after that?

---

### Post by Linux_Noob on 2005-05-02
Please disregard this post as the problem has been solved.

---

