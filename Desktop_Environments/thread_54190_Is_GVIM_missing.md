---
title: "Is GVIM missing?"
date: 2005-08-03
forum: Desktop Environments
---

### Post by bumboo on 2005-08-03
Hi,

I just installed Kubuntu 5.04 and really like it.  The one thing that puzzles me however is that I cannot find gvim anywhere.  I can find vim but not gvim.  Does anyone know why this is so and where I can get gvim?

Many thanks,

Bumboo

---

### Post by bumboo on 2005-08-03
An additional update:  If I need to install gvim separately, which is the right
vim package to get (see below for apt-get output)?

 root@darwin:~ # locate gvim
/etc/vim/gvimrc
/usr/share/apps/gvimagepart
/usr/share/apps/gvimagepart/gvimagepart.rc
/usr/share/apps/kappfinder/apps/Editors/gvim.desktop
/usr/share/icons/crystalsvg/16x16/apps/gvim.png
/usr/share/icons/crystalsvg/32x32/apps/gvim.png
/usr/share/icons/crystalsvg/48x48/apps/gvim.png
/usr/share/icons/crystalsvg/64x64/apps/gvim.png
/usr/share/icons/hicolor/48x48/apps/gvim.png
/usr/share/vim/gvimrc
/usr/share/services/gvimagepart.desktop
/usr/lib/kde3/libgvimagepart.so
/usr/lib/kde3/libgvimagepart.la


root@darwin:~ # apt-get install gvim
Reading package lists... Done
Building dependency tree... Done
Package gvim is a virtual package provided by:
  vim-gnome 1:6.3-046+1ubuntu7.1
  vim-tcl 1:6.3-046+1ubuntu7
  vim-python 1:6.3-046+1ubuntu7
  vim-perl 1:6.3-046+1ubuntu7
  vim-lesstif 1:6.3-046+1ubuntu7
  vim-gtk 1:6.3-046+1ubuntu7
You should explicitly select one to install.
E: Package gvim has no installation candidate
root@darwin:~ #

---

### Post by rosslaird on 2005-08-03
If you're using Kubuntu, the correct package is kvim.
Gvim will also work, as will vim-gnome and vim-gtk. I use Gvim myself, though I switch between gnome, kde, and xfce.

Use "sudo apt-cache search" to find kvim. Or just try sudo apt-get install kvim.

---

### Post by bumboo on 2005-08-03
Thanks Ross!

Looks like kvim is gvim wrapped up for KDE.  I just installed and it looks fine.

bumboo.

---

### Post by rosslaird on 2005-08-03
[QUOTE=bumboo]Looks like kvim is gvim wrapped up for KDE. [/QUOTE]

Yup, that's exactly right. Gvim has just been ported.
Take a look at yzis as well:

[http://www.yzis.org/](http://www.yzis.org/)

Glad to be of help.
Cheers.

Ross

---

### Post by bleers on 2005-09-12
Hi,
Is it right that Kvim isn't supported anymore?

Is it possible to use Gvim under KDE?

I just want to use the most regular GUI for vim.

cya.

---

### Post by rosslaird on 2005-09-12
[QUOTE=bleers]Hi,
Is it right that Kvim isn't supported anymore?
[/QUOTE]

You can still get Kvim from various KDE sources through apt.

[QUOTE=bleers]Is it possible to use Gvim under KDE?[/QUOTE]

Yes. Actually, gvim is a more complete vim gui than kvim (it handles fonts better, for example.)

---

### Post by bleers on 2005-09-13
ah.. allright.
Howto get Gvim in my packetmanager (I use Synaptic) for Kubuntu?

---

### Post by rosslaird on 2005-09-13
[QUOTE=bleers]ah.. allright.
Howto get Gvim in my packetmanager (I use Synaptic) for Kubuntu?[/QUOTE]


Well, I don't use Synaptic or Kynaptic or whatver. I use apt, with that you should be able to just do this:

sudo apt-get install gvim

It may ask you to specify one (I seem to recall there are various options), and if so, you should choose vim-gnome. Or, I guess you could just try:

sudo apt-get install vim-gnome

Good luck.

Ross

---

### Post by matthias_k on 2005-09-20
[QUOTE=rosslaird]Well, I don't use Synaptic or Kynaptic or whatver. I use apt, with that you should be able to just do this:

sudo apt-get install gvim

It may ask you to specify one (I seem to recall there are various options), and if so, you should choose vim-gnome. Or, I guess you could just try:

sudo apt-get install vim-gnome

Good luck.

Ross[/QUOTE]
 gvim is a virtual package, it's just the name of the executable; Synaptic's search won't yield any results when searching for 'gvim' (at least not with the default config).

The name of the package is 'vim-gnome'.

---

### Post by caspian on 2005-10-06
I tried to run "apt-get install gvim" and I get a bunch of error messages:

Is there something wrong with my apt-get databases? (I tried to run "apt-get update," but I got some error message about failed database downloads)

Below is the error messages I get when I run "apt-get gvim". Thanks t anyone who can help!
> Reading package lists... Done
Building dependency tree... Done
Package gvim is a virtual package provided by:
  vim-gnome 1:6.3-046+1ubuntu7.1
  vim-tcl 1:6.3-046+1ubuntu7
  vim-python 1:6.3-046+1ubuntu7
  vim-perl 1:6.3-046+1ubuntu7
  vim-lesstif 1:6.3-046+1ubuntu7
  vim-gtk 1:6.3-046+1ubuntu7
You should explicitly select one to install.
W: Couldn't stat source package list [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) warty/java Packages (/var/lib/apt/lists/ubuntu.tower-net.de_ubuntu_dists_warty_java_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) hoary-backports/main Packages (/var/lib/apt/lists/public.planetmirror.com_pub_ubuntu-backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) hoary-backports/universe Packages (/var/lib/apt/lists/public.planetmirror.com_pub_ubuntu-backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) hoary-backports/multiverse Packages (/var/lib/apt/lists/public.planetmirror.com_pub_ubuntu-backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) hoary-backports/restricted Packages (/var/lib/apt/lists/public.planetmirror.com_pub_ubuntu-backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package gvim has no installation candidate




---

### Post by matthias_k on 2005-10-06
Sorry, but read what was said, and read the error message closely:
> **Package gvim is a virtual package** provided by:
vim-gnome 1:6.3-046+1ubuntu7.1
vim-tcl 1:6.3-046+1ubuntu7
vim-python 1:6.3-046+1ubuntu7
vim-perl 1:6.3-046+1ubuntu7
vim-lesstif 1:6.3-046+1ubuntu7
vim-gtk 1:6.3-046+1ubuntu7
**You should explicitly select one to install.**

There is no real package called 'gvim', it's a virtual package. You have to install one of those listed above.

---

### Post by caspian on 2005-10-06
:oops:

oops.


Ok, it's vim-gnome that I want. I ran "apt-get install vim-gnome" and I got an error message saying that I'm using the unstable distro and this package hasn't been created yet for my distro. This may be because I'm using the Breezy Badger preview release -- but does this mean that I can't get Gvim until the Breezy Badger stable release?

---

### Post by matthias_k on 2005-10-07
Yes, this is very possible, since Breezy comes with a new version of Gtk+ and thus all packages with Gtk+ dependencies have to be rebuilt. I'd rather wait another week and install breezy final.

---

