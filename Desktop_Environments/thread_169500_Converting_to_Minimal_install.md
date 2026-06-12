---
title: "Converting to Minimal install"
date: 2006-05-02
forum: Desktop Environments
---

### Post by davehahn on 2006-05-02
I installed ubuntu, and then removed gnome, X, and a whole bunch of stuff I knew was on there - but how can I get a list of packages (from the command line, synaptic won't work since I have not more gui!) that are still available to remove.  Basically, when I updated I saw it update firefox, which I forgot to uninstall, and I'd like to see what else I forgot to remove.  This is a simple box for smtp and dns -- no gui or anything.  Anything similar to synaptic for the command line?

---

### Post by hw-tph on 2006-05-02
aptitude is superior to both apt-get and synaptic and you should use it whenever possible (at all times!). For example - if you install an application using apt-get or Synaptic and then later remove it, the dependancies installed along with that particular program will still be left installed. aptitude will remove the dependancies unless other programs rely on them as well. Very neat.


Håkan

---

### Post by nanotube on 2006-05-02
the list of dependencies for "ubuntu-desktop" would be a good place to start looking: [http://packages.ubuntu.com/breezy/base/ubuntu-desktop](http://packages.ubuntu.com/breezy/base/ubuntu-desktop)
if you have doubts about something, best bet is to not remove it, so you dont screw anything up :)

---

### Post by rbean on 2006-05-02
You can do a "server" install that leaves out all the stuff you don't need (when you boot the installer CD, press F1 for a list of options)

Aptitude is very similar to Synaptic. It has the additional advantage that it will continue to work even if X gets b0rked.

---

### Post by bionnaki on 2006-05-03
start over and do a server install
that's all you have to do, really.

---

