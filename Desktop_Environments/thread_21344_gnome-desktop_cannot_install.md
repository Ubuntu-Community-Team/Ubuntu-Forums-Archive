---
title: "gnome-desktop cannot install"
date: 2005-03-21
forum: Desktop Environments
---

### Post by wbeck85 on 2005-03-21
I downloaded the Kubuntu install CD and really liked it. I have just about everything configured the way i want it. However, I want gnome. And i dont wanna have to reinstall the whole system, so i figured i would just apt-get it. Sounds good, right?
here's what I get:

wbeck85@ganganork:~$ sudo apt-get install gnome-desktop-environment
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-desktop-environment: Depends: nautilus-media (>= 0.8.1) but it is not going to be installed
E: Broken packages
wbeck85@ganganork:~$        

So, what can be done about that nautilus-media package?
wbeck85@ganganork:~$ sudo apt-get install nautilus-media
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nautilus-media: Depends: libnautilus2-2 (>= 2.7.1) but it is not installable
E: Broken packages
wbeck85@ganganork:~$ 

attempting to install libnautilus2-2 does not yeild any friuts either i get:

wbeck85@ganganork:~$ sudo apt-get install libnautilus2-2
Reading Package Lists... Done
Building Dependency Tree... Done
Package libnautilus2-2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnautilus-extension1-dbg nautilus libnautilus-extension1
E: Package libnautilus2-2 has no installation candidate
wbeck85@ganganork:~$

So, what do i do now?

I was thinking of a -f or -m option, but i didnt want to go to dependence hell, so i backed down from that idea.

---

### Post by wbeck85 on 2005-03-21
I think i solved my problem, and i feel stupid cuz i figured it out immediately after posting the above :)

apt-get install ubuntu-desktop works. it is installing now. No apparent dependency problems. I'll letya know if this works in a minute.

---

