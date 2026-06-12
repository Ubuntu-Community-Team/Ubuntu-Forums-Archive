---
title: "Error from Synaptic"
date: 2009-02-10
forum: General Help
---

### Post by lsutiger on 2009-02-10
I am receiving the following error from Synaptic:
```
GPG error: http://download.virtualbox.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
Failed to fetch http://mirror.ubuntulinux.nl/dists/hardy-seveas/freenx/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://mirror.ubuntulinux.nl/dists/hardy-seveas/freenx/source/Sources.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

What do I need to do to fix this?

---

### Post by taurus on 2009-02-10
Are you sure the [http://download.virtualbox.org](http://download.virtualbox.org) is good?

Go into synaptic and change to another server.  If you are in LA, why do you use "nl" server?  Switch over to US or at least the Main Server.

---

### Post by slmagus on 2009-02-10
This should fix GPG error 

```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

```

Then reload the indexes via synaptic or command line

Taken from :

[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

---

### Post by lsutiger on 2009-02-10
Thanx for the replies. This what I get after running the command from Sun and running apt-get update:
```
W: GPG error: http://download.virtualbox.org hardy Release: The following signatures were invalid: BADSIG DCF9F87B6DFBCBAE Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>
W: You may want to run apt-get update to correct these problems

```

---

### Post by hikaricore on 2009-02-10
Read the section of that same page about adding the key..

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by lsutiger on 2009-02-10
> **hikaricore said:**
> Read the section of that same page about adding the key..

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

I have read the page and followed the instructions. I do not know what I am missing.

---

### Post by hikaricore on 2009-02-10
```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```

^

---

### Post by lsutiger on 2009-02-10
Correct...that is the code I copied and pasted into terminal. I get OK as a response. I then run sudo apt-get update and get the error posted above.

---

### Post by hikaricore on 2009-02-10
Then something is wrong with their key, this is not a fatal error and can be ignored.

---

