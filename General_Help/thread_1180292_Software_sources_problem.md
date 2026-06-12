---
title: "Software sources problem"
date: 2009-06-06
forum: General Help
---

### Post by Robbyx on 2009-06-06
When  I do a software source update this comes at the end:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CA1F91146F087E5A
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EE6F9258A958418A
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4BDB868079581714


How do  I work out what has to be removed from the above.

---

### Post by lindsay7 on 2009-06-06
type these commands in the terminal one at a time, where it says [COLOR="Red"]KEY[/COLOR], put in the key number. You should only need the last eight digits.  Do this for all the key numbers listed.

gpg --keyserver hkp://subkeys.pgp.net --recv-keys [COLOR="Red"]KEY[/COLOR]

gpg --export --armor [COLOR="Red"]KEY[/COLOR] | sudo apt-key add -


When you are done type sudo apt-get update  and then 
sudo apt-get upgrade

---

### Post by Robbyx on 2009-06-06
Thank you.

---

