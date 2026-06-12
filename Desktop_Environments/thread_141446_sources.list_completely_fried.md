---
title: "sources.list completely fried"
date: 2006-03-08
forum: Desktop Environments
---

### Post by mmcclure79 on 2006-03-08
I've been searching and searching for a good working sources.list file because mine is completely wasted. I think the repositories Automatix uses roasted the file. I have tried several ones I have found including the one at psychocats and the automatic generator. I have followed all the steps at psychocats and still no working list.

this is my output from sudo apt-get update:
```
Err http://security.ubuntu.com breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Ign http://security.ubuntu.com breezy-security Release
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/main Sources
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://security.ubuntu.com breezy-security/multiverse Packages
Ign http://security.ubuntu.com breezy-security/universe Sources
Ign http://security.ubuntu.com breezy-security/multiverse Sources
Err http://security.ubuntu.com breezy-security/main Packages
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/main Sources
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/restricted Sources
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/universe Packages
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/multiverse Packages
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/universe Sources
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://security.ubuntu.com breezy-security/multiverse Sources
  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Ign http://us.archive.ubuntu.com breezy Release
Ign http://us.archive.ubuntu.com breezy-updates Release
Ign http://us.archive.ubuntu.com breezy/main Packages
Ign http://us.archive.ubuntu.com breezy/restricted Packages
Ign http://us.archive.ubuntu.com breezy/main Sources
Ign http://us.archive.ubuntu.com breezy/restricted Sources
Ign http://us.archive.ubuntu.com breezy/universe Packages
Ign http://us.archive.ubuntu.com breezy/multiverse Packages
Ign http://us.archive.ubuntu.com breezy/universe Sources
Ign http://us.archive.ubuntu.com breezy/multiverse Sources
Ign http://us.archive.ubuntu.com breezy-updates/main Packages
Ign http://us.archive.ubuntu.com breezy-updates/restricted Packages
Ign http://us.archive.ubuntu.com breezy-updates/main Sources
Ign http://us.archive.ubuntu.com breezy-updates/restricted Sources
Ign http://us.archive.ubuntu.com breezy-updates/universe Packages
Ign http://us.archive.ubuntu.com breezy-updates/multiverse Packages
Ign http://us.archive.ubuntu.com breezy-updates/universe Sources
Ign http://us.archive.ubuntu.com breezy-updates/multiverse Sources
Err http://us.archive.ubuntu.com breezy/main Packages
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy/restricted Packages
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy/main Sources
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy/restricted Sources
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy/universe Packages
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy/multiverse Packages
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy/universe Sources
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy/multiverse Sources
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy-updates/main Packages
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy-updates/restricted Packages
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy-updates/main Sources
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy-updates/restricted Sources
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy-updates/universe Packages
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy-updates/multiverse Packages
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy-updates/universe Sources
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Err http://us.archive.ubuntu.com breezy-updates/multiverse Sources
  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/source/Sources.gz  Could not connect to security.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/source/Sources.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/source/Sources.gz  Could not connect to us.archive.ubuntu.com:80 (127.255.102.184). - connect (111 Connection refused)
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

and here's my sources.list file:
```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

```

Any suggestions from anyone?

---

### Post by adamkane on 2006-03-08
Sorry for not being very helpful. Maybe security.ubuntu.com is down? Possibly a connectivity problem.

---

### Post by Lord Illidan on 2006-03-08
It could be a problem with your dns.

Re: sources.list, remove all instances of us from archive.ubuntu.com

---

### Post by mmcclure79 on 2006-03-09
well I took out the us. references in the file still no go. I have no problem with surfing the internet, so I'm not understanding how it could be my dns.

---

### Post by adamkane on 2006-03-09
I used your sources.list, and didn't have any errors. Connection refused is usually a firewall/router issue. How are you connected to the internet?

---

### Post by mmcclure79 on 2006-03-09
I'm connected the same way I have been for almost a year now. I have a router hooked up to DSL with a static ip. I never had a problem before with my router's configuration. Perhaps I should try connecting directly to the DSL modem instead of going via wireless.

---

### Post by mmcclure79 on 2006-03-21
Update:

I took it to work and using their connection and DNS was able to connect ot he repositories just fine with no problems. Guess I'll be giving the help desk a call over at my ISP and letting them know that their DNS is junked up and if they could fix it so I can get to the repositories. If they don't I'll swipe my wifes badge and beat them repeatedly at their desk...

---

### Post by mmcclure79 on 2006-03-28
I ran apt-get update with two different sets of DNS servers. and still the same issue. It was mentined that "Connection Refused: error 111" was a router config problem. Now I'll be the first to admit that I Was cheap and bought the biggest piece of crap on the market. Does anyone know what config this may be referring to? Or does anyone have any other other suggestions?

---

### Post by jclose on 2006-05-04
I am having the same kinds of problems with connecting to their servers.  I found some other mirrors (see [https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive) for a list) and tried those.  I am some good luck but still a lot of connection refused errors from the new mirror, too.

I am trying to connect in a large coporate environment (behind a firewall of totally unknown configuration).  Unfortunately I can't change the settings of it (or even look at them).  :)

JC

---

