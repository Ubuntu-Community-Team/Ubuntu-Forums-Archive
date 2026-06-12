---
title: "Error when trying to install nVidia-settings"
date: 2008-05-05
forum: Desktop Environments
---

### Post by TheOhGodOfHangovers on 2008-05-05
When running:

```
sudo apt-get install nvidia-settings
```

I get the following error from the terminal:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-settings is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-settings has no installation candidate
```

I am running 8.04 installed through wubi- I have had the nVidia settings application installed before on a previous install which for various reasons i got rid of. There is no reason i can think of to why it is not working now.

---

### Post by Zorael on 2008-05-05
Nvidia drivers and the settings app are restricted, proprietary software. As such they're not included in the main repositories, since Canonical takes an opt-in stance towards non-free software.

Open up Software Sources (or Synaptics, then File -> Repositories) and make sure you have the **universe** repos enabled. After updating the list of available packages, you should be able to grab nvidia-settings.

---

### Post by TheOhGodOfHangovers on 2008-05-05
Thanks, this seems to have worked perfectly

TOGOH

---

