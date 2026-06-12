---
title: "Xubuntu install failure from Ubuntu - package dependency nightmare!"
date: 2005-10-23
forum: Desktop Environments
---

### Post by desquer on 2005-10-23
I'm a newbie who last used Suse 7.0/KDE and Gnome on an old desktop.  I'm trying to upgrade/downgrade to Xubuntu from Ubuntu on an old Dell Pentium II laptop with 256megs of ram. Everything works, even the wireless, with the wrapper instructions I found online.

I am trying to make this a proof of concept laptop for my intermediate school as I teach math and am the technology teacher.

With Gnome, things are slow in scrolling and browsing and I assume they will be even slower with KDE. I want to downgrade to Xubuntu due to the speed of the machine.

When I tried in the terminal window to "apt-get install xubuntu-desktop", I got the following web of dependencies.

Xubuntu depends xfce4 depends xwmf4 depends libxcomposite1 "but it is not installable" (see below).

Please help a teacher show that Windows is not the only game in town for public education!

TIA,
Dave

--------------------------------------------------------------------

dave@ubuntu:~$ sudo apt-get install xubuntu-desktop
Password:
Sorry, try again.
Password:
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
  xubuntu-desktop: Depends: abiword but it is not going to be installed
                   Depends: graveman but it is not going to be installed
                   Depends: ivman but it is not installable
                   Depends: xfce4 but it is not going to be installed
                   Depends: xfce4-sensors-plugin but it is not going to be installed
                   Depends: xfmedia but it is not going to be installed
E: Broken packages

dave@ubuntu:~$ sudo apt-get install xfce4
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
  xfce4: Depends: xfwm4 (>= 4.2.2-1) but it is not going to be installed
         Depends: xfwm4-themes (>= 4.2.2-1) but it is not going to be installed
E: Broken packages

dave@ubuntu:~$ sudo apt-get install xfwm4
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
  xfwm4: Depends: libxcomposite1 but it is not installable
E: Broken packages
dave@ubuntu:~$

---

### Post by Ampersand on 2005-10-23
It looks like you've got the universe repository enabled,  since xubuntu-desktop is there.

Have you tried doing a sudo apt-get update just before trying to get xubuntu-base?

---

### Post by desquer on 2005-10-23
I'll go try it now!
Thanks,
Dave

---

### Post by desquer on 2005-10-23
Nope, same problem!

Dave

---

