---
title: "Weird sources.list update error"
date: 2005-12-28
forum: General Help
---

### Post by Seth Williamson on 2005-12-28
My brother and I both run Kubuntu, and we both have the same identical sources.list file.  However, when I tried an apt-get update today, I got the error messages below, which he did NOT get, with the same sources.list.  I don't get it.  We are in adjacent states--Virginia and West Virginia--and perhaps there's some kind of weird routing problem.  But I just don't understand it.  Can somebody help?  These are the error messages:

99% [10 Packages gzip 0] [Waiting for headers]                                                                                                  10.1kB/s 0s
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  Sub-process gzip returned an error code (1)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Fetched 59.6kB in 11s (4984B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [http://claws.sylpheed.org](http://claws.sylpheed.org) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4B73A55696D94189
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Seth Williamson
Slings Gap
Franklin County, VA

---

### Post by Swab on 2005-12-28
comment out all of your sources, then apt-get update..
uncomment your sources and apt-get update again...
fixed this problem for me.

---

### Post by Seth Williamson on 2005-12-28
[QUOTE=Swab]comment out all of your sources, then apt-get update..
uncomment your sources and apt-get update again...
fixed this problem for me.[/QUOTE]

This worked like magic.  Thanks so much for your help.

Can you--or can somebody--explain to me WHY this helped?  I am trying to understand Linux and Debian and Kubuntu, and I can't figure out exactly what was wrong here, or why the procedure you suggested above worked.  Thanks a lot.


Seth Williamson
Slings Gap
Franklin County, VA
USA

---

### Post by Swab on 2005-12-29
Well GPG is an encryption key... I think it's used here to make sure you are actually connected to the correct server and not some evil crackers box.  So I can only assume that somehow the key on your machine didn't match the key on server.   Why this should be the case I don't know.  

Also I have no idea about this one "Sub-process gzip returned an error code (1)"

---

### Post by Footer on 2005-12-29
Here's how it was explained to me by aysiu:

"I don't know why, but apparently, there's some kind of residual "bad" signatures that need to be cleaned out..."

A few of us were having this problem back in November (post #4 and on):

[http://www.ubuntuforums.org/showthread.php?t=91804](http://www.ubuntuforums.org/showthread.php?t=91804)

Obivously, it's still a problem every now and again.

:)

---

