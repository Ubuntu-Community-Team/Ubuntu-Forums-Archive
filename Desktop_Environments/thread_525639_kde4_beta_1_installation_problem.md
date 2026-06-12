---
title: "kde4 beta 1 installation problem"
date: 2007-08-14
forum: Desktop Environments
---

### Post by marcomangiante on 2007-08-14
Hello,

I'm trying to install the kde4 beta 1 on my kubuntu 7.04, but when I try to install the package kde4base-dev with Adept package manager, I obtain in the list the BRAK install message: can someone help me to resolve this problem. I also noticed that the package kde4base package remain with uninstalled word near of it.

--
Regards,

Marco Mangiante

---

### Post by sanone on 2007-08-19
I have the same problem... 

I tried to follow [this]("http://kubuntu.org/announcements/kde4-beta1.php") tutorial  but so far I haven't been able to install a single package :(

```
sander@san-ubuntu-laptop:~$ sudo apt-get install kde4base-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde4base-dev: Depends: kde4base (= 3.92.0-0ubuntu1~feisty1) but it is not going to be installed
                Depends: kdelibs5-dev but it is not going to be installed
                Depends: kdepimlibs5-dev but it is not going to be installed
E: Broken packages
```

---

### Post by sanone on 2007-08-19
Ah I found it...
I changed the default repository server from "The Netherlands" to "Main Server" and **tadaaah** we're installing!

Kinda ugly that not all the mirrors are updated!!!

---

### Post by marcomangiante on 2007-08-21
Hello,
I tried your suggestion but it don't works. When package manager try to install the package, I obtain this error:

lettura incompleta in buffer_copy (dpgk-deb backend su ./usr/lib/kde4/lib/libkichermain.so.2.0.0')

The message say that there is an incomplete read in buffer_copy on /usr/lib/kde4/lib/libkichermain.so.2.0.0, but sincerely I don't know what is the solution to this problem.
Maybe the package that kde4base-dev try to install (kde4base) now is corrupted and don't works, so even with the package that I downloaded and reinstalled (kde4base-dev) the problem is the same.

What I think to do is to try to download again the kde4base package and give it a try.

Hope this works.

--
Regards,

Marco Mangiante

---

