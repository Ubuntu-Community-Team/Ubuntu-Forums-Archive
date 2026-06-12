---
title: "Alternate routing of default installation path"
date: 2009-04-07
forum: General Help
---

### Post by kvk on 2009-04-07
Normally when installing from the package manager, things are routed into the /usr/share directory. I need to change this to the /home/arctos directory ( ~/ ) to install there, since I didn't want to just drag installed applications over from the /usr/share directory. HOw do I set that directory path?

Thank you!

---

### Post by mb_webguy on 2009-04-07
First, programs are *not* installed to the /usr/share directory.  They're installed to the /usr directory, with executables in the /usr/bin directory and data files in the /usr/share directory.

Since you're a bit fuzzy on this point, I'm wondering about the wisdom in trying to change it.  Why would you want to do this?  If you want to install software so that only a certain user or group of users can use it... well, that's what user and group permissions are for.  Simply change the ownership or permissions of the executable so that only the one user or group can execute it.

I can't think of any other good reason to change the installation directory.  Software is installed to certain directories in certain ways for a reason.  Changing things without knowing why things are the way they are, and why your reason for changing them is more important, is a Very Bad Thing.  Trying to do so almost certainly break your installation.

---

### Post by kvk on 2009-04-07
Thanks for the correction; my bad.

The reason I'm interested in changing it:

I'm running a non-linear modeling application inside Emacs. The application is installed in the ~/ directory, while Emacs was installed into the /usr directories. The ~/.emacs file and the usr/share/emacs/22.2/lisp/admb/admb.el library define the interaction between the two and run a series of customized key bindings for the modeling software in addition to some interfaces with R and other applications. The fact that one is in the local directory and the other is in the /usr directory has created some problems with the Lisp commands. Placing them in the same directory should resolve these, or at least remove one level of difficulty.

I'm the only one who uses the machine, so I'm not trying to limit permissions.

---

### Post by mb_webguy on 2009-04-07
In that case, there's no reason to actually change the installation location.  Just create one or more symlinks in your home directory to the installation directory, with "ln -s */path/to/target* *linkname*".

---

### Post by kvk on 2009-04-08
Hmmm...I'll see if that works! Thanks!

---

