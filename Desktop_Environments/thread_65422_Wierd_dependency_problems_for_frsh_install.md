---
title: "Wierd dependency problems for frsh install"
date: 2005-09-13
forum: Desktop Environments
---

### Post by idn on 2005-09-13
Jus tried to install liferea but its asking me to install mozilla browser, which I dont want to do, I have firefox and epiphany already.

When i try to install amule:

root@idn:~# apt-get install amule
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
  amule: Depends: libglib1.2 (>= 1.2.0) but it is not installable
         Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
         Depends: libwxgtk2.4 (>= 2.4.2.6) but it is not going to be installed
E: Broken packages

With gift:

root@idn:~# apt-get install gift
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
  gift: Depends: giftd (= 0.11.8.1-1) but it is not going to be installed
E: Broken packages

Try to install the missing libs:

root@idn:~# apt-get install libwxgtk2.4
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
  libwxgtk2.4: Depends: libglib1.2 (>= 1.2.0) but it is not installable
               Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
               Depends
....you get the picture

 Whats ogin on!

Is there a problem with my machine?

---

### Post by Hairy_Palms on 2005-09-14
so this is on a fresh install during installation? sounds to me like youve got CD errors or a scratched disc meaning it cant read the data fo those packages.

---

