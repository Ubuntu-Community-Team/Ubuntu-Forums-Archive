---
title: "Update Problem"
date: 2009-03-19
forum: General Help
---

### Post by golfer32 on 2009-03-19
When trying to update Ubuntu 8.10 in the update manager I get these errors:


W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 778978B00F7992B0

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680

W: GPG error: [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2C392DFEEFD17969
W: Failed to fetch [http://ppa.launchpad.net/project-neon/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/project-neon/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/Release](http://wine.budgetdedicated.com/apt/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.

It seems I need a Public Key.  Where do I get this key and how do I install it?

---

### Post by golfer32 on 2009-03-19
bump

---

### Post by drs305 on 2009-03-19
You can use the following code, and I believe you can include multiple keys on the same line:
```

gpg --keyserver keyserver.ubuntu.com --recv A040830F7FAC5991  778978B00F7992B0  58403026387EE263   60D11217247D1CFF  632D16BB0C713DA6 43C0AFF0D7FAE680 2C392DFEEFD17969
gpg --export --armor A040830F7FAC5991  778978B00F7992B0  58403026387EE263   60D11217247D1CFF  632D16BB0C713DA6 43C0AFF0D7FAE680 2C392DFEEFD17969 | sudo apt-key add -
sudo apt-get update


```

Launchpad recently starting using keys to improve security, which is why you started getting the error messages.

---

### Post by AoA Linux on 2009-03-19
I had the same problem and I now have the pub keys but now I get the following message when I try to update:

E: /var/cache/apt/archives/amsn_0.97.20070524-1_i386.deb: trying to overwrite `/usr/share/doc/amsn/READMEru', which is also in package amsn-data

W: Failed to fetch [http://repoubuntusoftware.info/./pidgin-libnotify_0.13-1~getdeb1_i386.deb](http://repoubuntusoftware.info/./pidgin-libnotify_0.13-1~getdeb1_i386.deb)
  404 Not Found


W: Failed to fetch [http://repoubuntusoftware.info/./w32codecs_1_20061022-0.0-0ubuntu1_i386.deb](http://repoubuntusoftware.info/./w32codecs_1_20061022-0.0-0ubuntu1_i386.deb)
  404 Not Found

Can someone help me with this?

---

### Post by golfer32 on 2009-03-19
> **drs305 said:**
> You can use the following code, and I believe you can include multiple keys on the same line:
```

gpg --keyserver keyserver.ubuntu.com --recv A040830F7FAC5991  778978B00F7992B0  58403026387EE263   60D11217247D1CFF  632D16BB0C713DA6 43C0AFF0D7FAE680 2C392DFEEFD17969
gpg --export --armor A040830F7FAC5991  778978B00F7992B0  58403026387EE263   60D11217247D1CFF  632D16BB0C713DA6 43C0AFF0D7FAE680 2C392DFEEFD17969 | sudo apt-key add -
sudo apt-get update


```

Launchpad recently starting using keys to improve security, which is why you started getting the error messages.


Ok I did this and it worked great. It installed several updates but after it was done it wanted to update again so I did and I got this:

Failed to fetch [http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas?

---

### Post by golfer32 on 2009-03-20
bump

---

### Post by drs305 on 2009-03-20
That repository only has hardy repositories at the present time and you are requesting an intrepid package. You may have to find the package on another server. You can see the problem if you start with the first part of the address ( [http://http://ppa.launchpad.net/googlegadgets/ubuntu/dists/]("http://ppa.launchpad.net/googlegadgets/ubuntu/dists/")and click on the subfolders. Eventually you will end up with only two choices: Parent Directory and Hardy.

---

### Post by golfer32 on 2009-03-22
Thanks I got it fixed.

---

