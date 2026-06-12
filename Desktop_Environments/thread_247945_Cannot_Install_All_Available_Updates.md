---
title: "Cannot Install All Available Updates"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Thund3rstruck on 2006-08-31
Everytime I get a notification of software updates I'm presented with a form that tells me:

Cannot Install All Available Updates:
Totem
checkInstall

I believe this originated from a kernel update. It suggested a few things to do but none has worked. 

Can anyone shed some light on what exactly this message is telling me (besides the obvious fact that synaptic cannot install updates to these packages)

Thx

---

### Post by ayoli on 2006-08-31
I guess it's related to a dependancy problem, ie: a new version of checkinstall is available, but requires a new version of some other package that is not available so the old package is kept until dep could be satisfied.
regards.

---

### Post by Ramses de Norre on 2006-08-31
This might help: ```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by justinflavin on 2006-08-31
> **Ramses de Norre said:**
> This might help: ```
sudo aptitude update && sudo aptitude dist-upgrade
```

i'm having the same problem - but i'm using apt-get instead.

---

### Post by Thund3rstruck on 2006-08-31
I don't know why that never occurred to me before but I think it fixed it as the 2 packages were downgraded and then upgraded. I was only attempting dist-upgrade and that didn't work on its own.

Thanks guys

---

### Post by ayoli on 2006-08-31
> **Ramses de Norre said:**
> This might help: ```
sudo aptitude update && sudo aptitude dist-upgrade
```

right, aptitude does not the same as apt. apt keep checkinstall and not upgrade it, when aptitude remove installwatch to upgrade checkinstall. i was right it's a dep problem :)

---

### Post by justinflavin on 2006-08-31
yeah - aptitude worked - but it had to remove the totem-xine plugin for firefox, before it upgraded totem.

its a dependency problem in the repository.

---

### Post by ayoli on 2006-08-31
that's why sometimes i prefer to wait for next upgrade.
regards.

---

### Post by justinflavin on 2006-08-31
here's the aptitude output when i try to do 
sudo aptitude install totem-xine-firefox-plugin


The following packages are BROKEN:
  totem
The following NEW packages will be automatically installed:
  totem-xine
The following packages will be automatically REMOVED:
  totem-gstreamer
The following NEW packages will be installed:
  totem-xine totem-xine-firefox-plugin
The following packages will be REMOVED:
  totem-gstreamer
0 packages upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 1096kB of archives. After unpacking 2814kB will be used.

The following packages have unmet dependencies:

totem: Depends: totem-gstreamer (>= 1.4.3-0ubuntu1) but it is not installable or totem-xine (>= 1.4.3-0ubuntu1) but 1.4.1-0ubuntu4 is to be installed.

Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
totem [1.4.3-0ubuntu1 (dapper-updates, now) -> 1.4.1-0ubuntu4 (dapper)]

Score is -40

---

