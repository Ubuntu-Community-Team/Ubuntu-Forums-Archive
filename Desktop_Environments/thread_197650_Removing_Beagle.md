---
title: "Removing Beagle"
date: 2006-06-16
forum: Desktop Environments
---

### Post by keplero on 2006-06-16
Hello,
I'm having some problems trying to remove Beagle. I've installed it with Synaptic (package "beagle") and then decided to cancel it. I've removed the "beagle" package with all the configuration (full uninstall) but now when I try to access the search button (Resources->Search) Ubuntu says:

```
Error reading file file://usr/share/applications/beagle-search.desktop: file not found
```

What can I do? :(

---

### Post by Hi-Teck on 2006-07-01
I had the same problem.

1. 1st go into synaptic and search for "gnome-utils" (this is the package that contains gnome-search-tool...the default search tool ubuntu uses).

2. Right click on the package and mark it for a reinstall....click apply...then restart gnome by hit Ctrl Alt Backspace.

When Gnome comes back up the icon "Search" under "Places" will work again. Beagle also leaves an icon is Assessories...do as it as you wish.

---

