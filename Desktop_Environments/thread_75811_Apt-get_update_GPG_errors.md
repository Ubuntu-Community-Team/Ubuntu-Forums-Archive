---
title: "Apt-get update GPG errors"
date: 2005-10-14
forum: Desktop Environments
---

### Post by poison on 2005-10-14
Hi

is there a way to update our keys on Breezy so that [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates will work ?

Thanks

---

### Post by bonsiware on 2005-10-14
are you talking about this error message?

```
W: GPG error: http://it.archive.ubuntu.com breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

I don't know the cause of it...

is there anyone else who has the same problem?

---

### Post by ioliver on 2005-10-14
I'm getting exactly the same on a 100% clean Breezy install.
Ian

---

### Post by joelito on 2005-10-14
I think the problem is with so many people flodding the servers, wait a couple days and see

---

### Post by moopere on 2005-10-16
[QUOTE=joelito]I think the problem is with so many people flodding the servers, wait a couple days and see[/QUOTE]

Or, the alternative, suggested by another thread here at UF is to use aptitude or apt-get from the command line with the --allow-unauthenticated switch as in:

apt-get dist-upgrade --allow-unauthenticated

This will still spit out an error at you whenever you do an apt-get update, but it will essentially ignore gpg based error messages....good stuff if you have to get a server up.

Cheers,
Craig

---

### Post by moopere on 2005-10-16
[QUOTE=moopere]Or, the alternative, suggested by another thread here at UF is to use aptitude or apt-get from the command line with the --allow-unauthenticated switch as in:

apt-get dist-upgrade --allow-unauthenticated

This will still spit out an error at you whenever you do an apt-get update, but it will essentially ignore gpg based error messages....good stuff if you have to get a server up.

Cheers,
Craig[/QUOTE]

Oh, and while I'm in a less than charitable mood, why on earth we don't have a sane (re: easy to find) fallback from the gpg package authentication thingy is beyond me.

---

### Post by joshmachine on 2005-10-19
I have posted a bug at:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=18088](https://bugzilla.ubuntu.com/show_bug.cgi?id=18088)

Cheers,
Josh

---

### Post by krisg on 2005-10-19
mine's worse :confused: 

```
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```

---

### Post by ProPilot on 2005-10-19
I am getting the GPG error after a synaptic reload and a terminal sudo apt-get update as well

---

### Post by Ampersand on 2005-10-19
[QUOTE=krisg]mine's worse :confused: 

```
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```[/QUOTE]

There aren't any breezy backports yet. They'll be up in a few months, probably after the Dapper features freeze.

---

### Post by martbd on 2007-02-23
I getting the error when running sudo apt-get update 
W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-updates Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty-backports Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release: Couldn't access keyring: 'No such file or directory'
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release: Couldn't access keyring: 'No such file or directory'

---

