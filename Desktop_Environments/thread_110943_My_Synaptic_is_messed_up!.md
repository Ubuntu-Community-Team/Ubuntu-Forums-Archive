---
title: "My Synaptic is messed up!"
date: 2006-01-01
forum: Desktop Environments
---

### Post by Zonkle on 2006-01-01
Hi ;),

I added the new sources to the source list as ppl suggested here to enable the universe and multiverse stuff (I dunno what does it mean:???:), then after I do update the new lists shows up and I can download ..... but after I close Synaptic and open it I get error saying I have the following errors:
```

W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://dk.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://download.skype.com stable/non-free Packages (/var/lib/apt/lists/download.skype.com_linux_repos_debian_dists_stable_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://wine.sourceforge.net binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://de.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://de.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://de.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://de.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://people.ubuntu.com ./ Packages (/var/lib/apt/lists/people.ubuntu.com_%7edoko_OOo2_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://deb.opera.com etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)

```

Then I have to do update again so I can see the new lists .... but they get lost again after I restart Synaptic.

What is wrong ?

This is my sources list:

```

deb http://dk.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu breezy universe
deb-src http://dk.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

## Multiverse
deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

## Wine
deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/

## Penguin Liberation Front
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## Backports
deb http://de.archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted
deb-src http://de.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#deb http://ubuntu-backports.mirrormax.net/ breezy-backports-staging main universe multiverse restricted

#backports-extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ breezy-extras-staging main universe multiverse restricted

# Open Office 2 final
deb http://people.ubuntu.com/~doko/OOo2 ./

# Opera web browser
deb http://deb.opera.com/opera/ etch non-free


```

Is there like a place to get the latest sources.list ? Or I shouldn't just add everything ?

Thanks.

---

### Post by bullfrog on 2006-01-01
try [http://psychocats.net/linux/sources.php](http://psychocats.net/linux/sources.php)    hope this helps  cant help you as im new to unbuntu  also    bulldog

---

### Post by Zonkle on 2006-01-14
Guys this looks not a normal error :???:  could you help me please?

After I reload the packages, everything looks nice .... but after closing and opening Synaptic (not a defined number, but not from the first time!) I get the error in the attached image and then I only see the installed packages.

Why is that happening??

---

### Post by souteneur3190 on 2006-01-14
press the reload button (in synaptic) and errors shoulld leave

---

### Post by Zonkle on 2006-01-15
They do go away, but the problem is that they come back when I close and open Synaptic !!

---

