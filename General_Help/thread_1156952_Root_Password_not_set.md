---
title: "Root Password not set?"
date: 2009-05-12
forum: General Help
---

### Post by YankeeFan on 2009-05-12
Cheers all,
I've installed Ubuntu 9.04 on my Dell desktop. It is a dual boot with Windows XP.  It had XP on it and I installed the Ubuntu yesterday.

I'm trying to unzip a RPM file and to do that I had to install something else and to do that I had to install something else, sigh!  Somewhere along the installs, I had to switch to the root user and give the root password.  

I never set up root password during the Ubuntu install.  I was asked to set up username and password, but not a root.  

For the root password, I tried to use the password I used during the install.  It doesn't work.

What do I do?

Thanks for any help.

---

### Post by snowpine on 2009-05-12
1. Ubuntu does not use a root password. You should use the command 'sudo' to temporarily give yourself root privileges. See here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

2. RPM packages are used by red had based distros like Fedora; the package you are trying to install will not work in Ubuntu. Look for Ubuntu-specific instructions for whatever you're trying to do. :)

---

