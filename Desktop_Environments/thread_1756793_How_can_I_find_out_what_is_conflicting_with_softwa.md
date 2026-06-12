---
title: "How can I find out what is conflicting with software installs?"
date: 2011-05-12
forum: Desktop Environments
---

### Post by maddbaron on 2011-05-12
I accidently uninstalled empathy and now it won't reinstall. I'm trying to find out see what is causing the conflict and resolve the dependencies but I have no idea where to look...

help please

---

### Post by jerrrys on 2011-05-12
you can do a **sudo apt-get install empathy** and it should tell you whats going on.  or go to 'synaptic package manager' and load from there and it should also tell you what needs to be resolved.  what kind of error msg did you get ?

---

### Post by maddbaron on 2011-05-13
> **jerrrys said:**
> you can do a **sudo apt-get install empathy** and it should tell you whats going on.  or go to 'synaptic package manager' and load from there and it should also tell you what needs to be resolved.  what kind of error msg did you get ?

```
$ sudo apt-get install empathy
[sudo] password for wordsmith: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 empathy : Depends: libchamplain-0.10-0 (>= 0.9.0) but it is not installable
           Depends: libchamplain-gtk-0.10-0 (>= 0.9.0) but it is not installable
           Depends: libgck0 (>= 2.91.1) but it is not installable
           Depends: libgcr-3-0 (>= 2.91.4) but it is not installable
           Depends: libgnome-control-center1 (>= 1:2.91.2) but it is not installable
           Recommends: nautilus-sendto-empathy but it is not going to be installed
           Recommends: freedesktop-sound-theme but it is not installable
E: Broken packages

```

i unchecked the ppa with 3.1.1.1 but it still shows up as a conflict... if i turn off all ppa's would that let me load empathy 2.34?

turned off all 3rd party ppa's then reinstalled the 2.34 version then locked version, i'll check every couple of months if a new empathy update is released but for now i'll roll with 2.34...

---

