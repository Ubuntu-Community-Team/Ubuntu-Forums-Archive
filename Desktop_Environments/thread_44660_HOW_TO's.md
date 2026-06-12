---
title: "HOW TO's"
date: 2005-06-27
forum: Desktop Environments
---

### Post by mokong on 2005-06-27
im trying to install a new program,the i got this error how do i fix this

checking for rpm... /usr/bin/rpm
checking for dot... no
checking whether ln -s works... yes
checking for esd-config... no
checking for ESD - version >= 0.2.7... no
*** The esd-config script installed by ESD could not be found
*** If ESD was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the ESD_CONFIG environment variable to the
*** full path to esd-config.
checking for pkg-config... /usr/local/bin/pkg-config
checking for GLIB - version >= 2.4.0...
*** 'pkg-config --modversion glib-2.0' returned 2.6.5, but GLIB (2.6.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: *** GLIB >= 2.4.0 not installed! ***
 :roll:  :roll: 

im a total virgin in linux so pls help ](*,)

---

### Post by mokong on 2005-06-27
forgot to say 

i have already installed the GLIB/ what i got is GLIB 2.5.xxxx
and the pkg-config/ snd i keep getting this 

guess its saying something about a path / which i dont know how to configure

is there away to automatically just install or update those lib/ using apt-get or something/

ty

---

### Post by wdso on 2005-06-27
What program are you trying to compile? Why don't you use apt-get? Its faster and more reliable, you get updates with apt-get dist-upgrade and so on.

 If you insist on building the package yourself, check out apt-build or checkinstall.

---

