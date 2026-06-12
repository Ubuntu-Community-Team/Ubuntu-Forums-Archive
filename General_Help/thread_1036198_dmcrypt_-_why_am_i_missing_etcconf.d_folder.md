---
title: "dmcrypt - why am i missing /etc/conf.d/ folder?"
date: 2009-01-10
forum: General Help
---

### Post by johnnydopefish on 2009-01-10
Ubuntu 8.10

I'm trying to encrypt a partition using [this guide]("http://blog.pioto.org/2007/12/encrypting-your-home.html") and everything worked great, up until it says:

> 
Before we continue, we should configure the system to mount our new /home at boot. This requires editing ... /etc/conf.d/dmcrypt:


  # /etc/conf.d/dmcrypt
  # This file has all sorts of comments in it already
  # just uncomment the following:

  ## /home with passphrase
  target=crypt-home
  source='/dev/hda4'


Problem is, I don't have an /etc/conf.d folder.  Creating one containing the file the guide tells me to use results in a fsck failure at boot.

So I have the encrypted partition set up and everything, but right now the problem I'm having is getting the dmcrypt module loaded automatically and getting this dmcrypt configuration thing set up so that fstab recognizing /dev/mapper as a valid partition.

Anybody else have experience with getting dmcrypt set up?  What am I doing wrong?

Thanks

---

### Post by johnnydopefish on 2009-01-10
Solved.

Ubuntu doesn't seem to use conf.d for anything, so the guide needed some deviation for Debian users.

On Ubuntu 8.10 at least, instead of /etc/conf.d/dmcrypt you gotta add an entry to /etc/crypttab like this:

# <target name>	<source device>		<key file>	<options>
home	        /dev/hda4		none		luks

---

