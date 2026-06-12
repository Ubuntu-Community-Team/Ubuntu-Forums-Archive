---
title: "Binaries not running on 8.1 x64"
date: 2009-01-29
forum: General Help
---

### Post by agarzon on 2009-01-29
I have just installed ubuntu 8.10 amd64 on a Dell Workstation T7000

The binaries that I run on DebianEtch(64), SuSE10(64), and Ubuntu7.04 are not running on Ubuntu 8.10 x64

I have made sure the files are on the binary path, and also have tried running them as ./app but with no luck

The files are executable and I made sure that everyone could execute them.

The error message is this

bash: ./app: No such file or directory

Which is really frustrating considering the file IS on the directory.

Any idea what may be going on? 

What is the obvious thing I have not seen?

---

### Post by jerome1232 on 2009-01-29
My guess is your missing a library somewhere, I would try and run getlibs on it to pull in any needed libraries [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by agarzon on 2009-01-29
jerome,

Thanks, you got it right.

I installed the ia32 package from synaptic and got the binary to respond.

Thanks

---

