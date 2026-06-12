---
title: "Beryl Packages wont install Help"
date: 2007-03-31
forum: Desktop Effects &amp; Customization
---

### Post by phosphorusdeathcamp on 2007-03-31
Ok heres the deal. I am trying to install Beryl on 6.10 but when I type 

sudo apt-get install beryl

I get this 

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
  beryl: Depends: beryl-core but it is not going to be installed
         Depends: libberylsettings0 but it is not going to be installed
         Depends: beryl-plugins but it is not going to be installed
         Depends: beryl-settings but it is not going to be installed
         Depends: emerald but it is not going to be installed or
                  aquamarine but it is not going to be installed or
                  heliodor but it is not going to be installed or
                  yawd but it is not installable or
                  compiz-gnome but it is not going to be installed
E: Broken packages
```

Am I missing some packages or files?

Any help would be appreciated. :(

---

### Post by FuturePilot on 2007-04-01
Maybe try
```
sudo apt-get install beryl emerald-themes
```
And make sure you have all of the necessary repos

---

