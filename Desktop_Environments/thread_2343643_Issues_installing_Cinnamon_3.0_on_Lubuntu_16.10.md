---
title: "Issues installing Cinnamon 3.0 on Lubuntu 16.10"
date: 2016-11-17
forum: Desktop Environments
---

### Post by Alex_Botelho on 2016-11-17
Currently trying to install Cinnamon 3.0 from embrosyn's repo, [https://launchpad.net/~embrosyn/+archive/ubuntu/cinnamon](https://launchpad.net/~embrosyn/+archive/ubuntu/cinnamon), on Lubuntu 16.10. I'm getting errors that I can't quite seem to solve myself, and I've spent enough time looking now to be comfortable about posting.
```

alex@alexUltraLin:~$ sudo add-apt-repository ppa:embrosyn/cinnamon
 This PPA contains unofficial (though probably closest to official) builds of Cinnamon releases for the latest two long-term (LTS) and short-term (STS) support releases, which currently means:
* Ubuntu 16.04, Xenial Xerus (xenial),
* Ubuntu 16.10, Yakkety Yak (yakkety).


New STS and LTS releases will supersede current releases, which will result in older releases no longer maintained.


Needless to say, I will do my best to build packages as timely as possible, but some lags are going to happen due to so-called "real-life obligations". Sorry for that. I despise them no less than you do :P


Xenial packages are tried and tested on my daily driver, but regardless, everything available here is provided "as is", without any warranty. It should NOT set your hard disk on fire or steal your puppies, but I can guarantee nothing.


Regarding Bluetooth: blueberry is the new Bluetooth configuration tool which replaces cinnamon-bluetooth. Users are strongly encouraged to use blueberry instead of the deprecated cinnamon-bluetooth package.


If you encounter some issues not documented on the official GitHub repositories (github.com/linuxmint), please let me know.


~ embrosyn
 More info: https://launchpad.net/~embrosyn/+archive/ubuntu/cinnamon
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keybox '/tmp/tmpasx9hop5/pubring.gpg' created
gpg: /tmp/tmpasx9hop5/trustdb.gpg: trustdb created
gpg: key EA1FE56966DFE684: public key "Launchpad PPA for embrosyn" imported
gpg: Total number processed: 1
gpg:               imported: 1
OK

```Seems all fine.

```
alex@alexUltraLin:~$ sudo apt update
Hit:1 http://security.ubuntu.com/ubuntu yakkety-security InRelease
Hit:2 http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu yakkety InRelease                
Hit:3 http://ca.archive.ubuntu.com/ubuntu yakkety InRelease                              
Hit:4 http://ca.archive.ubuntu.com/ubuntu yakkety-updates InRelease
Hit:5 http://ca.archive.ubuntu.com/ubuntu yakkety-backports InRelease
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.

```Again, seems all fine, yet:

```
alex@alexUltraLin:~$ sudo apt install cinnamon blueberry
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:


The following packages have unmet dependencies:
 cinnamon : Depends: cinnamon-screensaver (>= 3.2.0) but it is not going to be installed
            Depends: iso-flag-png but it is not installable
            Depends: gir1.2-xapp-1.0 but it is not installable
            Depends: xapps-common but it is not installable
            Recommends: gnome-themes-standard but it is not going to be installed
            Recommends: gnome-terminal
            Recommends: cinnamon-bluetooth but it is not installable
E: Unable to correct problems, you have held broken packages.

```
Obviously a dependency issues. But why would it not be able to install the appropriate packages? It seems to want to install cinnamon-bluetooth, which is deprecated in favor of blueberry?

Any ideas how how to resolve this? I'm willing to bet it's something absolutely simple/silly.

---

### Post by faure212 on 2017-05-09
I have the same problem (incurable unmet dependencies after the ppa and cinnamon installation), but cannot find an answer.  Sort of strange that no one seems to care or be able to help...

---

### Post by QIII on 2017-05-09
This is an old thread that was buried under the muck at the bottom of the sea for months.  It is less likely that nobody wanted to help than that the OP did not bother to bump the thread back up to the top.  A PPA is not official, the maintainer may walk away from it and it is not necessarily the case that anyone here would be able to help.

Please start your own thread describing your problem.  It may not be the same.

Closed.

---

