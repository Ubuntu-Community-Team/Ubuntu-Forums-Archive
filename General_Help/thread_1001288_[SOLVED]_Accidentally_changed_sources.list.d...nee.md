---
title: "[SOLVED] Accidentally changed sources.list.d...need help"
date: 2008-12-03
forum: General Help
---

### Post by Anonymous111 on 2008-12-03
I accidentally changed sources.list.d to the wrong thing while trying to install Wine...Now i cant open add/remove or install any other programs....is there anyway to revert the folder back to how it was when i first installed ubuntu or at least delete the file i added (it says permission is denied)?

---

### Post by iaculallad on 2008-12-03
By saying "Accidentally changed sources.list.d" folder, you renamed it? If so you could just do the command below:

```
sudo cp /etc/apt/altered_sources.list.d.folder.name /etc/apt/sources.list.d
```

and do:

```
sudo apt-get update
```

---

### Post by Anonymous111 on 2008-12-03
No, i meant that i added a file that screwed it up and i need help to revert it back to how it was before i added the file.

(and both of those commands dont work for some reason)

---

### Post by sisco311 on 2008-12-03
open the file manager as root and remove the file:
```
gksu nautilus /etc/apt/sources.list.d/
```

please be careful while running applications with root privileges as you may damage your system.

---

### Post by todak on 2008-12-03
Alt+F2 then enter ```
gksu nautilus
``` Then go to the folder and remove the offending file.

---

### Post by iaculallad on 2008-12-03
> **Anonymous111 said:**
> No, i meant that i added a file that screwed it up and i need help to revert it back to how it was before i added the file.

(and both of those commands dont work for some reason)

Yes, the first command won't work unless you have to change the path and folder name as my post only represents an action as I don't know the current folder name of your sources.list.d (As you title implied "Accidentally changed sources.list.d....").

What about doing:

```
sudo cp /etc/apt/sources.list.d/medibuntu.list.save /etc/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get upgrade

```

The file medibuntu.list.save (If it exist) serves as a backup file of your medibuntu.list file.

---

