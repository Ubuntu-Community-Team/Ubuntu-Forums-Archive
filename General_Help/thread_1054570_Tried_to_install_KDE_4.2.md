---
title: "Tried to install KDE 4.2"
date: 2009-01-29
forum: General Help
---

### Post by sports fan Matt on 2009-01-29
and stopped the package manager before it was done..I have kde packages but would rather completely remove KDE...This is the message from terminal: ldconfig deferred processing now taking place
Setting up kdm (4:4.1.4-0ubuntu1~intrepid3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing kdm (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up kdm (4:4.1.4-0ubuntu1~intrepid3) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing kdm (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kdm

How borked is my system at this point?

---

### Post by sports fan Matt on 2009-01-29
just an update: I ran a test and can tick all the kde packages through synaptic but cant uninstall them..the message appears..any ideas?

Edit: 2,000 posts:)

---

### Post by sports fan Matt on 2009-01-29
err, no...only 1,100..my bad

---

### Post by sports fan Matt on 2009-01-29
It seems I have a broken package but it wont show up in Symnaptic under "broken", and sorry to keep posting, just giving as much helpful info as possible :)

---

### Post by sports fan Matt on 2009-01-30
additional errors with synaptic: E: kdm: subprocess post-installation script returned error exit status 1
E: libglide2: subprocess post-installation script returned error exit status 1
E: libggi2: dependency problems - leaving unconfigured
E: libggi-target-x: dependency problems - leaving unconfigured
E: vlc-plugin-ggi: dependency problems - leaving unconfigured

---

### Post by sports fan Matt on 2009-01-30
I think i may have to reinstall/upgrade to 8.10..I cant figure out if this is a hosed system or not..Can someone at least tell me if it has errors beyond repair?

---

### Post by kmac on 2009-01-30
Can you get to the log where the errors are?

---

### Post by sports fan Matt on 2009-01-30
I can get into System>Admin>System log..without it throwing up errors..but what would one need?

---

### Post by halovivek on 2009-01-30
> **sox fan Matt said:**
> I think i may have to reinstall/upgrade to 8.10..I cant figure out if this is a hosed system or not..Can someone at least tell me if it has errors beyond repair?

I am also getting the same error in 8.10.

---

### Post by sports fan Matt on 2009-01-30
Halo, may I ask which set or all of them?

---

### Post by sports fan Matt on 2009-01-30
This morning after last night just trying to randomly remove residual config, it removed ..so i'll keep an eye out and see if it gives any more errors

---

### Post by theozzlives on 2009-01-30
You might wanna try:
```
sudo dpkg --configure -a
```
then:
```
sudo apt-get install -f
```
if that works, try this [http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

