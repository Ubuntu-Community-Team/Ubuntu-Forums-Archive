---
title: "SOS -- problem with apt-get update"
date: 2009-05-08
forum: General Help
---

### Post by lordbux on 2009-05-08
i am getting this error..


```
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9423A34CCA967634
```:confused::(

please help me fix this.

---

### Post by lordbux on 2009-05-08
solve  
use this code

```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 9423A34CCA967634 && gpg --armor --export $key | sudo apt-key add -
```

---

### Post by haired on 2009-05-08
Try:
```
sudo gpg --keyserver subkeys.pgp.net --recv 9423A34CCA967634
```and then:

```
sudo gpg --export --armor 9423A34CCA967634 | sudo apt-key add -
```Edit: Beat me to it. ;p

---

