---
title: "Wireless out of box"
date: 2008-07-06
forum: Debian
---

### Post by L815 on 2008-07-06
I want to give Debian a good shot, I hear many great things about her. The problem I last time encountered, is there is no wireless support out of the box.

This is an issue for me because I only have wireless access. 

Is there a way I can get wireless support (intel wireless Vaio Laptop) without having to download 1x amount of cds?

---

### Post by p_quarles on 2008-07-06
Yeah. You just need to download the iwlwifi-firmware .deb package and install that. The iwl3945/iwl4965 packages (everything besides the firmware) are in the distributed kernels.

---

### Post by basenvironment on 2008-07-06
> **L815 said:**
> there is no wireless support out of the box.
sure there is.....
:)

---

### Post by L815 on 2008-07-09
Thanks, I have got it working.
Found the deb for my driver (which was not being loaded at boot because of an error)
After installing the firmware with the deb (i put in on a flash drive), wireless is good to go :)

---

