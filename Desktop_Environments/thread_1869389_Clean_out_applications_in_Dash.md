---
title: "Clean out applications in Dash"
date: 2011-10-25
forum: Desktop Environments
---

### Post by djgrant on 2011-10-25
I have all sorts of crap showing up in my Dash when I search for an application. I get lots of low-res icons with no description beneath them. For example, if I look for "Synaptic" I get one nice looking icon that says "Synaptic" underneath it. But I also get an ugly low-res icon that doesn't have any text below it. I also have a Picasa icon but I don't have Picasa installed.

Where are these stored and how do I get rid of them?

---

### Post by garvinrick4 on 2011-10-25
Can check each one in synaptic to see if installed, if offending remove.
or
install aptitude and see if each installed by aptitude:
```
sudo apt-get install aptitude
``````
aptitude show "package name"
``` (without quotes)
Will show you if installed:

```
sudo dpkg --get-selections > installedsoftware 
```Above will give you a list in alphabetical order of all installed (will be in home)

All installed apps:
```
nautilus /usr/share/applications
```

---

### Post by djgrant on 2011-10-25
> **garvinrick4 said:**
> 
All installed apps:
```
nautilus /usr/share/applications
```

I think this part will be most helpful. Thanks.

---

