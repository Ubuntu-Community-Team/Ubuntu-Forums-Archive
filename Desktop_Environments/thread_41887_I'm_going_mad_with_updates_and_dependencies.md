---
title: "I'm going mad with updates and dependencies"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Sav on 2005-06-15
Hi, it's all started when I decided to get ac3 audio streaming working.
I started to add repositories.
Now my sources are:
> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#Primary Mirror (5/17/2005) overloaded :)
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted


But now I get this errors:
> [http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz:) 401 Authorization Required


Plus, I'm unable to add the marillat sig.
I did:

1) gpg --recv-keys 07DC563D1F41B907
2) gpg --export 07DC563D1F41B907 >marillat.sig

But when I tried to add the marillat.sig in ubuntu update manager, I got this error message: The selected file may not be a GPG key file or it might be corrupt.
Now I can't upgrade the following packages

acroread
ffmpeg
libavcodeccvs
libpostproc0
libxvidcore4
mplayer-386

and I'm still unable to play divxs with ac3 sound.

---

### Post by desdinova on 2005-06-15
on the backports website it says to use a mirror, not the main site - try one of the other backposts mirrors....

---

### Post by Knome_fan on 2005-06-15
I think there are some issues with the marillat repos and hoary at the moment, so it's probably best to simply get rid of them.

You should also only use mirrors for the backports repos, as they are the only ones that work, so get rid of the primary mirror too.

---

### Post by psychicdragon on 2005-06-15
Use these for your backports repos instead:
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by Sav on 2005-06-15
Now my source list is:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sid main
deb-src [http://download.videolan.org/pub/videolan/debian/](http://download.videolan.org/pub/videolan/debian/) sid main

But there is a mismatch with the libvorbis version, so I can't upgrade ffmpeg, libavcodeccvs, etc...

By the way I found a solution to play movies: xine
But avidemux doesn't still recognize any ac3 codec.

---

### Post by Knome_fan on 2005-06-15
Again, I think it would be a good idea to get rid of the marillat repositories and probably also the videolan repositories. At least the mariallat repositories are known to cause problems with hoary.

---

### Post by Sav on 2005-06-15
[QUOTE=Knome_fan]Again, I think it would be a good idea to get rid of the marillat repositories and probably also the videolan repositories. At least the mariallat repositories are known to cause problems with hoary.[/QUOTE]

Thanks, no more error messages from synaptic.
By the way there isn't still a valid ac3 codec to use with avidemux.

---

### Post by Knome_fan on 2005-06-15
Hm, I'm really no expert when it comes to stuff like this, but did you try liba52, or gstreamer0.8-a52dec?

---

### Post by Sav on 2005-06-22
[QUOTE=Knome_fan]Hm, I'm really no expert when it comes to stuff like this, but did you try liba52, or gstreamer0.8-a52dec?[/QUOTE]

Sorry for the late reply and tanks for your support.
Those libraries are already installed.

---

