---
title: "How to reset gnome-shell and python3 configuration in Ubuntu 20.04?"
date: 2021-07-20
forum: Desktop Environments
---

### Post by EngineerStrange on 2021-07-20
I am having some auto-update issues after installing some gnome-shell extensions and now I want to reset the configuration of python3 and gnome-shell. How can I do that? Should I remove these packages including configuration files or it'll make it impossible to install those again? (as ubuntu-desktop and many packages will too be removed and become useless until I reinstall python3 and gnome-shell)

The problem which I am having looks like this 
[https://ubuntuforums.org/attachment.php?attachmentid=288837&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=288837&stc=1)

This is not a big problem so far but still it hinders my mood sometimes hence I would prefer to fix it if possible.

---

### Post by ajgreeny on 2021-07-20
I don't use gnome so I can not help you personally.

However gnome users who may be more able to assist will be helped more if you can tell them exactly what you did; what gnome-shell extensions did you install and what else you have done to the system.

---

### Post by EngineerStrange on 2021-07-20
Ok can tell me about python3? You may also tell me how to remove gnome including configuration file.

---

### Post by deadflowr on 2021-07-20
Your error shows nothing to do with python3 or gnome.
Try removing the corrupted file and try updating again.

In a terminal you can run
```
sudo rm /var/lib/apt/lists/ppa.launchpad.net_git-core_ppa_ubuntu_dists_focal_InRelease
sudo apt clean
sudo apt update
sudo apt full-upgrade
```

Alternatively you can rm (remove) all the files in that directory
like so,
```
sudo rm -rf /var/list/apt/lists/*
```
These files get regenerated upon the apt update command.

---

