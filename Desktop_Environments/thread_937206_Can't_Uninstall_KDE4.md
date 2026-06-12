---
title: "Can't Uninstall KDE4"
date: 2008-10-03
forum: Desktop Environments
---

### Post by jasper.davidson on 2008-10-03
I decided I wanted to uninstall KDE4 and stick with KDE 3.5.9, but I just can't seem to get rid of KDE4. When I do:
```
dpkg --get-selections | grep kde4
```
It shows everything with kde4 in its name as "deinstall." I have also done:
```
sudo apt-get autoclean
sudo apt-get autoremove

```
Yet my Adept notifier keeps telling me that I need to install the following packages:
```
kde-icons-oxygen
kde4libs-bin
kdebase-data-kde4
kdebase-runtime
kdebase-runtime-bin-kde4
kdebase-runtime-data
kdebase-runtime-data-common
kdebase-workspace-data
kdelibs5
kdelibs5-data
kdepimlibs-data
```
What do I need to remove so that the Adept notifier won't try to install the above KDE4 packages again? Thanks in advance.

---

### Post by sayakb on 2008-10-03
Try:
```
sudo apt-get install kubuntu-kde4-desktop
```

---

### Post by jasper.davidson on 2008-10-03
Thanks, but I think you might have misunderstood me; I'm trying to completely *uninstall* KDE4, not install it. :)

---

### Post by sayakb on 2008-10-04
Sorry :)
```
sudo apt-get purge kde4 kde4-core kubuntu-kde4-desktop
```

---

### Post by jasper.davidson on 2008-10-04
> **LinuxIsInnovation said:**
> Sorry :)
```
sudo apt-get purge kde4 kde4-core kubuntu-kde4-desktop
```
Yes, I've all ready done that, and still my Adept updater wants to reinstall all those KDE4 packages that I listed in my first post. Any idea why?

---

### Post by jasper.davidson on 2008-10-06
*bump*

Any ideas why Adept would want to reinstall those packages from my first post? Thanks in advance.

---

### Post by benerivo on 2008-10-06
I've only briefly used adept, so don't know much about it. The package managers i've used tend to force the installation of packages when they are required rather than asking for them later. But your last post says 'reinstall' and your first post says 'install'. Are those packages you list installed or not? (i only ask as synaptic uses the term 'reinstall' for packages that are currently installed, rather than for packages that were once installed, but no longer so).

I would try```
sudo apt-get purge libqt4*
```which should remove virtually all of kde4. Maybe also trying to purge the packages that you listed for (re)install may help.

---

### Post by jasper.davidson on 2008-10-07
Thanks benerivo, but still no go; Adept still prompts me to install those packages. BTW, the packages are not installed any more, I said "reinstall" only because I had them at one time but manually uninstalled them. 

Is there any way to figure out what dependency is causing Adept to think I need to install those packages?

---

### Post by pbhj on 2008-10-07
I don't think this is possible with adept.

With synaptic you can easily workout what the dependants are. You can probably do it with dselect too.

Load up synaptic (eg Alt-F2, "kdesu synaptic", enter password) and then search for one of the suggested packages. For example kdebase-runtime-bin-kde4 (just search for kdebase in 'name and description'). Click on the dependencies tab in the lower pane and use the dropdown widget to select "dependants" - you'll see below a list of the packages that depend on this package.

A quicker way though would be to look in the packages list pane, right click and choose "Mark For Complete Removal", this then brings up a dialog telling you all the packages that will then be removed, basically this is all stuff that depends on that package.

I'd guess you have maybe got the KDE4 version of something like Gwenview, KDM, Konqueror or whatever installed - such things need a base of packages from KDE4.

You can get similar from "dpkg --simulate --remove kdebase-runtime-bin-kde4" - if you want to actually do it then remove the simulate option and check the man page about recursive and force options. YMMV, I'd use synaptic as it's always clear what will happen and nothing gets done until you click "Apply" then check what will happen and then say "OK".

---

