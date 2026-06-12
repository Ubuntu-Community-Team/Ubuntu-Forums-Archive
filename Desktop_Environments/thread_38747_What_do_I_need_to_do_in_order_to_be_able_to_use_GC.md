---
title: "What do I need to do in order to be able to use GCC / g++?"
date: 2005-06-01
forum: Desktop Environments
---

### Post by erik-the-red on 2005-06-01
Obviously, not having GCC on your install forbids you to install from source.

Apparently, Warty's default installation does not install GCC.

Moreover, I am unsuccessful in using either synaptic or apt-get.

However, I have been very successful in using "sudo dpkg -i" from the online Debian archive.

I have installed gcc-3.3, gcc-3.3-base, and cpp-3.3 successfully.

However, when I try to install g++-3.3, it depends on and says libstdc++5 has not been configured.

When I try to resolve this dependency, it says g++-3.3 is dependent and has not been configured.

What can I do?

---

### Post by DJ_Max on 2005-06-01
What was your problem with installing gcc from the ubuntu repositories? Going with another distributions package is asking for trouble, especially with something like gcc.

You ran into a dependency problem due to mixing packages from another OS.

---

### Post by az on 2005-06-01
You have all the tools on the cd.  You should be able to install "build-essential" and that will bring everything else in....

WHat is the problem with synaptic, or even sudo apt-get install build-essential?

---

