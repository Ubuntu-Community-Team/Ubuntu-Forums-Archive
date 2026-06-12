---
title: "what to do: unable to get exlusive lock"
date: 2009-01-02
forum: General Help
---

### Post by sinkpink on 2009-01-02
I have ubuntu 8.10 gnome on my system.. while installing firestarter something went wrong and now when I try to start synaptic package manager this message appear: unable to get exlusive lock
Now I know I screwed something with iptable but I'm quite noob
so can't diagnose where it went wrong and what to (do to) repair.
btw. system was fully updated one h before that so everything is quite up to date.. 
Any sugestions?

---

### Post by donkyhotay on 2009-01-02
That error has nothing to do with firewalls or iptables. That error message means that synaptic or apt-get is still running on your system (it happens with interrupted installs). If synaptic or add/remove programs is not visible on the screen it's probably a stray process in the background. Killing the process will correct this. If you don't know how to do that just reboot the computer.

---

