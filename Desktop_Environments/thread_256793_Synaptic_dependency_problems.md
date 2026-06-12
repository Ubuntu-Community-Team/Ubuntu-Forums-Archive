---
title: "Synaptic dependency problems"
date: 2006-09-13
forum: Desktop Environments
---

### Post by dcroxton on 2006-09-13
I'm having some problems with packages.  Whenever I install or uninstall something in Synaptic, I get the following errors:

E: gnome-menus: subprocess post-installation script returned error exit status 1
E: gnome-panel: dependency problems - leaving unconfigured
E: gnome-applets: dependency problems - leaving unconfigured
E: python-gtk-1.2: subprocess post-installation script returned error exit status 1
E: iceme: dependency problems - leaving unconfigured
E: icepref: dependency problems - leaving unconfigured

In spite of the errors, no packages show up as "Broken," and I have run "repair broken packages" to no effect.  I haven't noticed any problems with these applications, but the errors concern me, especially as the list of packages showing up in the error list keeps getting longer.  Any ideas?

Sincerely,
Derek

---

### Post by lamego on 2006-09-13
Regarding the "post-installation" errors, look for the files refered to the packages at /var/lib/dpkg/info/ and delete them.

Regarding the "dependency problems" just try to temove those packages.

After this operations just install "ubuntu-desktop" to make ure the packages will get properly reinstalled.

---

### Post by dcroxton on 2006-09-13
Well, what do you know.  It turned out that these packages all use python, and for some reason it was causing a recompile of all site-packages (at least, that's what it looks like to me).  And one sample package for TurboGears was causing problems, which made the whole setup fail.  I just renamed the offending file to $file.bak, and the packages configured correctly.  I am so relieved to have this solved.  Thanks for your help.

Sincerely,
Derek

---

### Post by Kumaresan on 2006-09-13
I did some thing with "Synaptic Package Manager", and I am getting the following error message 

"failed to run /usr/sbin/synaptic as user root:
 Wrong password."

Any ideas how to get around this ?

I was able to load from terminal, using "sudo synaptic" command, however I would like to run in GUI mode.

---

