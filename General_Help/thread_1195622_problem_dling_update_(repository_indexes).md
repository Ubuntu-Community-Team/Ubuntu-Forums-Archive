---
title: "problem d/ling update (repository indexes)"
date: 2009-06-24
forum: General Help
---

### Post by rhythmiccycle on 2009-06-24
i'm using a public network at my work.

i'm trying to add some software sources.
i've done this from my home with out any problem.

when i was trying to do this at work, i got this message

> 
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


and then

> 
GPG error: [http://mirror.noreply.org](http://mirror.noreply.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDDFailed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.noreply.org/pub/tor/dists/jaunty/main/binary-i386/Packages.bz2](http://mirror.noreply.org/pub/tor/dists/jaunty/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.noreply.org/pub/tor/dists/jaunty/main/source/Sources.bz2](http://mirror.noreply.org/pub/tor/dists/jaunty/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.


i know this is because of the security on the network i'm on.

my question is,

is there a was to get these file from the network?

OR

is there a way for me to get the files from my home and bring them to work?

---

### Post by dcstar on 2009-06-24
> **rhythmiccycle said:**
> i'm using a public network at my work.
........
i know this is because of the security on the network i'm on.

my question is,

is there a was to get these file from the network?
........

**You** have to find out how the network will allow Internet access.

---

### Post by rhythmiccycle on 2009-06-24
i do have internet access. but its limited. its under a comsifter.

i'm thinking that i could download the files at my house and then bring that to work. But i don't know how to do that.

---

