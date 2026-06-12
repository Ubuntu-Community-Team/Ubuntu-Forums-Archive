---
title: "gnome-shell dependency errors when trying to install"
date: 2010-05-29
forum: Desktop Environments
---

### Post by steve19137 on 2010-05-29
so i saw a video on gnome-shell today, and i instantly had to have it. so having seen that there was a gnome-shell source in ubuntu tweak. i enabled it, and ran "sudo apt-get install gnome-shell" in my terminal. i get some dependency errors. here the output. 

```
steven@ubuntu-laptop:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-shell: Depends: libgjs0 but it is not going to be installed
               Depends: gjs (>= 0.7) but it is not going to be installed
E: Broken packages

```

what can i do?

---

