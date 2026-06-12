---
title: "Uninstalling Python 2.6 without trashing everything"
date: 2009-04-15
forum: General Help
---

### Post by Skofo on 2009-04-15
Hey guys, I want to remove Python 2.6 from my computer, or at least change the default python to 2.5. When I try to remove Python 2.6 through the package manager, it asks me if I want to remove about 200 other things, which I don't want to do. Things that only support Python 2.5 (like Panda3D and Google App Engine) try to use python 2.6 instead of python 2.5 by default, which screws things up. How do I fix this?

---

### Post by kennyrogersjr on 2009-05-07
bump

I'm having the same issue. I upgraded to 9.04 and have python 2.6. I see that 2.5 and 2.4 are installed, yet I don't know how to deactivate/unregister 2.6. Obviously uninstalling won't happen, especially since so many apps are dependent on the newer version. However, there should be a way to configure python or the system to use a latter version in specific cases or all the time.

Take care.

Ken

---

### Post by kennyrogersjr on 2009-05-08
bump

---

### Post by kennyrogersjr on 2009-05-08
bump

---

### Post by kennyrogersjr on 2009-05-08
bump

---

### Post by Yellow Pasque on 2009-05-08
Don't uninstall Python 2.6. You can have multiple versions of Python. I'm sure there's a more elegant way to do it (maybe using alternatives?), but the dirty workaround would be to manipulate the /usr/bin/python link
EDIT: This could bork your system, so tread lightly
EDIT2: IIRC, the staff of this forum ask that you don't bump more than once a day

---

### Post by zipho on 2009-08-11
Bump

---

### Post by nikhilk on 2009-08-11
See if you can install the python 2.5 package directly via dpkg to a different location using --instdir option of dpkg.
I am not sure but the command would be something like dpkg -i <package> --instdir /mylocation

---

### Post by NoBugs! on 2009-08-12
Did you try replacing "python filename.py" with "python2.5 filename.py"?
To change system-wide, you could try running:
```
sudo nautilus
```
Then go to /usr/bin, you'll notice "python" is a link to "python2.6".
You could probably delete that link, then right click python2.5, make link, and rename it "python".

---

