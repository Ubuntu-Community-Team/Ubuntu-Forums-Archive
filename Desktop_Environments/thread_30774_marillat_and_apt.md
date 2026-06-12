---
title: "marillat and apt"
date: 2005-04-30
forum: Desktop Environments
---

### Post by frs-design on 2005-04-30
Hi all,

I've got a problem adding these lines to my apt source.list:

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

after apt-get update, i got:

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

So i entered this command to tell where to find the gpg key:
sudo gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907

it gives me:
gpg: keyring `/home/user1/.gnupg/secring.gpg' created
gpg: keyring `/home/user1/.gnupg/pubring.gpg' created
gpg: /home/user1/.gnupg/trustdb.gpg: trustdb created
gpg: key 1F41B907: public key "Christian Marillat <marillat@debian.org>" imported
gpg: Total number processed: 1
gpg:               imported: 1


And always the same error after apt-get update.
I can't install mplayer or vlc  :? 

And if i try to install mplayer by compiling the source, the sudo ./configure --enable-gui is ok but the sudo make gives me errors  ](*,) 

How can i do ???

Thank you.
Bye

---

### Post by IdoMcFly on 2005-04-30
read ubuntuguide.org, there is a section on adding repository, it seems there is one more command line to enter.

---

### Post by frs-design on 2005-04-30
Thanks a lot, that rules !

sudo gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907         
plus: sudo gpg --armor --export 1F41B907 | sudo apt-key add -              


Bye

---

