---
title: "twinkle on edgy broken?!"
date: 2006-10-02
forum: Desktop Environments
---

### Post by stani on 2006-10-02
Hi,
Is anyone able to set up twinkle on Edgy? I get a broken dependency error.

```
stani@blue:~$ sudo apt-get install twinkle
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  twinkle: Depends: libccrtp1-1.4-0 but it is not going to be installed
E: Broken packages

```

Should I file a bug report?

Stani

---

### Post by c4r1 on 2006-10-04
same problem here.
please fill a bug report.

---

### Post by Ramses de Norre on 2006-10-04
I'd try the [edgy](http://www.ubuntuforums.org/forumdisplay.php?f=144) section of the forums first.

---

### Post by c4r1 on 2006-10-05
seems now to be fixed

---

