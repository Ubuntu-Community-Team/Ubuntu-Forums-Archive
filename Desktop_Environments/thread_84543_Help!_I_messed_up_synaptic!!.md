---
title: "Help! I messed up synaptic!!"
date: 2005-10-31
forum: Desktop Environments
---

### Post by kreso on 2005-10-31
I tried to install a modem driver in .deb format via sudo dpkg -i, and the installation didn't finish.

now I can't see any packages in synaptic! It says it cannot access cache or something.
When synaptic starts it reports one broken package.

dpkg list returns the correct list of packages though.

I tried removing the package with dpkg -r but it tells me to reinstall the apllication before trying to remove it.

any ideas? I don't care how drastic :)

---

### Post by jdwannam on 2005-10-31
There should be an option with dpkg to force remove the package.  (edit:  it's --force)  Also, if either the package manager / installer terminated impromperly there might be some left over lock files that need to be removed.  Try running aptitude from the terminal and see if it gives you a lock file error.  If not then don't delete anything!   ;) 

Best of Luck,

J.D.

---

### Post by kreso on 2005-10-31
well I solved the problem (kinda). I sudo gedit-ed the file in /usr/lib/dpkg or somewhere like that, and removed the entry where it said my installed package was corrupt.

It's not a fix, but hey, synaptic works fine now and no apt-get problems.

---

### Post by Efwis on 2005-10-31
another thing you could have done, since your synaptic was reporting a broken error, was go to synaptic, click on custom, in the left window it shows broken, then all you woul dhave to do is click on broken, then click on the file that it showed, synaptic would have removed th program in question.

---

### Post by bryan986 on 2005-10-31
There is even a better solutin in synaptic "edit->fix broken packages"

---

### Post by kreso on 2005-11-02
well yeah, but synaptic didnt show any packages, so it couldnt find the broken ones :)

---

### Post by Efwis on 2005-11-02
[QUOTE=kreso]well yeah, but synaptic didnt show any packages, so it couldnt find the broken ones :)[/QUOTE]
well thats a penguin of a different color then :)

---

