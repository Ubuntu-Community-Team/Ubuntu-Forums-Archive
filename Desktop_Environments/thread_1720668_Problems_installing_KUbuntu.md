---
title: "Problems installing KUbuntu"
date: 2011-04-03
forum: Desktop Environments
---

### Post by LinuxPhreak on 2011-04-03
I have Ubuntu 10.10 and I decided to install KUbuntu as well. I replaced the GDM with the KDM. So I then restarted my computer and tried to log into the KUbuntu. When I did this I got terminal window and nothing else. When I exited the Terminal I got brought back to the KDM. 

When I login to the Gnome section of my Ubuntu install I have no problems even though I'm using the KDM. 

Additional info that may be needed. 

Dell Inspiron 8500
Restricted NVIDIA Graphics driver installed

---

### Post by kio_http on 2011-04-03
Would it be possible for you do describe the terminal window?

Also did you install the default kde from kubuntu-desktop or use the ppa version of kde?

Can you launch kde applications from GNOME (e.g dolphin)?

Maybe [upgrading to a newer version of kde]("http://www.kubuntu.org/news/kde-sc-4.6.1") would help.

---

### Post by techunit on 2011-04-03
I think he installed KDM instead of the Kubuntu desktop. KDM isn't going to install the GUI. In that terminal can you run
```
sudo apt-get update
```

if so try installing kubuntu-desktop

---

### Post by kio_http on 2011-04-04
> **techunit said:**
> I think he installed KDM instead of the Kubuntu desktop. KDM isn't going to install the GUI. In that terminal can you run
```
sudo apt-get update
```

if so try installing kubuntu-desktop

No, actually I think he is referring to the prompt to chose between KDM or GDM when installing kubuntu-desktop.

---

