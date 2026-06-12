---
title: "Trouble adding repositories"
date: 2009-03-09
forum: General Help
---

### Post by funky_uncle on 2009-03-09
Following the instructions on [http://www.google.com/linuxrepositories/testrepo.html](http://www.google.com/linuxrepositories/testrepo.html), I add this to my software sources list :```
deb http://dl.google.com/linux/deb/ stable non-free
```only to end up with this ```
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991

```

This has happened with other repos as well. Any idea what it means and how to fix it?

---

### Post by plucky on 2009-03-09
On the link you gave there is this note > Note that you also need to follow the other steps specified in the regular repository configuration guides, such as importing the Google package signing key.

Download the file to your computer,make a note of the name, and then add it using "Software Sources" in the Authentication GUI (Import Key File).


Good Luck

---

### Post by funky_uncle on 2009-03-09
I see. So the authentication is a security measure of sorts?

edit: still can't find picasa in the repos even though I added both the stable and testing repos from Google, and the authentication key.

edit 2: but typing```
sudo apt-get install picasa
``` worked. I just can't see it in the package manager for some reason.

---

### Post by plucky on 2009-03-09
Try ```
sudo apt-get update
``` and then see if you can find it in synaptic.

Good Luck

---

### Post by funky_uncle on 2009-03-09
> **plucky said:**
> Try ```
sudo apt-get update
``` and then see if you can find it in synaptic.

Good LuckDunno... here's the output:```
(snip)

Hit http://us.archive.ubuntu.com intrepid-security/universe Packages
Hit http://us.archive.ubuntu.com intrepid-security/multiverse Packages
Hit http://packages.medibuntu.org intrepid/non-free Packages
Fetched 4151B in 0s (6818B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by plucky on 2009-03-09
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it

You cannot have two package managers open,so you need to close synaptic or add/remove before using that command.That lock stops you installing packages on the system from more than one package manager at a time.

---

### Post by funky_uncle on 2009-03-10
> **plucky said:**
> You cannot have two package managers open,so you need to close synaptic or add/remove before using that command.That lock stops you installing packages on the system from more than one package manager at a time.OK, I made sure Synaptic wasn't running in the background and didn't get any errors this time. But I still can't find Picasa in Synaptic. Not a big deal, but I'll probably want to uninstall it later, and I suspect that's going to be a hassle.

---

