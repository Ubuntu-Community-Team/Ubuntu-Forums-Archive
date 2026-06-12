---
title: "Where's MPlayer"
date: 2005-03-20
forum: Desktop Environments
---

### Post by malegria on 2005-03-20
This is my current /etc/apt.sources.list :
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)]/ hoary main restricted


deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted
```

And yet I can't get the mplayer package. I know I can very well compile from the source and the same for the plugin, but I liked the ease of being able to apt-get it.

Any ideas?

---

### Post by DJ_Max on 2005-03-20
Do
```
apt-cache search mplayer
```

Make sure you have updated your listings.
```
sudo apt-get update
```

---

### Post by c_dog on 2005-03-20
Ubuntu mplayer is "multiverse" compoent. You'll need to add that repository to your ubuntu archive line.

I've never gotten the Ubuntu Mplayer to work, but the debian Mplayer packages work fine.

# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

Depending on which platform you're using amd64, i386, or PPC you'll need to either comment out the "sid" testing line or the "sarge" unstable with Hoary. The stable release works with Warty.

---

### Post by Darrena on 2005-03-20
You may also want to consider kplayer, it is a KDE media player based on mplayer:

[http://kplayer.sourceforge.net/](http://kplayer.sourceforge.net/)

---

### Post by Anubis on 2005-03-21
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted




Thats my apt.source.list and I can't install mplayer either.

---

### Post by malegria on 2005-03-21
Follow DJ Max's instruction and you'll see how to.

Worked for me.

---

### Post by rudeboyskunk on 2005-03-22
every single time i add deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main, or stable main, or testing main, or all three, and then run apt-get update, this is what i get:

Reading Package Lists... Done
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems
root@timebomb:/home/rudepirate #

---

### Post by mike998 on 2005-03-22
You need to install your own GPG key and import the GPG key from nerim.  Search brought this up
[http://www.ubuntuforums.org/showthread.php?t=8763&highlight=nerim+gpg](http://www.ubuntuforums.org/showthread.php?t=8763&highlight=nerim+gpg)
I had to do this myself, and it's easy to rememdy.

---

### Post by Trauma on 2005-04-13
If i follow Dj max instructions

apt get doesn't find any packages 
Even if i update my listings.
and i'm sort of new to linux so i don't understand everything yet :???:

---

### Post by egnaro on 2005-04-13
I found these instructions quite helpful.
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) 
It tells you how to update your gpg keys after adding.
Mplayer does show up in my apt-get after doing this.

---

### Post by Dr Gonzo on 2005-04-13
Hey, all, the backports repository was for Hoary packages backported to Warty.

Until there's a new development branch, the backports lists don't help.  I'd remove them for now.

---

### Post by skunkydog on 2005-04-24
I followed the instructions at [http://www.ubuntulinux.org/wiki/InstallingMplayerFromHoaryInWarty](http://www.ubuntulinux.org/wiki/InstallingMplayerFromHoaryInWarty) and that worked for me.  I'm running Hoary 5.04.

---

