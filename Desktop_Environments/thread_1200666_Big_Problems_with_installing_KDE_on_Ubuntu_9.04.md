---
title: "Big Problems with installing KDE on Ubuntu 9.04"
date: 2009-06-30
forum: Desktop Environments
---

### Post by LexLuthor08 on 2009-06-30
I want to install KDE (preferrably the newest 4.3) on my jaunty ubuntu.
I tried everything, I added deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main to the repositories and activated the backports. 

The error I get for trying to install kubuntu-desktop is:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: language-selector-qt but it is not going to be installed
                   Recommends: libqca2-plugin-ossl but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed
                   Recommends: quassel but it is not going to be installed
E: Broken packages
```

I tried to install those packages separately but then I ran into a lot of other dependency errors.

Can it be that hard to get kde on ubuntu??

---

### Post by colau on 2009-06-30
> **LexLuthor08 said:**
> I want to install KDE (preferrably the newest 4.3) on my jaunty ubuntu.
I tried everything, I added deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) jaunty main to the repositories and activated the backports. 

The error I get for trying to install kubuntu-desktop is:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: language-selector-qt but it is not going to be installed
                   Recommends: libqca2-plugin-ossl but it is not going to be installed
                   Recommends: openoffice.org-kde but it is not going to be installed
                   Recommends: quassel but it is not going to be installed
E: Broken packages
```

I tried to install those packages separately but then I ran into a lot of other dependency errors.

Can it be that hard to get kde on ubuntu??

[http://www.cyberciti.biz/faq/ubuntu-linux-install-kde-42/](http://www.cyberciti.biz/faq/ubuntu-linux-install-kde-42/)

---

### Post by LexLuthor08 on 2009-06-30
ok, I am installing this kde-nightly now its 530MB.

Isn't there missing something when I only install kde and not the whole kubuntu-desktop?

---

