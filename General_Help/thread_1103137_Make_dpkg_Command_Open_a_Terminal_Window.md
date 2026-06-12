---
title: "Make dpkg Command Open a Terminal Window"
date: 2009-03-22
forum: General Help
---

### Post by Mark76 on 2009-03-22
What would I need to put in the shell command box to do that?

---

### Post by Rocket2DMn on 2009-03-22
Try:
```
gnome-terminal -e 'sudo dpkg -i "$@"'
```
The terminal will close as soon as the commands are finished.

---

### Post by Mark76 on 2009-03-22
That worked (after I took out the 's). Thanks :)

---

### Post by Mark76 on 2009-03-22
Just thought.

Is there a way to get it to automatically install dependencies as well?

---

### Post by Rocket2DMn on 2009-03-22
If you are installing .deb packages that are not from the repositories, then I think if you have any dependencies in .deb format, just place them in the same directory as the .deb you are trying to install.  If the .deb you are trying to install hasn't declared its dependencies, then you are out of luck.

---

### Post by Mark76 on 2009-03-22
What about dependencies that are already in the repositories?

---

### Post by Rocket2DMn on 2009-03-22
If you are installing a package from the repos using one of Ubuntu's package managers, it will get all dependencies automatically.  If you are installing a .deb manually (as in not direct from the repos) then I think you need to install the dependencies yourself using a package manager.  I suggest installing anything you can from the repos since the package will get upgraded for you automatically when there are updates, however we know this is not always possible.

---

