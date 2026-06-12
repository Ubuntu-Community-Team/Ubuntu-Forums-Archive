---
title: "Problem with package manager and update manager!"
date: 2006-06-14
forum: Desktop Environments
---

### Post by BabyBoy on 2006-06-14
Hi when i try and get updates from update manager i get this message:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-static_2.16.1-2ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-static_2.16.1-2ubuntu6.1_i386.deb)
  Could not connect to localhost:80 (127.0.0.1). - connect (111 Connection refused)

This also happens with package manger, Any idea??

It all worked before, but then it just ........... didnt lol

Thanks,

---

### Post by lamego on 2006-06-14
Check your /etc/apt/apt.conf , probably you have configured apt to use localhost as a proxy.

---

### Post by BabyBoy on 2006-06-14
i dont have an apt.conf :sad: 

I really have no idea why it would be using a proxy i am on network with a router but it never interfierd before at alll and no one has messed with it what so ever so its definatly not that!

Really stuck guys and i really need to update have done it in 4 months lol.;)

---

### Post by Heaf on 2007-11-12
I know the date  when this have posted but 
try this 

[1] Open a terminal window - Applications > Accessories > Terminal
[2] Open the sources.list file for editing as super-user:
gksudo gedit /etc/sources.list
[3] Replace its content with the following:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Re...es/CommandLine](https://help.ubuntu.com/community/Re...es/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

[4] Use the following command to update your packages information:
sudo apt-get update

if you r using different version of ubuntu just change the  (feisty) to your own version

---

