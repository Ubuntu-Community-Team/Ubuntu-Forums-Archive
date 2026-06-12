---
title: "Gnome updation"
date: 2012-05-16
forum: Desktop Environments
---

### Post by abhishektrivedi on 2012-05-16
Hi! I installed lubuntu 11.04(LXDE) on my compaq precario (specs:intel p4 processor, 1 GB RAM and 64 MB built-in graphic card) and then updated to Gnome 2 desktop via synaptic package manager. Now I want to update to Gnome 3. How can I do this? (unity and compiz are not working on my system may be due to hardware incompatibility)

---

### Post by zombifier25 on 2012-05-16
Use GNOME 3's PPA
```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get-update

```
Note that the GNOME 3 version for Natty in the PPA is rather old, and may break your system if you decide to upgrade to 11.10.

---

### Post by kc1di on 2012-05-16
Also if I'm not mistaken you have to have Compiz working for Gnome 3 to work. With your hardware it's better to stick to gnome 2 or 3 fallback.

---

