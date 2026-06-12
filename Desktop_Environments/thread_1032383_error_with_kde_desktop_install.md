---
title: "error with kde desktop install"
date: 2009-01-06
forum: Desktop Environments
---

### Post by mdewet on 2009-01-06
I am trying to install the kubuntu desktop on my 8.04 (currently gnome), but I keep on getting this error

```
muerte@muerte:~$ sudo apt-get install kubuntu-desktop
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
  kubuntu-desktop: Depends: kde-guidance but it is not going to be installed
                   Depends: kdenetwork-filesharing but it is not going to be installed
                   Recommends: kde-guidance-powermanager but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed
E: Broken packages

```

I did a 

```
sudo apt-get update
```

still doesn't work, any ideas?

also, it worked the first time I tried it, but I didn't install due to my crappy internet connection, so I tried using the kubuntu cd to install it.  It then gave me this error so I removed the cd from sources.list to enable the download of the package again, but it still gives me this error now?!?

---

