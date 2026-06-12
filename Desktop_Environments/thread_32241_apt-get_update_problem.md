---
title: "apt-get update problem"
date: 2005-05-06
forum: Desktop Environments
---

### Post by antoniost on 2005-05-06
Hello 

I try to update kubuntu through konsole ( sudo apt-get update ) , and i have these error messages : 

..............Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957; 34,6kB &#963;&#949; 1m58s (293B/s)
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... Completed
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may run apt-get update to correct these problems
antonios@dhcppc3:~$                                 


What does this means ?Can i do something for this ?

---

### Post by joshmachine on 2005-05-06
> **antoniost]Hello 

I try to update kubuntu through konsole ( sudo apt-get update ) , and i have these error messages : 

..............Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
&#924 said:**
> ftp://ftp.nerim.net[/url] stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may run apt-get update to correct these problems
antonios@dhcppc3:~$                                 


What does this means ?Can i do something for this ?
 I don't believe that this is a fatal error, and the packages from ftp.nerim.net will still be available.

The reason that this happens is that some of the apt repositories use public key encryption to sign their package lists.  All of ubuntu's are signed and the public keys are already know to apt.  If you add non ubuntu ones you have to tell apt what the "good" public keys are.

Try step 6 in the adding extra repositories section of the howto guide at 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Then the errors should stop appearing.

Cheers

---

### Post by antoniost on 2005-05-06
[QUOTE=joshmachine]I don't believe that this is a fatal error, and the packages from ftp.nerim.net will still be available.

The reason that this happens is that some of the apt repositories use public key encryption to sign their package lists.  All of ubuntu's are signed and the public keys are already know to apt.  If you add non ubuntu ones you have to tell apt what the "good" public keys are.

Try step 6 in the adding extra repositories section of the howto guide at 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

Then the errors should stop appearing.

Cheers[/QUOTE]


Thanks.
The problem solved

---

### Post by crazybill on 2005-05-06
Nice. Thanks

---

### Post by antoniost on 2005-05-31
Now , when i give :  sudo apt-get update    ,  i take this   :

........................................................................................

&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957; 17,5kB &#963;&#949; 40s (431B/s)
&#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz)   403 Forbidden
&#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz)   403 Forbidden
&#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz)   403 Forbidden
&#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz)   403 Forbidden
&#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz)   403 Forbidden
&#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz)   403 Forbidden
&#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz)   403 Forbidden
&#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz)   403 Forbidden
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages)
W: You may run apt-get update to correct these problems E: Some file didn't downloaded, ignored  or used other older 

What are all these error messages again ?
Can i correct these ?

---

### Post by antoniost on 2005-05-31
I also get the mesage that :

W: Impossible to find the list of the source packages [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat(2 There is not such file or folder)
....................................................................



How can i correct this ?

---

### Post by jagguars on 2005-06-04
did you try to use your old sources.list and just factor out the nerim adresses. they don't work realy good at my version too.
The sources.list version from the link worked, but i factored out the us. servers, cause i installed a version in my language. most times, and if kubuntu at the installation supports your language, it works to edit the us when you just put your country shortcuts instead of the us. 

mfg jagg

---

