---
title: "Fedora Repository"
date: 2008-12-28
forum: Fedora/RedHat and derivatives
---

### Post by danmpem on 2008-12-28
Okay, really stinking easy question.  I'm running the latest Fedora Cora on one of my computers.  For some reason, only installed packages are appearing on my Synaptic Package Manager.  The options I am used to using on my Ubuntu system are not present.  How can I get SPM to show me all packages in the repo?

Thanks!

---

### Post by igknighted on 2008-12-28
How did you get synaptic?  Did you switch your repo's to apt4rpm repo's in the process?  Also, Fedora Core is ancient, it is likely that the repo's are no longer online, or have moved.  Try Fedora as a replacement now, version 10 is current.

---

### Post by gettinoriginal on 2008-12-28
[http://rh-mirror.linux.iastate.edu/fedora-core/](http://rh-mirror.linux.iastate.edu/fedora-core/)
[http://fedoraproject.org/wiki/YumUpgradeFaq](http://fedoraproject.org/wiki/YumUpgradeFaq)

---

### Post by danmpem on 2008-12-29
> **igknighted said:**
> How did you get synaptic?  Did you switch your repo's to apt4rpm repo's in the process?  Also, Fedora Core is ancient, it is likely that the repo's are no longer online, or have moved.  Try Fedora as a replacement now, version 10 is current.

Hmm...i'm not a big fefora user, mostly Ubuntu and Debian.  I'm using the latest version of Fedora period.

---

### Post by igknighted on 2008-12-29
> **danmpem said:**
> Hmm...i'm not a big fefora user, mostly Ubuntu and Debian.  I'm using the latest version of Fedora period.

Ok, sorry... i read "latest" as "last".  FWIW, Fedora Core ended at version 6.  From 7 onward, it is known only as Fedora.

But on to your issues.  Synaptic is not an application you can get on Fedora without some work.  It also cannot use the default Fedora repo's.

Try opening a terminal and typing 'su -' to become root (password will be required), and the 'yum update' after that.  Hopefully it will try to update a bunch of stuff.  You can hit ctrl+c to cancel it, what matters more is if it sees anything to update.

---

### Post by danmpem on 2008-12-29
> **igknighted said:**
> Ok, sorry... i read "latest" as "last".  FWIW, Fedora Core ended at version 6.  From 7 onward, it is known only as Fedora.

But on to your issues.  Synaptic is not an application you can get on Fedora without some work.  It also cannot use the default Fedora repo's.

Try opening a terminal and typing 'su -' to become root (password will be required), and the 'yum update' after that.  Hopefully it will try to update a bunch of stuff.  You can hit ctrl+c to cancel it, what matters more is if it sees anything to update.

Yeah I don't remember if I installed SPM or if it came with Fedora, but I definitely know that if I installed it, it had to have been from the Fedora repo, because I didn't compile it.  Is there any other package manager with a gui for fedora?

---

### Post by Antman on 2008-12-29
> **danmpem said:**
> Is there any other package manager with a gui for fedora?
Fedora systems include a graphical interface to yum, which appears on the Main Menu under Applications > Add/Remove Software.
Or you can install yumex and use that instead:
```
su -c 'yum install yumex'
```

---

### Post by danmpem on 2008-12-29
Awesome.  Thanks!

---

