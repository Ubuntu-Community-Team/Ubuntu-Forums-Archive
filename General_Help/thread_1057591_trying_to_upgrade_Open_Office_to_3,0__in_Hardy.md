---
title: "trying to upgrade Open Office to 3,0  in Hardy"
date: 2009-02-02
forum: General Help
---

### Post by sports fan Matt on 2009-02-02
What have I done wrong and why is this error fetched?

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

---

### Post by jrusso2 on 2009-02-02
This is the one that worked for me on Hardy.

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

### Post by solwic on 2009-02-02
> **jrusso2 said:**
> This is the one that worked for me on Hardy.

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

+1.  Worked for me as well.

---

### Post by sports fan Matt on 2009-02-02
Worked well here as well, but why did it throw out that error?  Anyone have an idea?

---

### Post by mb_webguy on 2009-02-02
You didn't have the key (or the right key) for the PPA installed.

---

### Post by SunnyRabbiera on 2009-02-02
actually that error is meaningless, I was able to install OO 3.0.1 without issue from PPA

---

### Post by mb_webguy on 2009-02-02
Perhaps, but that was nonetheless why he was getting the error.

---

### Post by mikewhatever on 2009-02-02
Apparently, the most recent version of Open Office is 3.0.1. Will the upgrade to the latest version madness continue?

---

### Post by mb_webguy on 2009-02-02
Once you've added the openoffice-pkgs PPA, the hard work is done, and you'll receive updates for OpenOffice automatically.  Unlike updates from the Ubuntu repositories, these will included version upgrades as well as security updates and bug fixes.

---

