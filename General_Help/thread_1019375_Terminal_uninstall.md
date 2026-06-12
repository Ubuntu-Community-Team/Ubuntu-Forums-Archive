---
title: "Terminal uninstall"
date: 2008-12-23
forum: General Help
---

### Post by Celestika6 on 2008-12-23
what command do I enter to uninstall limewire 4.18.8 via the terminal?

---

### Post by gettinoriginal on 2008-12-23
sudo dpkg -r package_limewire

---

### Post by cdtech on 2008-12-23
If you installed this from a site then you may want to uninstall using the purge as well:
```
sudo dpkg --remove --purge <package>
```
> Remove an installed package. -r or --remove remove everything except configuration files. This may avoid having to reconfigure the package if it is reinstalled later. (Configuration files are the files listed in the debian/conffiles control  file). -P  or --purge removes everything, including configuration files.(man dpkg)

---

### Post by hyper_ch on 2008-12-23
```

sudo apt-get remove limewire

```
if it's in the repos.

---

