---
title: "bug report : fvwm-gnome"
date: 2008-07-30
forum: Desktop Environments
---

### Post by satheesan on 2008-07-30
Hello,

I was trying to install fvwm in ubuntu Hardy Heron. I have already installed xfce in addition to gnome. But I am getting the following error message.
--------------------------------------------------------------------------
sudo apt-get install fvwm*
[sudo] password for satheesan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting fvwm-beta for regex 'fvwm*'
Note, selecting fvwm1 for regex 'fvwm*'
Note, selecting fvwmtabss for regex 'fvwm*'
Note, selecting fvwm-icons for regex 'fvwm*'
Note, selecting fvwm-gnome for regex 'fvwm*'
Note, selecting fvwm-themes for regex 'fvwm*'
Note, selecting fvwm-crystal for regex 'fvwm*'
Note, selecting fvwm-common for regex 'fvwm*'
Note, selecting fvwm95 for regex 'fvwm*'
Note, selecting fvwmtabs for regex 'fvwm*'
Note, selecting fvwm for regex 'fvwm*'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  fvwm: Conflicts: fvwm-gnome
E: Broken packages
-------------------------------------------------------------------------

Please help me to solve this problem?
Thanks & Regards

Satheesan

---

### Post by prshah on 2008-07-30
> **satheesan said:**
> I was trying to install fvwm in ubuntu Hardy Heron. 

Just install the fvwm metapackage; there's no need for the wildcard "*"```

sudo apt-get install fvwm
```

---

