---
title: "Synaptic Package Manager error"
date: 2005-03-08
forum: Desktop Environments
---

### Post by Caesar on 2005-03-08
Hello,
after the last update i get this error every time i install something new:

```

E: postfix:  subprocess post-installation script returned error exit status 1
E: at:  dependency problems - leaving unconfigured
E: postfix-dev:  dependency problems - leaving unconfigured
E: postfix-tls:  dependency problems - leaving unconfigured
E: ubuntu-base:  dependency problems - leaving unconfigured

```

How to fix those dependancy problems?
I've tried to reinstall those packages... but no way :(


TIA  [-o<

---

### Post by lao_V on 2005-03-08
what is in your repository? have you tried to install those packages from synaptic?

---

### Post by Caesar on 2005-03-08
This is my full repository list:

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Alpha powerpc Binary-1 (20050204)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
## deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
## deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

## deb http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/ mplayer/

deb http://apt.cerkinfo.be/ unstable main contrib non-free
deb-src http://apt.cerkinfo.be/ unstable main contrib non-free
``` 


I can't copy&paste the full error log after the installation of new packages with Synaptic but the errors are reported alwyas for postfix/at/postfix-dev/postfix-tls/ubuntu-base. Do you know if there is a log file somewhere?

---

