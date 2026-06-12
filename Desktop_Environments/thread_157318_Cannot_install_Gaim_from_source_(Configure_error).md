---
title: "Cannot install Gaim from source (Configure error)"
date: 2006-04-08
forum: Desktop Environments
---

### Post by firecrotch on 2006-04-08
Here is the output that I get when trying to configure Gaim:

```
*** 'pkg-config --modversion glib-2.0' returned 2.10.0, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at http://www.gtk.org/.
```

I have the latest version of GLib installed, yet I get this error, and I have no clue what to do.  Thanks in advance for your help.

---

### Post by dermotti on 2006-04-08
Hmm. do you have package **build-essential** installed?

---

### Post by firecrotch on 2006-04-08
Yes I do.

---

### Post by jklasdf on 2006-04-08
You need the glib development libraries (libglib2.0-dev) in addition to plain glib (libglib2.0-0).

---

### Post by GeneralZod on 2006-04-09
Before trying configure again, do

```

sudo apt-get build-dep gaim

```

It should fetch (almost?) everything you need to compile gaim from source.

---

### Post by firecrotch on 2006-04-10
I tried that, and I get this:
```
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list http://.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Could not open file /var/lib/apt/lists/.archive.ubuntu.com_dists_breezy_universe_source_Sources - open (2 No such file or directory)

```

Running "apt-get update" as it suggests gives me all sorts of problems:

```
Err http://.archive.ubuntu.com breezy Release.gpg
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com breezy-backports Release.gpg
  Could not resolve '.archive.ubuntu.com'
Ign http://.archive.ubuntu.com breezy Release
Ign http://.archive.ubuntu.com breezy-backports Release
Ign http://.archive.ubuntu.com breezy/universe Packages
Ign http://.archive.ubuntu.com breezy/universe Sources
Ign http://.archive.ubuntu.com breezy-backports/main Packages
Ign http://.archive.ubuntu.com breezy-backports/restricted Packages
Ign http://.archive.ubuntu.com breezy-backports/universe Packages
Ign http://.archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://.archive.ubuntu.com breezy-backports/main Sources
Ign http://.archive.ubuntu.com breezy-backports/restricted Sources
Ign http://.archive.ubuntu.com breezy-backports/universe Sources
Ign http://.archive.ubuntu.com breezy-backports/multiverse Sources
Err http://.archive.ubuntu.com breezy/universe Packages
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com breezy/universe Sources
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com breezy-backports/main Packages
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com breezy-backports/restricted Packages
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com breezy-backports/universe Packages
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com breezy-backports/multiverse Packages
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com breezy-backports/main Sources
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com breezy-backports/restricted Sources
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com breezy-backports/universe Sources
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com breezy-backports/multiverse Sources
  Could not resolve '.archive.ubuntu.com'
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://security.ubuntu.com breezy-security Release [27.0kB]
Get:3 http://security.ubuntu.com breezy-security/main Packages [45.7kB]
Get:4 http://security.ubuntu.com breezy-security/restricted Packages [4458B]
Get:5 http://security.ubuntu.com breezy-security/main Sources [14.5kB]
Get:6 http://security.ubuntu.com breezy-security/restricted Sources [960B]
Get:7 http://security.ubuntu.com breezy-security/universe Packages [31.9kB]
Get:8 http://security.ubuntu.com breezy-security/universe Sources [5007B]
Fetched 130kB in 2s (45.4kB/s)
Failed to fetch http://.archive.ubuntu.com/dists/breezy/Release.gpg  Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/dists/breezy-backports/Release.gpg  Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/dists/breezy/universe/binary-i386/Packages.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/dists/breezy/universe/source/Sources.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/dists/breezy-backports/main/binary-i386/Packages.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/dists/breezy-backports/restricted/binary-i386/Packages.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/dists/breezy-backports/universe/binary-i386/Packages.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/dists/breezy-backports/multiverse/binary-i386/Packages.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/dists/breezy-backports/main/source/Sources.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/dists/breezy-backports/restricted/source/Sources.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/dists/breezy-backports/universe/source/Sources.gz  Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/dists/breezy-backports/multiverse/source/Sources.gz  Could not resolve '.archive.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list http://.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/.archive.ubuntu.com_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

It looks to me as if there is an errant "." in the domain name it's searching for, but I can't figure out how to fix that.  Thanks for all of the help.

---

### Post by lowey23 on 2006-04-10
Hi firecrotch

Try this link (courtesy of aysiu)

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

It will tell you how to fix your source.list

You should then be able to get gaim from the repositories using apt-get or synaptic.

Hope this helps.

Cheers

Lowey

---

### Post by firecrotch on 2006-04-10
Thanks a lot - that seemed to do the trick.  If I have any more problems, I'll be back :)

---

