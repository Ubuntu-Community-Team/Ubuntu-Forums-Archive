---
title: "Error message in terminal"
date: 2005-12-27
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-12-27
When trying to install lilypond I go the following

```
gabriel@ubuntu:~$ sudo apt-get install lilypond
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lilypond: Depends: lilypond-data (= 2.2.6-2) but 2.6.3-9 is to be installed
E: Broken packages
gabriel@ubuntu:~$
```

What happened there? What's missing for installation, and why is that package not simply re-installed, if broken?

G

---

### Post by art on 2005-12-27
You could install lilypond-data 2.6.3-9 from 

[http://packages.debian.org/unstable/tex/lilypond-data](http://packages.debian.org/unstable/tex/lilypond-data)

and then run sudo apt-get install lilypond, and see what happens. What's missing is that you need a newer version of lilypond-data to get lilypond to work. 
HTH

---

### Post by kaamos on 2005-12-27
I think 2.6.3-9 is exactly what ubuntu would install. However the version needed seems to be 2.2.6-2

Or did I get to output wrong?

EDIT: If I'm right, then opening synaptic and forcing the install on 2.2.6-2 and then doing "apt-get install lilypond" should do the trick.

---

### Post by art on 2005-12-27
Ooops, you are right, my bad... I read it wrong. It's here

[ftp://ftp.ubuntulinux.org/ubuntu/pool/universe/l/lilypond/lilypond-data_2.2.6-2_all.deb](ftp://ftp.ubuntulinux.org/ubuntu/pool/universe/l/lilypond/lilypond-data_2.2.6-2_all.deb)

they are actually Warty packages.

---

### Post by art on 2005-12-27
Actually one could get even a newer version, on [http://www.lilypond.org/web/install/#2.6](http://www.lilypond.org/web/install/#2.6).

---

