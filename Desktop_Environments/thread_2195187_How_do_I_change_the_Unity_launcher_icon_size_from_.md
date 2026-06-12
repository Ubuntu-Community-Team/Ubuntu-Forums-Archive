---
title: "How do I change the Unity launcher icon size from the command line?"
date: 2013-12-22
forum: Desktop Environments
---

### Post by entropy1 on 2013-12-22
How do I change the Unity launcher icon size from the command line?

---

### Post by steeldriver on 2013-12-22
On Saucy, I was able to do this using dconf e.g. to set the launcher icon size to 64 pixels

```

dconf write /org/compiz/profiles/unity/plugins/unityshell/icon-size 64

```

To reset it to the default value, you can use

```

dconf reset /org/compiz/profiles/unity/plugins/unityshell/icon-size

```


The dconf command line utility is not installed by default - you need to install the dconf-tools package. Usually there is an equivalent command via gsettings however in this case it appears the required schema definition does not exist.

---

### Post by entropy1 on 2013-12-22
Thank you,  steeldriver.  Your solution worked perfectly!

---

