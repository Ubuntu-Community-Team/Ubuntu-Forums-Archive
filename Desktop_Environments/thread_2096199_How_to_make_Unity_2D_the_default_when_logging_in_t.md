---
title: "How to make Unity 2D the default when logging in to Ubuntu."
date: 2012-12-19
forum: Desktop Environments
---

### Post by Confused2570 on 2012-12-19
Hi, i have a laptop I want to install Ubuntu on but since it's old it doesn't have a graphics card (just your standard integrated one) so I wanted to know how to make Unity 2D the default desktop. Thanks!
 
EDIT: For Ubuntu 12.04.1

---

### Post by zombifier25 on 2012-12-19
On the log in screen, click the little Ubuntu logo on your username, choose "Ubuntu 2D" on the list.

If you want to make it default for ALL users, then modify /etc/lightdm/lightdm.conf . The command will launch Gedit as root to edit it:
```
gksu gedit /etc/lightdm/lightdm.conf
```
Find this line:
```
user-session=ubuntu
```
and change it to:
```
user-session=ubuntu-2d
```

---

### Post by grahammechanical on 2012-12-19
If your graphics adapter is not capable of running Ubuntu Unity (3~D) then the install process will automatically install Ubuntu 2D and that will be the default login option. If it turns out that your adapter is capable but you think the machine will work better with Unity 2D. You may find that 2D has not been installed. You can install it in 12.04 through the Software Centre.

Things are a little different for 12.10 onwards. As Unity 2D is not used in 12.10 there is another method of getting the Unity 3D effect on hardware with lower specification. This also is done automatically during the installation process.

Regards.

---

### Post by Confused2570 on 2012-12-20
Thanks zombifier, it works!

---

