---
title: "problems with synaptic and installing stuff"
date: 2006-01-10
forum: General Help
---

### Post by neilm on 2006-01-10
I am having a really painful time trying to install software on my system.  Let's use xmms as an example:

I unpack the *tar.gz archive
cd into the relevant directory
$ ./configure

It gives me this:

[INDENT]checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot create executables[/INDENT]

Huh?  What does one have to do to get the c compiler to work?

Not sure if this is related, but when I start up synaptic package manager I get this and other similar warnings:

[INDENT]W: Couldn't stat source package list [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)

[/INDENT]

What does this mean and how can I fix it?

---

### Post by lamego on 2006-01-10
GCC is not installed by default.
About synaptic, do you have the network correctly setup ?
Can you ping za.archive.ubuntu.com ?
Try to hit the RELOAD button on the pacakage manager, it will try to refetch the package list from the network.

There maybe a problem with the server pointed by za.archive.ubuntu.com, if it is the cased edit your apt sources:
sudo gedit /etc/apt/sources.list
replace za. with us.

---

### Post by neilm on 2006-01-10
Thanks, used synaptic to install gcc and some libraries.  Now it's looking for GLIB:

[INDENT]checking for glib-config... no
checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***[/INDENT]

I notice libglib2.0 is installed, so do I need to go and find 1.2.2?

Successfully pinged za.archive.ubuntu.com, but edited /etc/apt/sources.list like you said and tried RELOAD.  Still waiting....

---

### Post by neilm on 2006-01-10
nope, us.archive.ubuntu didn't work either.

---

