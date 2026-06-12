---
title: "apt-get update"
date: 2004-12-20
forum: Desktop Environments
---

### Post by jbarroso on 2004-12-20
Hi, how can I get 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
source, now it says me:
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B90

I went to nerim home page, and I executed:

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907

but, it won't work

And other question:

when I had:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe
on my /etc/apt/sources.list
i had got:
bad header line

I found on forum, about it is a proxy error, do you know how can I do to solve this problem? 
Now, I changed from http to ftp, and all is fine

Thanks you! 

Sorry for my poor english

---

### Post by rwabel on 2004-12-20
[QUOTE=jbarroso]Hi, how can I get 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
source, now it says me:
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B90

I went to nerim home page, and I executed:

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907

but, it won't work

And other question:

when I had:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe
on my /etc/apt/sources.list
i had got:
bad header line

I found on forum, about it is a proxy error, do you know how can I do to solve this problem? 
Now, I changed from http to ftp, and all is fine

Thanks you! 

Sorry for my poor english[/QUOTE]

It's the same for me:
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.us.debian.org](ftp://ftp.us.debian.org) experimental Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6FFA8EF91DB114E0

but as long as the updates are running, I'm O.K.

---

### Post by waratah on 2005-02-19
For those cruising in...

See [http://ubuntuforums.org/showthread.php?p=66309#post66309](http://ubuntuforums.org/showthread.php?p=66309#post66309)

You also need to run:

gpg --armor --export 1F41B907 | sudo apt-key add -

---

