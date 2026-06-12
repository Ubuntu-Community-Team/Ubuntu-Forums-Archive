---
title: "Prey install lost desktop"
date: 2015-10-02
forum: Desktop Environments
---

### Post by SMButler on 2015-10-02
Attempted to install latest version of Prey from [https://preyproject.com/download](https://preyproject.com/download) for Ubuntu/Debian ([https://prey-releases.s3.amazonaws.com/node-client/1.4.1/prey_1.4.1_i386.deb](https://prey-releases.s3.amazonaws.com/node-client/1.4.1/prey_1.4.1_i386.deb)).

Install warned about sudo, python and several other packages.  After reboot, system boots to login page.  Login produces a blank screen (well almost blank -- I see 15.04 in the lower right hand side).  The only thing that works is CNTL/ALT/F1.  I'm able to login on the hard terminal screen -- but all attempts to recover desktop have failed.  I'm afraid that I'm in too deep now.  Is there a way to get back to a solid 15.04 without losing my documents/email/etc?

PS.  Right now getting my email on my Android phone.

---

### Post by claracc on 2015-10-04
As you can log in into console mode by means of ctrl+alt+f1 you can try to uninstall the culprit package":

```
sudo apt-get remove --purge "name of package"
```

Then you can run the following commands:

```
sudo apt-get autoremove
```

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

In order to get rid off packages that you don't need anymore. If lucky perhaps
you can recover the previous situation before the installation of Prey

---

