---
title: "Error when trying to reload repos"
date: 2009-02-02
forum: General Help
---

### Post by Smeags on 2009-02-02
When reloading the repos and downloading updates it freezes every time.  I got this error when trying to enable and reload the repositories.  It means nothing to me but hopefully someone here can help me out.


W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


Any help is appreciated...I'm a noob to Ubuntu.

---

### Post by kostkon on 2009-02-02
Open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and give the following to add the Medibuntu key
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
It will ask you for a password, give yours.

---

### Post by Smeags on 2009-02-03
I'll give this a shot as soon as I get the chance.  Thanks for the reply, kostkon!

---

### Post by Smeags on 2009-02-05
That worked.  Thanks again kostkon!

---

