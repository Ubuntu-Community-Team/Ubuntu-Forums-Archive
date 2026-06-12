---
title: "ppa.launchpad.net"
date: 2012-06-05
forum: Desktop Environments
---

### Post by dentaku65 on 2012-06-05
Hi,

can someone confirm that since yesterday the [http://ppa.launchpad.net](http://ppa.launchpad.net) (with all the repositories) is not reachable?

I'm using google DNS but I think that the site is really down....

by

---

### Post by Frogs Hair on 2012-06-05
A little late , but Lauchpad  has been up and running here on 6-4 and 6-5 2012.

---

### Post by dentaku65 on 2012-06-06
mmm... still not connecting on 6-6 :confused:

---

### Post by fballem on 2012-06-06
If I understand your objective correctly, then I assume that you want to get to the PPAs that are stored on Launchpad. If that's correct, would this URL be the correct one: [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas) ?

---

### Post by dentaku65 on 2012-06-06
> **fballem said:**
> If I understand your objective correctly, then I assume that you want to get to the PPAs that are stored on Launchpad. If that's correct, would this URL be the correct one: [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas) ?

Hi,

no... I mean that all my PPA configured as repositories are not reachable from my box, here the error since 2 days:

```
Ign http://ppa.launchpad.net precise InRelease        
Ign http://ppa.launchpad.net precise InRelease        
Ign http://ppa.launchpad.net precise InRelease        
Ign http://ppa.launchpad.net precise InRelease        
Ign http://ppa.launchpad.net precise InRelease        
Ign http://ppa.launchpad.net precise InRelease        
Ign http://ppa.launchpad.net precise InRelease        
Ign http://ppa.launchpad.net precise InRelease        
Err http://ppa.launchpad.net precise Release.gpg      
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise Release.gpg
  Unable to connect to ppa.launchpad.net:http:
Ign http://ppa.launchpad.net precise Release
Ign http://ppa.launchpad.net precise Release
Ign http://ppa.launchpad.net precise Release
Ign http://ppa.launchpad.net precise Release
Ign http://ppa.launchpad.net precise Release
Ign http://ppa.launchpad.net precise Release
Ign http://ppa.launchpad.net precise Release
Ign http://ppa.launchpad.net precise Release
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Err http://ppa.launchpad.net precise/main Sources
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main i386 Packages
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Translation-en
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Sources
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main i386 Packages
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Translation-en
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Sources
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main i386 Packages
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Translation-en
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Sources
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main i386 Packages
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Translation-en
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Sources
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main i386 Packages
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Translation-en
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Sources
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main i386 Packages
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Translation-en
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Sources
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main i386 Packages
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Translation-en
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Sources
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main i386 Packages
  Unable to connect to ppa.launchpad.net:http:
Err http://ppa.launchpad.net precise/main Translation-en
  Unable to connect to ppa.launchpad.net:http:
Fetched 5102 B in 1min 3s (80 B/s)
W: Failed to fetch http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/precise/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/precise/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu/dists/precise/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu/dists/precise/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/n-muench/vlc/ubuntu/dists/precise/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/precise/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/dists/precise/Release.gpg  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/precise/main/source/Sources  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/precise/main/source/Sources  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu/dists/precise/main/source/Sources  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/marlin-devs/marlin-daily/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu/dists/precise/main/source/Sources  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/n-muench/vlc/ubuntu/dists/precise/main/source/Sources  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/n-muench/vlc/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/n-muench/vlc/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/precise/main/source/Sources  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/shnatsel/zram/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/source/Sources  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/webupd8team/jupiter/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/dists/precise/main/source/Sources  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/dists/precise/main/binary-i386/Packages  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/dists/precise/main/i18n/Translation-en  Unable to connect to ppa.launchpad.net:http:

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

If I try to go via http [http://ppa.launchpad.net](http://ppa.launchpad.net) I get connection timeout; of course this happen only for ppa resources, everything else on the net works fine.

thx

---

### Post by zombifier25 on 2012-06-06
Dunno about you, but it's up and running here.

---

### Post by dentaku65 on 2012-06-06
Ok, I've found the issue... I've switched off/on the router and now I can access the PPAs.

The strange thing was that I was able to go anywhere except the ppa repos... ):P

---

