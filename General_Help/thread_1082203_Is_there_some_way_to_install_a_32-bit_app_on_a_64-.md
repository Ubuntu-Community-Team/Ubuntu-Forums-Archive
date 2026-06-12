---
title: "Is there some way to install a 32-bit app on a 64-bit OS"
date: 2009-02-27
forum: General Help
---

### Post by beattyml1 on 2009-02-27
Is there some package/library/app etc. that will allow me to install a 32-bit program like skype on my 64-bit ubuntu OS

---

### Post by taurus on 2009-02-27
You need to install the ia32-lib package first if you want to run some 32bit apps on your x86_64.

---

### Post by sisco311 on 2009-02-27
[uhelp]community/Skype#AMD64[/uhelp]

or enable the medibuntu repositories and install skype from Add/Remove... or Synaptic.
[uhelp]community/Medibuntu[/uhelp]

---

### Post by Yellow Pasque on 2009-02-27
A 32-bit program will need 32-bit shared libraries. Some of the basic 32-bit libs are offered in the Debian/Ubuntu repos as lib32 packages (ia32-libs depends on the most commonly used of these packages).

If you need other shared libs not offered in the repos, you can use getlibs: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

