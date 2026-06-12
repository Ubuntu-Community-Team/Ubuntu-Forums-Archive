---
title: "awesome instantly crashes"
date: 2009-02-24
forum: General Help
---

### Post by dbbolton on 2009-02-24
Awesome immediately crashes when I try to log into an awesome session or if I try to launch it from a shell. I am using the version from the Intrepid repositories:

```

apt-cache policy awesome
awesome:
  Installed: 2.3.2-1
  Candidate: 2.3.2-1
  Version table:
 *** 2.3.2-1 0
        500 http://us.archive.ubuntu.com intrepid/universe Packages
        100 /var/lib/dpkg/status

==================

apt-cache policy libconfuse0
libconfuse0:
  Installed: 2.6-2
  Candidate: 2.6-2
  Version table:
 *** 2.6-2 0
        500 http://us.archive.ubuntu.com intrepid/universe Packages
        100 /var/lib/dpkg/status


```

Here is the output of launching awesome from the shell:

```

W: awesome: xerror:139: fatal error: request code=1, error code=2
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  1 (X_CreateWindow)
  Value in failed request:  0x0
  Serial number of failed request:  151
  Current serial number in output stream:  462

```

Any suggestions?

---

### Post by dbbolton on 2009-02-24
I just googled part of the output and found this: [http://awesome.naquadah.org/bugs/index.php?do=details&task_id=347](http://awesome.naquadah.org/bugs/index.php?do=details&task_id=347)

There the 'ati' driver was mentioned. I am using the fglrx driver.

---

### Post by dbbolton on 2009-02-25
Since no one seems to know why this is happening, I filed a bug report:

[https://bugs.launchpad.net/bugs/334106](https://bugs.launchpad.net/bugs/334106)

---

