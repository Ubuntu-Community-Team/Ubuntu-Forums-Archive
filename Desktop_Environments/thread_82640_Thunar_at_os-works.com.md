---
title: "Thunar at os-works.com"
date: 2005-10-26
forum: Desktop Environments
---

### Post by ecobuntu on 2005-10-26
Hi-
I want to use Thunar for my file manager for XFCE4 and I found a repository at os-works.com that has it.  I guess it's Benny's repository (the developer of Thunar).  
I don't know how to add his key to apt so when i run sudo apt-get update after adding the repository to sources.list... I get this

W: GPG error: [http://www.os-works.com](http://www.os-works.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CF455A0A8AC2C0A6
W: You may want to run apt-get update to correct these problems

How do I fix this?  I would really like to get Thunar and can rox-filer.  Also I would like to see Thunar backported if possible!

---

### Post by ecobuntu on 2005-10-26
[QUOTE=ecobuntu]Hi-
I want to use Thunar for my file manager for XFCE4 and I found a repository at os-works.com that has it.  I guess it's Benny's repository (the developer of Thunar).  
I don't know how to add his key to apt so when i run sudo apt-get update after adding the repository to sources.list... I get this

W: GPG error: [http://www.os-works.com](http://www.os-works.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CF455A0A8AC2C0A6
W: You may want to run apt-get update to correct these problems

How do I fix this?  I would really like to get Thunar and can rox-filer.  Also I would like to see Thunar backported if possible![/QUOTE]

Fixed my problem...here is how I did it.  

added to /etc/apt/sources.list...
deb [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main
deb-src [http://www.os-works.com/debian](http://www.os-works.com/debian) testing main

Then...
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 8AC2C0A6
sudo gpg --armor --export 0x8AC2C0A6 | sudo apt-key add -
sudo apt-get update
sudo apt-get install thunar

---

