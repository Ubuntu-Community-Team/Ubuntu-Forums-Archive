---
title: "Can't install gnome shell"
date: 2012-06-06
forum: Desktop Environments
---

### Post by RooSH23 on 2012-06-06
Hi all,
after performing an update, my ubuntu crashed on every startup.
uninstalling gnome shell solved this problem.
Now I'm trying to install it back but I keep getting errors:

```
sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: gir1.2-clutter-1.0 but it is not going to be installed
               Depends: gir1.2-mutter-3.0 (>= 3.4.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

```
sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libclutter-1.0-0
The following packages will be upgraded:
  orion-gtk-theme
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
E: The package index files are corrupted. No Filename: field for package orion-gtk-theme.
```

I tried to upgrade libclutter-1.0-0 manually, but i got the same error: "E: Unable to correct problems, you have held broken packages."

---

### Post by cortman on 2012-06-06
Have you tried running

```
sudo apt-get -f install
```

?

---

