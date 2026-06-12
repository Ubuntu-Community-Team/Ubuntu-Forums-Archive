---
title: "Updates Failed to fetch 404 Not found"
date: 2010-10-24
forum: Desktop Environments
---

### Post by itbcn8 on 2010-10-24
Hi all,
I have been having trouble with my updates, specifically these:

linux-generic
linux-headers-2.6.32-25 (New install)
linux-headers-2.6.32-25-generic (New install)
linux-headers-generic
linux-image-2.6.32-25-generic (New install)
linux-image-generic
linux-libc-dev

When I try to install these updates I get the following error message:

W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-25-generic_2.6.32-25.44_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-25-generic_2.6.32-25.44_i386.deb)
  404  Not Found


W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-25_2.6.32-25.44_all.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-25_2.6.32-25.44_all.deb)
  404  Not Found


W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-25-generic_2.6.32-25.44_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-25-generic_2.6.32-25.44_i386.deb)
  404  Not Found


W: Failed to fetch [http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-25.44_i386.deb](http://es.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-25.44_i386.deb)
  404  Not Found


Any suggestions?

---

### Post by blackcobra on 2010-10-24
yeah error 404 means that it failed to connect to the server.
try clicking the link [http://es.archive.ubuntu.com/ubuntu/...25.44_i386.deb](http://es.archive.ubuntu.com/ubuntu/...25.44_i386.deb)
(opps the link is not found) try changing your repository check out this forum  for details [http://ubuntuforums.org/showthread.php?t=822656](http://ubuntuforums.org/showthread.php?t=822656)

try this:

sudo add-apt-repository ppa:kernel-ppa/ppa

and try updating again

---

### Post by itbcn8 on 2010-10-24
Ah ok,
I just ran sudo apt-get update && sudo apt-get upgrade and it updated (i guess from the main repository)...

Looks like spain servers were failing (surprise surprise...)

So I just switched it to Main in software sources for the future.

Thanks for pointing me in the right direction!!


Problem SOLVED.

---

### Post by itbcn8 on 2010-10-24
WAIT! Not solved. Now look at what it says when I try and check for updates:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://apt.spideroak.com](http://apt.spideroak.com) release Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5D654504F1A41D5E

W: Failed to fetch [http://apt.spideroak.com/ubuntu-spideroak-hardy/dists/release/Release](http://apt.spideroak.com/ubuntu-spideroak-hardy/dists/release/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by RJARRRPCGP on 2010-10-24
> 
  404  Not Found


Means the files got deleted from the mirror.

---

### Post by kabeza on 2011-04-25
> **RJARRRPCGP said:**
> Means the files got deleted from the mirror.

sorry for bumping. I'm having the same problem. Does this mean I should remove the conflicting ppas? Thanks

---

### Post by KegHead on 2011-04-25
Hi!

You could try a different server.

Then in terminal;

sudo apt-get update

sudo apt-get upgrade-f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

Advise.

KegHead

---

