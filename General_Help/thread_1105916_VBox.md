---
title: "VBox"
date: 2009-03-25
forum: General Help
---

### Post by bcbotha on 2009-03-25
how do I uninstall and remove Sun xVM VirtualBox from my pc?

---

### Post by kpkeerthi on 2009-03-25
How did you install it? If you installed it from the repositories/synaptic/add-remove/apt-get/aptitude, choose Applications -> Add/Remove.

---

### Post by 3Miro on 2009-03-25
> **bcbotha said:**
> how do I uninstall and remove Sun xVM VirtualBox from my pc?

There is open source version from the repositories (Add/Remove Programs) and there is the version that you can download from virtualbox.com. Which one do you want.

---

### Post by bcbotha on 2009-03-25
it's version 2.02 that i got from a linux fomat mag. i installed it from the cd.

---

### Post by 3Miro on 2009-03-25
OK, there might be a easier way, but this should work:

in the terminal:

> 
dpkg -S VirtualBox


This would list tings like:
> 
.....
virtualbox-ose: /usr/share/virtualbox/nls/VirtualBox_sk.qm
virtualbox-ose: /usr/share/virtualbox/nls/VirtualBox_pl.qm
virtualbox-ose: /usr/share/virtualbox/nls/VirtualBox_it.qm
.....


So in my case the package is virtualbox-ose, in your case it might be something different. Then you can uninstall it with:

> 
sudo dpkg -r virtualbox-ose


or

> 
sudo dpkg -P virtualbox-ose


I am not sure what the difference between remove and purge is, I guess remove leaves some files behind, but I don't know which files.

---

### Post by bcbotha on 2009-03-25
it doesn't work. the reply i get is 'dpkg - warning: ignoring request to remove vbox which isn't installed'.
if i go to applications - system tools one of my options is Sun xVM VirtualBox? i don't understand?

---

### Post by bcbotha on 2009-03-26
in order to delete it i need to have root permissions. how do i do so?

---

### Post by coffeecat on 2009-03-26
> **bcbotha said:**
> i need to have root permissions. how do i do so?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

