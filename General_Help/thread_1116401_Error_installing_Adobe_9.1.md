---
title: "Error installing Adobe 9.1"
date: 2009-04-04
forum: General Help
---

### Post by dixiegent on 2009-04-04
Hello, I am new to linux and Ubuntu. I was trying to install Adobe 9.1 and after downloading I received the following error message. What does it mean and how do I correct the problem so I can install it? Thanks.

/tmp/AdbeRdr9.1.0-1_i386linux_enu-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

---

### Post by taurus on 2009-04-04
What if you install it from a terminal?

Applications -> Accessories -> Terminal
```
sudo dpkg -i /tmp/AdbeRdr9.1.0-1_i386linux_enu-1.deb
```

---

### Post by 73ckn797 on 2009-04-04
> **dixiegent said:**
> Hello, I am new to linux and Ubuntu. I was trying to install Adobe 9.1 and after downloading I received the following error message. What does it mean and how do I correct the problem so I can install it? Thanks.

/tmp/AdbeRdr9.1.0-1_i386linux_enu-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

Adobe Acroread is available via Synaptic. You will have to enable the "medibuntu" repositories to have it show up.

Follow the instructions in this link: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) , to add it to your software sources. It will install all necessary dependencies. After adding you will need to go into System/Administration/Synaptic Package Manager and find it listed as "acroread".

---

