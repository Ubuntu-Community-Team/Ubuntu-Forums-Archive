---
title: "beryl 0.2.1 universe broken?"
date: 2007-03-24
forum: Desktop Effects &amp; Customization
---

### Post by mthaddon on 2007-03-24
Tried to install beryl from the universe repo in feisty (just saw the announcement about it making the repos) and I got this:

```
sudo aptitude install beryl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  beryl beryl-settings 
The following NEW packages will be automatically installed:
  beryl-core beryl-manager libberylsettings0 
The following NEW packages will be installed:
  beryl-core beryl-manager libberylsettings0 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 208kB/591kB of archives. After unpacking 3748kB will be used.
The following packages have unmet dependencies:
  beryl-settings: Depends: beryl-plugins (>= 0.1) which is a virtual package.
                  Depends: beryl-settings-bindings which is a virtual package.
  beryl: Depends: beryl-plugins which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
beryl [Not Installed]
beryl-settings [Not Installed]

Score is -9992

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

Anyone else having that problem?

Thanks, Tom

---

### Post by SBFC on 2007-03-24
I too get a complaint about not being able to install beryl-plugins. :(

---

### Post by MeneK on 2007-03-25
Same problem here. Also, it seems that beryl-xgl is missing from beryl-core.

---

### Post by xopher on 2007-03-25
This worked fine for me. Updated using update-manager, not aptitude though. Shouldn't matter anyway.

Id just remove Beryl completely, and (re)install it from the feisty repository.

---

### Post by mthaddon on 2007-03-25
Now seems to be working fine for me. I wonder if it was a temporarily thing while it was being rolled out to the mirrors...

---

### Post by SBFC on 2007-03-25
Must have been, I can finally see all packages now after updating.

---

### Post by AtrejuT on 2007-03-26
well I can install from universe just fine, but it doesn't work, i.e. just stops responding after activating beryl... - so the problem with XGL seems to be there still.
I forced the packages back to 0.2.0 for now, anyone know if there'll be a better solution for xgl?

---

### Post by MrJavalava on 2007-03-26
Yeah, have the same problem. XGL is not supported in the 0.21 version. I had to downgrade to make it work (I've locked the version 0.20 aswell). Also because XGL is not supported, my cpu usage was at 100% and I had a choppy performance from the ATI card (eventhough the 3D works).

Though I noted while going through synaptic to find out which files to downgrade, that there is a new plugin for Beryl, which is described as an easier interface for Ubuntu users. Anyone tried it?

It's called 'beryl-ubuntu', there is one for Kubuntu aswell: 'beryl-kubuntu'

---

### Post by AtrejuT on 2007-03-26
No, I haven't seen that before - but I think I'll wait for xgl to work properly from the repos before trying it out...

at least we're not alone ;-)

---

### Post by AtrejuT on 2007-03-27
anyone know if that's been fixed? I just noticed I lost the group plugin by downgrading, and I'd like to have it back ;-)

---

