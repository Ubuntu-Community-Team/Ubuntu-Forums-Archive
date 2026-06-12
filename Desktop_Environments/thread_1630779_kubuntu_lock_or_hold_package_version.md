---
title: "kubuntu lock or hold package version"
date: 2010-11-25
forum: Desktop Environments
---

### Post by SalsaDoom on 2010-11-25
Hi fellas,

Having trouble figuring this out. I've got a package that I've installed from out-of-repos and Kubuntu feels the need to "upgrade" this package to a version that I do not want to use. I've found out how to do this in **U**buntu, but not in **K**ubuntu. A commandline solution would be fine, although I've googled it and not come up with any working results. 

TIA :)

---

### Post by ajgreeny on 2010-11-25
To pin a package version add these lines to  /etc/apt/preferences:
```
Package: name                
Pin: version (number from repos, you can find this in synaptic for version already installed)    
Pin-Priority: 1001
```It will not matter if it is Ubuntu, Kubuntu, Xubuntu, Lubuntu, or any of the other *ubuntu family, they should all have the ability to pin a package this way.

---

### Post by SalsaDoom on 2010-11-25
Ah, yes. Right-o. Thats what I was looking for. Thanks a bunch :D

---

