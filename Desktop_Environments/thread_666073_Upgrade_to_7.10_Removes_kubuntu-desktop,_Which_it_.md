---
title: "Upgrade to 7.10 Removes kubuntu-desktop, Which it Requires!"
date: 2008-01-13
forum: Desktop Environments
---

### Post by kidko on 2008-01-13
Hi, I'm currently running Kubuntu 7.04, and am trying to upgrade to 7.10 (mostly to get KDE4). Everything ran fine during the package updates, although I noticed applications like Konqueror being uninstalled...

Then, it uninstalled kubuntu-desktop, which it turned out to need for the upgrade to 7.10. It reported being unable to find a copy of x/ed/k/ubuntu on my system, which was its own fault. I can't reinstall anything, not even the metapackage or Konqueror or anything of the sort because of all sorts of broken dependancies. Typing "sudo apt-get install kubuntu-desktop" results in:
```
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
  kubuntu-desktop: Depends: kcontrol but it is not going to be installed
                   Depends: kde-systemsettings but it is not going to be installed
                   Depends: kdm but it is not going to be installed
                   Depends: kicker but it is not going to be installed
                   Depends: kmplayer-konq-plugins but it is not going to be installed
                   Depends: konq-plugins but it is not going to be installed
                   Depends: ksplash but it is not going to be installed
                   Depends: ksplash-engine-moodin but it is not going to be installed
                   Depends: kubuntu-default-settings but it is not going to be installed
                   Recommends: konqueror but it is not going to be installed
                   Recommends: kubuntu-konqueror-shortcuts but it is not going to be installed
E: Broken packages

```

And as I said, I can't even shut down my computer for the night, since I have no file browsing, and I also believe kdm was removed, and will not come back up on the next boot. 

Anybody run into similar problems? Or could offer a solution?

---

### Post by jnylen on 2008-01-13
Ouch.  I can think of 2 things you might want to try:

[LIST]
[*]sudo apt-get -f install
[*]download the .deb files individually (the ones kubuntu-desktop depends on) and install them with sudo dpkg -i (you can get them from packages.ubuntu.com)
[/LIST]

---

### Post by kidko on 2008-01-13
[quote="jnylen"][list][*]sudo apt-get -f install
[*]download the .deb files individually (the ones kubuntu-desktop depends on) and install them with sudo dpkg -i (you can get them from packages.ubuntu.com)[/list][/quote]

-f install just gets me the same thing. It's rather strange.

And the individual package thing would mean I download hundreds. For example... kubuntu-desktop needs konqueror, which needs libgcc ( > xx.xx.xx, while that same version is to be installed, and again, -f does nothing).

Would a clean install just work better?

---

### Post by jnylen on 2008-01-13
Or you could try aptitude - supposedly it has better handling of dependencies.  But it may be too late, and yeah, my next step after that would probably be a complete reinstall, as much as that sucks.

---

