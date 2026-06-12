---
title: "Knights Installed on Ubuntu 10.10"
date: 2011-01-17
forum: Gaming &amp; Leisure
---

### Post by apollothethird on 2011-01-17
Is anyone able to install the chess program, Knights, on Ubuntu 10.10 or Kubuntu 10.10?  I have Ubuntu 10.10 64 bit installed on my main computer.  I couldn't get it to install.

I then installed Kubuntu 10.10 64 on one of my other computers and still can't get Knights installed.

I get lots of errors that are similar to:

```
$ sudo apt-get install knights
[sudo] password for ljames:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 knights : Depends: kdebase-kio-plugins but it is not going to be installed
E: Broken packages
----------------------------------------------------
$ sudo apt-get install kdebase-kio-plugins
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 kdebase-kio-plugins : Depends: kdelibs4c2a (>= 4:3.5.8-1) but it is not going to be installed
                       Depends: kdesktop but it is not going to be installed
                       Recommends: kdemultimedia-kio-plugins but it is not going to be installed
E: Broken packages
```

Thanks in advance for any comments on anybody's experience, especially success with this combination.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

