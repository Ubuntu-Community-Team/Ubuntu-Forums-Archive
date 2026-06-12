---
title: "update notification"
date: 2009-01-30
forum: General Help
---

### Post by banana jama on 2009-01-30
when i try to check for updates this message pops up:
 > W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
  does anyone know what this means? what can i do to resolve this? i've been looking on the internet but nothing specific.

---

### Post by Yellow Pasque on 2009-01-30
[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%27s%20keys%20to%20your%20system](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%27s%20keys%20to%20your%20system)

---

### Post by sisco311 on 2009-01-30
Open a terminal (Applications -> Accessories -> Terminal) 
and run this commands:
```
gpg --keyserver keyserver.ubuntu.com --recv 247d1cff
```
```
gpg --export --armor 247d1cff | sudo apt-key add -
```
and
```
sudo apt-get update
```

---

### Post by Zeedok on 2009-01-30
An enterprising user wrote a script which fixes the problem for me. The script can be found [here]("http://ubuntuforums.org/showthread.php?t=1047743&page=5"). 

Hope it helps (it seemed the easiest solution to me).

---

### Post by banana jama on 2009-01-30
thanks sisco311 the commands worked

---

