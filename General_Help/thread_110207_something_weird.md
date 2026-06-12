---
title: "something weird :"
date: 2005-12-30
forum: General Help
---

### Post by cvcaelen on 2005-12-30
when I type in terminal ```
winecfg
```

I get :

[IMG]http://images.fotopic.net/yei3ib.jpg[/IMG]

Can someone tell me what's wrong?
Looks like a font is missing ?

Thanks in advance
Christiaan

---

### Post by cvcaelen on 2005-12-31
Nobody :confused: 

it's a pretty frustrating thing ya know.

In the mean time I've updated to Wine 9.4, but the problem still exists(maybe it got nothing to do with wine :(  )

when I " sudo apt-get update" I get :

```
christiaan@telenetPC:~$ sudo apt-get update
Ophalen:1 http://be.archive.ubuntu.com breezy Release.gpg [189B]
Ophalen:2 http://be.archive.ubuntu.com breezy-updates Release.gpg [189B]
Genegeerd http://be.archive.ubuntu.com breezy-backports Release.gpg
Geraakt http://be.archive.ubuntu.com breezy Release
Geraakt http://be.archive.ubuntu.com breezy-updates Release
Ophalen:3 http://security.ubuntu.com breezy-security Release.gpg [189B]
Genegeerd http://be.archive.ubuntu.com breezy-backports Release
Geraakt http://security.ubuntu.com breezy-security Release
Geraakt http://be.archive.ubuntu.com breezy/main Sources
Geraakt http://be.archive.ubuntu.com breezy/restricted Sources
Geraakt http://be.archive.ubuntu.com breezy/universe Packages
Geraakt http://be.archive.ubuntu.com breezy/main Packages
Geraakt http://be.archive.ubuntu.com breezy/restricted Packages
Geraakt http://be.archive.ubuntu.com breezy/multiverse Packages
Geraakt http://be.archive.ubuntu.com breezy/universe Sources
Geraakt http://security.ubuntu.com breezy-security/main Packages
Genegeerd http://wine.sourceforge.net binary/ Release.gpg
Geraakt http://be.archive.ubuntu.com breezy-updates/main Packages
Geraakt http://be.archive.ubuntu.com breezy-updates/restricted Packages
Geraakt http://be.archive.ubuntu.com breezy-updates/main Sources
Geraakt http://be.archive.ubuntu.com breezy-updates/restricted Sources
Genegeerd http://be.archive.ubuntu.com breezy-backports/main Packages
Genegeerd http://be.archive.ubuntu.com breezy-backports/restricted Packages
Geraakt http://security.ubuntu.com breezy-security/restricted Packages
Geraakt http://security.ubuntu.com breezy-security/main Sources
Genegeerd http://be.archive.ubuntu.com breezy-backports/universe Packages
Genegeerd http://be.archive.ubuntu.com breezy-backports/multiverse Packages
Genegeerd http://be.archive.ubuntu.com breezy-backports/main Sources
Genegeerd http://be.archive.ubuntu.com breezy-backports/restricted Sources
Geraakt http://security.ubuntu.com breezy-security/restricted Sources
Geraakt http://security.ubuntu.com breezy-security/universe Packages
Geraakt http://security.ubuntu.com breezy-security/universe Sources
Genegeerd http://be.archive.ubuntu.com breezy-backports/universe Sources
Genegeerd http://be.archive.ubuntu.com breezy-backports/multiverse Sources
Fout http://be.archive.ubuntu.com breezy-backports/main Packages
  404 Not Found
Geraakt http://wine.sourceforge.net binary/ Release
Fout http://be.archive.ubuntu.com breezy-backports/restricted Packages
  404 Not Found
Fout http://be.archive.ubuntu.com breezy-backports/universe Packages
  404 Not Found
Fout http://be.archive.ubuntu.com breezy-backports/multiverse Packages
  404 Not Found
Fout http://be.archive.ubuntu.com breezy-backports/main Sources
  404 Not Found
Fout http://be.archive.ubuntu.com breezy-backports/restricted Sources
  404 Not Found
Fout http://be.archive.ubuntu.com breezy-backports/universe Sources
  404 Not Found
Fout http://be.archive.ubuntu.com breezy-backports/multiverse Sources
  404 Not Found
Genegeerd http://wine.sourceforge.net binary/ Packages
Geraakt http://wine.sourceforge.net binary/ Packages
3B opgehaald in 3s (1B/s)
Ophalen van http://be.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz 404 Not Found is mislukt
Ophalen van http://be.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz 404 Not Found is mislukt
Ophalen van http://be.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz 404 Not Found is mislukt
Ophalen van http://be.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz 404 Not Found is mislukt
Ophalen van http://be.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz 404 Not Found is mislukt
Ophalen van http://be.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz 404 Not Found is mislukt
Ophalen van http://be.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz 404 Not Found is mislukt
Ophalen van http://be.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz 404 Not Found is mislukt
Pakketlijsten worden ingelezen... Klaar
W: Kon de status van de bronpakketlijst http://be.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/be.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst http://be.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/be.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst http://be.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/be.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst http://be.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/be.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: U kunt misschien 'apt-get update' uitvoeren om deze problemen te verhelpen
E: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.
christiaan@telenetPC:~$

```


edit:
the above problem is solved : my repositories were not correct, they are now,

but the first prob with winecfg STILL exists
Thanks in advance

Christiaan

---

