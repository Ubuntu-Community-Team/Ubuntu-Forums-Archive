---
title: "lightdm not working and systems messed up"
date: 2011-10-17
forum: Desktop Environments
---

### Post by lucacerone on 2011-10-17
Dear all,
I messed up my computer and I think I uninstalled some important
package.
Now everytime I start up the graphical shell hangs
and I have to manually launch
sudo /etc/init.d/gdm restart
from a different shell.
After that if I try to start lightdm
or if I try to login in a Ubuntu (Unity) session
the launcher don't appear and the windows are broken.
I don't know why but I think that the kde-windows manager is used
instead of compiz/lightdm etc...

Can you please help me to restore my computer to a working state?
I have a lot of important stuffs on it and it would be a mess to
have to reinstall everything from scratch!

Thanks a lot in advance for your help,
Cheers, -Luca

---

### Post by ymzn on 2011-10-23
try this 

sudo dpkg-reconfigure lightdm
[URL="https://wiki.ubuntu.com/LightDM"]
https://wiki.ubuntu.com/LightDM[/URL]

---

### Post by lucacerone on 2011-10-23
Thanks Ymzn.
Maybe you can help me: on askubuntu ([http://askubuntu.com/questions/70572/reset-unity-and-gnome-to-default-values/70617#70617](http://askubuntu.com/questions/70572/reset-unity-and-gnome-to-default-values/70617#70617)) I've been suggested to use:
```
sudo apt-get -o DPkg::options::=--force-confnew --reinstall install <package>

```
The problem is I don't know which are the packages that would need such a solution.
Can you help me?
Thanks a lot again!

---

### Post by pt123 on 2011-10-26
```
sudo apt-get -o DPkg::options::=--force-confnew --reinstall install <package>
```
in this  case the package is lightdm

so you get this
```
sudo apt-get -o DPkg::options::=--force-confnew --reinstall install lightdm
```


but I have tried this and it doesn't get lightdm to start

---

