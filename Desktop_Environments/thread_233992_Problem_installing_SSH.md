---
title: "Problem installing SSH"
date: 2006-08-10
forum: Desktop Environments
---

### Post by CUBANb95 on 2006-08-10
Im tryin to setup ssh for my ubuntu box and im getting this error when trying to install:

 * Restarting OpenBSD Secure Shell server... /etc/ssh/sshd_config: line 61: Bad configuration option: GSSAPINoMICAuthentication
/etc/ssh/sshd_config: terminating, 1 bad configuration options
invoke-rc.d: initscript ssh, action "restart" failed.
dpkg: error processing openssh-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openssh-server
 ssh
E: Sub-process /usr/bin/dpkg returned an error code (1)

The command I am using is: sudo apt-get install ssh
Can anyone tell me whats going on or how to fix it. Thank you in advance im pulling my hair out trying to install this.

---

### Post by wieman01 on 2006-08-10
Try to use Synaptic and install "open-ssh". That should resolve your "dependency" problem which I had before. "open-ssh" should run like a charm. :-)

---

### Post by CUBANb95 on 2006-08-10
Thats actually the first way I tried to install it but same message  comes up im not sure exactly what the problem is when I had brezzy i installed openssh like it was nothing.
Thanks for posting though

---

### Post by murataht on 2006-08-10
it seems that the configuration file has some problem...

there is just a tip, i don't know if it will work or not. try it with your own risk...

i installed ssh on my breezy server. and it had no problem. and when dapper out, i updated it with no problem. so why not try the package from breezy first. if it installs, then upgrade it to dapper version. here i am just talking about a single package, not a whole system. hope it helps. let us know if it works or not.

---

### Post by nofool on 2006-08-10
Unless you are really using GSSAPI, then edit the /etc/ssh/sshd_config file and put hashes in front of the following lines.

```
# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

```

By default both Kerberos and GSSAPI are off.

Hope that helps. Oh...and if you are still planning to reinstall to correct this, you may want to do a purge instead of just a reinstall. That will insure your config files get replaced.

Good-Luck

---

### Post by CUBANb95 on 2006-08-10
> **nofool said:**
> Unless you are really using GSSAPI, then edit the /etc/ssh/sshd_config file and put hashes in front of the following lines.

```
# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

```

By default both Kerberos and GSSAPI are off.

Hope that helps. Oh...and if you are still planning to reinstall to correct this, you may want to do a purge instead of just a reinstall. That will insure your config files get replaced.

Good-Luck
Yea I did realize the config file was messed up, it seems there is just instructions in the config but I will try your method nofool. Thank you all for the reply's

---

### Post by bonjun on 2006-08-10
maybe you can try fixing your ssh installation

> sudo apt-get install --fix-missing ssh

hope this work...

---

### Post by CUBANb95 on 2006-08-10
Thank you no fool I reinstalled and the package was installed successfully. I appricate the help good lookin out. Thank you all for reply's

---

