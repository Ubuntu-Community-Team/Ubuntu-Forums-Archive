---
title: "Problems installing dosbox"
date: 2005-12-22
forum: General Help
---

### Post by La1nE on 2005-12-22
Well, im trying to install dosbox to play an old game or two, but i seem to have encountered som difficulties. 

at first, ill try apt-getting it.
```

laine@workgroup:~$ sudo apt-get install dosbox
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
  dosbox: Depends: libsdl-sound1.2 but it is not going to be installed
E: Broken packages
```

That seems odd. And what's the deal with the broken package? apt-get update / upgrade does'nt solve it. Oh well, ill try getting the libsdl-sound package:

```

laine@workgroup:~$ sudo apt-get install libsdl-sound1.2
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
  libsdl-sound1.2: Depends: libsmpeg0 (>= 0.4.4-7) but it is not going to be installed
E: Broken packages
```

More broken packages, and libsmpeg0 this time? That's odd. Well, I'll try getting libsmpeg instead!

```

laine@workgroup:~$ sudo apt-get install libsmpeg0
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  libopenal0 libsmpeg0c2 rss-glx
The following NEW packages will be installed:
  libsmpeg0
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 92.9kB of archives.
After unpacking 5775kB disk space will be freed.
Do you want to continue [Y/n]?
```

Well, this doesn't seem good at all. Is it ok to replace the tre packages with libsmpeg0? 

Any help would be appriciated!

---

### Post by La1nE on 2005-12-23
*boink

Noone? I could really need som help with this. :|

---

