---
title: "Ubuntu does not have rpm"
date: 2009-01-28
forum: General Help
---

### Post by mlapl1 on 2009-01-28
I have a server running the latest versionof ubuntu but it does not have rpm - what should I do?

Thanks for any help
Andrew

---

### Post by Simian Man on 2009-01-28
Ubuntu uses Debian's dpkg instead of rpm.  Do you have an rpm file you need to install?  If so you might be able to find a .deb version, convert it with alien, or, as a last option, install something like CentOS instead.

---

### Post by mlapl1 on 2009-01-28
Wow - that was fast!. yes I do have an rpm file I need to install. 

Also, I do have another server running centos and may unpack the file there and then bring it back (but that defeats the purpose of .rpm). On top of that I do not have alien on my system.

Thank you
Andrew

---

### Post by fenian on 2009-01-28
You can use Alien to convert rpm to deb,[instructions are here.]("http://www.makeuseof.com/tag/easily-install-non-native-packages-in-ubuntu-with-alien/")

---

### Post by mlapl1 on 2009-01-28
Problem is I do not have alien either - and do not know where to get it - and how difficult it may be to install.

Thanks
Andrew

---

### Post by fenian on 2009-01-28
To install alien open a terminal and enter...

> sudo apt-get install alien

---

### Post by mlapl1 on 2009-01-28
Sorry - I should have read your instructions first. alien now appears to be installed correctly on my system.

Thank you
Andrew

---

### Post by Quarg on 2009-01-28
What he said. Alien is great, I use it all the time for messing around with rmp's on ubuntu. either sudo apt-get install alien, or use synaptic package manager system>Administration>Synaptic package manager and search 'Alien' install it. and when you have it, open the terminal: 
fakeroot alien /path of rpm/
and it should work out as a .deb file you can install

---

### Post by stchman on 2009-01-28
> **mlapl1 said:**
> Wow - that was fast!. yes I do have an rpm file I need to install. 

Also, I do have another server running centos and may unpack the file there and then bring it back (but that defeats the purpose of .rpm). On top of that I do not have alien on my system.

Thank you
Andrew

What is the rpm you need to install?  Chances are that the same package is available in the Ubunut repos.

---

### Post by Simian Man on 2009-01-28
> **stchman said:**
> What is the rpm you need to install?  Chances are that the same package is available in the Ubunut repos.

Many 3rd party software developers only distribute software for Linux as rpms.  This is largely because in the corporate sector, rpm based distros like Red Hat and Suse are by far the most popular.

Examples of such products I've run across include the Maya modeler and the synopsys tool suite.

---

### Post by browndog on 2009-01-28
Alien did an incredible job of converting an AVG anti-virus .rpm to .deb

---

