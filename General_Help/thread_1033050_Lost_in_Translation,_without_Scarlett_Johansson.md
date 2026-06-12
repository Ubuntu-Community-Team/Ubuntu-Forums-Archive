---
title: "Lost in Translation, without Scarlett Johansson"
date: 2009-01-06
forum: General Help
---

### Post by IKhider on 2009-01-06
Hello All, 

I am still trying to install Skype on my AMD 64 bit processor machine and get the following error messages:

"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
skype: Depends: skype-common (= 2.0.0.72-0medibuntu1) but 2.0.0.72-0medibuntu4 is to be installed
E: Broken packages"


Alternately, when I used Synaptic I got this after an "unresolvable dependency":

"skype: Depends: skype-common (=2.0.0.72-0medibuntu1) but 2.0.0.72-0medibuntu4 is to be installed"


These above messages are in the computer-ese language. Can someone translate the above? Does it mean that the problem is my machine and not Ubuntu repositories? Or the problem are the Ubuntu repositories and not my machine, or both? Or none at all?

Oh yeah, I am using hardy heron, folks.

-I-

---

### Post by hwttdz on 2009-01-07
It looks like a dependencies problem.  I'd recommend removing all skype packages (purge, or remove completely from synaptic and trying again).  It seems like you tried to get half your packages from one source and half from another.  Let us know how purging and retrying goes.  

On a side note I've never gotten skype to work very well in linux at all, and even less so in linux 64.  Though I can't suggest a great alternative.

---

### Post by mali2297 on 2009-01-07
You could try installing it with aptitude. From the command line:
```

sudo aptitude install skype

```
aptitude is sometimes better at resolving dependencies.

---

