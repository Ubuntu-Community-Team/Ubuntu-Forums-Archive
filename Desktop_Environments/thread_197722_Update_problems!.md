---
title: "Update problems!"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Aimo on 2006-06-16
When i try to run the update manager i get this message after downloading all the updates and are about to install em all...

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

How do i solve this problem?

- Aimo -

---

### Post by mrvw0169 on 2006-06-16
```
sudo gedit /etc/apt/sources.list
```

and find the lines that start or contain cdrom:// and place a # at the beginning of the line or delete the entire line... Or goto System>Admin>Synaptic>Settings>Repos and uncheck CD Disk options... 

Though, you can ignore those warnings though if the update proceeds to install afterwards...

---

### Post by Aimo on 2006-06-16
Thanks... it worked perfectly....

---

