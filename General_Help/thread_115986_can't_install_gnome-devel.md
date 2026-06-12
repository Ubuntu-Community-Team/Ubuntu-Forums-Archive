---
title: "can't install gnome-devel"
date: 2006-01-11
forum: General Help
---

### Post by pinky on 2006-01-11
hello,
i have tried to install gnome-devel on Ubuntu 5.10 but there seems to be many dpency problems:

```

aptitude install gnome-devel
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  gnome-devel: Depends: gnome-core-devel (= 1:2.10.1.1ubuntu1) but it is not installable

```

that's the first point were i get wondering gnome-core-devel (= 1:**2.10.1.1ubuntu1**) isn't gnome2.12 the default gnome version?

Than i tried to install gnome-core-devel:

```

aptitude install gnome-core-devel
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  gnome-core-devel: Depends: libbonoboui2-dev (>= 2.8.1) but it is not installable
                    Depends: libeel2-dev (>= 2.10.0) but it is not installable
                    Depends: libnautilus-extension-dev (>= 2.10.1) but it is not installable
                    Depends: libgnome2-dev (>= 2.10.0) but it is not installable
                    Depends: libgnomevfs2-dev (>= 2.10.1) but it is not installable
                    Depends: libpanel-applet2-dev (>= 2.10.1) but it is not installable
                    Depends: libgnomeui-dev (>= 2.10.0) but it is not installable
                    Depends: libxslt1-dev (>= 1.1.12) but it is not installable

```

Is it even possible to install gnome-devel on ubuntu 5.10?

---

### Post by dmartin on 2006-02-18
Same issue here.  I've looked everywhere, I've asked on IRC.  No one seems to have any idea what I'm talking about.  I know it's not everyone, but certainly we aren't the only two people trying to do Gnome development on Ubuntu!

I just don't understand how a repository can have unmet dependencies and be labeled "stable".

---

### Post by sean on 2006-05-19
I have the same problem in dapper.  Further, autoconf/automake tools are somewhat broken.

Sean

---

