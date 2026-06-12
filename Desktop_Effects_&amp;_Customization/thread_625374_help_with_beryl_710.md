---
title: "help with beryl 710"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by Jammer429 on 2007-11-27
I am having trouble installing beryl I tried to apt-get it but it says broken package is there another way to get it all help would be great

---

### Post by FuturePilot on 2007-11-27
What is the exact error? You may have another problem that will need to be fixed first.
Beryl is no longer developed. 7.10 comes with most of Compiz Fusion already installed.

---

### Post by Jammer429 on 2007-11-27
this is what is says
 sudo apt-get install beryl
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
  beryl: Depends: beryl-settings but it is not going to be installed
E: Broken packages

---

### Post by -grubby on 2007-11-27
there is no need to install Beryl because it is no longer developed. I would recommend Compiz-Fusion . To get the "extra" features of Compiz-Fusion I would recommend you install this:

```
sudo apt-get install compizconfig-settings-manager
```

and you can find it under system>preferences>advanced desktop effect settings

---

