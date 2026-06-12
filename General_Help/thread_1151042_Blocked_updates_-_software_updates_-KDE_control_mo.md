---
title: "Blocked updates - software updates -KDE control module"
date: 2009-05-06
forum: General Help
---

### Post by SkippoGuangiacomo on 2009-05-06
Greetings! 
I got some weird message during my last update. I got some error which I was supposed to send to the KDE developers but I could not get the error. Now when I start the automatic updates I have a red-cross with a message that says 3 blocked updates. Any clue?

Best wishes

---

### Post by zvacet on 2009-05-07
```
sudo apt-get update && sudo apt-get upgrade
```

Post output here.

---

### Post by SkippoGuangiacomo on 2009-05-07
sudo apt-get update gives:
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty Release.gpg                                                                          
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty/main Translation-en_US                                                               
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty/restricted Translation-en_US                                                         
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty/universe Translation-en_US                                                           
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty/multiverse Translation-en_US                                                         
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates Release.gpg                                                                  
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates/main Translation-en_US
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates/restricted Translation-en_US
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates/universe Translation-en_US
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates/multiverse Translation-en_US
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security Release.gpg
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security/main Translation-en_US
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security/restricted Translation-en_US
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security/universe Translation-en_US
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security/multiverse Translation-en_US
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-proposed Release.gpg
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-proposed/restricted Translation-en_US
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-proposed/main Translation-en_US
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-proposed/multiverse Translation-en_US
Ign [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-proposed/universe Translation-en_US
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty Release
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates Release
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security Release
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-proposed Release
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty/main Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty/restricted Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty/main Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty/restricted Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty/universe Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty/universe Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty/multiverse Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty/multiverse Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates/main Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates/restricted Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates/main Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates/restricted Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates/universe Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates/universe Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates/multiverse Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-updates/multiverse Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security/main Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security/restricted Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security/main Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security/restricted Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security/universe Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security/universe Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security/multiverse Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-security/multiverse Sources
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-proposed/restricted Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-proposed/main Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-proposed/multiverse Packages
Hit [http://ftp.uni-kl.de](http://ftp.uni-kl.de) jaunty-proposed/universe Packages
Reading package lists... Done


whereas 'sudo apt-get upgrade' gives
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by zvacet on 2009-05-07
```
sudo apt-get dist-upgrade
```

---

### Post by SkippoGuangiacomo on 2009-05-09
That worked! Thank you very much zvacet!

Is there a way to say that this tread has been solved?

---

### Post by killabee44 on 2009-05-09
Just wanted to say that I also had been having this problem and this fixed it. Thanks.

---

### Post by mcb CH on 2009-05-18
This has been bugging me as well for the past 10 days - now resolved. Thank you!

---

### Post by wmtabada on 2009-05-18
I have problems updating the jaunty (Ubuntu 9.04).  The following errors occured when i did the updating:

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_PH.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_PH.bz2)  Could not resolve 'ph.archive.ubuntu.com'

I am using MSI Wind notebook.

---

### Post by zvacet on 2009-05-18
@ **wmtabada**

**System>admin>sotware sources>change server** and see if that helps.

---

### Post by skymera on 2009-05-18
> **wmtabada said:**
> I have problems updating the jaunty (Ubuntu 9.04).  The following errors occured when i did the updating:

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://ph.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'ph.archive.ubuntu.com'

W: Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_PH.bz2](http://ph.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_PH.bz2)  Could not resolve 'ph.archive.ubuntu.com'

I am using MSI Wind notebook.

Those lines shouldn't be in your sources.list, hence the errors.

---

