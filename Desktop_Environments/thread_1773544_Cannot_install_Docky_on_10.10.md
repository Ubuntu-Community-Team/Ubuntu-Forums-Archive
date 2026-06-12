---
title: "Cannot install Docky on 10.10"
date: 2011-06-02
forum: Desktop Environments
---

### Post by Whitsboy on 2011-06-02
Hi All,
When I try to install docky through the synaptic package manager I receive this dialog box saying, 
docky:
 Depends: libgnome-keyring1.0-cil (>=1.0.0) but it is not installable
  Depends: libmono-addins0.2-cil (>=0.6) but 0.4-6 is to be installed
 Recommends: dockmanager but it is not going to be installed

can anyone help. Thanks

---

### Post by Frogs Hair on 2011-06-02
Run these commands in the terminal and report back .
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install docky
```

---

### Post by Whitsboy on 2011-06-03
> **Frogs Hair said:**
> Run these commands in the terminal and report back .
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install docky
```

I have run these commands in the terminal and I get a reply:
 Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 docky : Depends: libgnome-keyring1.0-cil (>= 1.0.0) but it is not installable
         Recommends: dockmanager but it is not going to be installed

---

### Post by Frogs Hair on 2011-06-03
As far as I know Docky is compatible with 10.10 , so I don't know what the problem would be. I can only suggest trying the Docky 10.10 PPA at the link or look into Awn . I used Awn with great success on 10.10 . .[http://www.ubuntugeek.com/how-to-install-docky-in-ubuntu-10-10-maverick.html](http://www.ubuntugeek.com/how-to-install-docky-in-ubuntu-10-10-maverick.html)

---

