---
title: "Trouble installing R on Ubuntu"
date: 2011-10-01
forum: Education &amp; Science
---

### Post by Axolotl9250 on 2011-10-01
Hi there, I've installed R on Ubuntu many times before without a hitch, but when I wanted to put it on a new install, I followed CRAN instructions, added the source to my repository list and updated apt-get, and set up the gpg key. However upon issuing the command ```
sudo apt-get install r-base
``` I get the following message, which seems to be about dependencies:
```
ome packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 r-base : Depends: r-base-core (>= 2.13.1-1natty2) but it is not going to be installed
          Depends: r-recommended (= 2.13.1-1natty2) but it is not going to be installed
          Recommends: r-base-html but it is not going to be installed
E: Broken packages

```

Ok says I, I'll try this: 
```
sudo apt-get install r-base-core r-recommended r-base-html

```
But still no luck as it returns: 
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 r-base-core : Depends: libblas3gf but it is not installable or
                        libblas.so.3gf but it is not installable or
                        libatlas3gf-base but it is not installable
               Depends: libgfortran3 (>= 4.3) but it is not installable
               Depends: liblapack3gf but it is not installable or
                        liblapack.so.3gf but it is not installable or
                        libatlas3gf-base but it is not installable
               Depends: tcl8.5 (>= 8.5.0) but it is not installable
               Depends: tk8.5 (>= 8.5.0) but it is not installable
               Recommends: r-base-dev but it is not going to be installed
 r-recommended : Depends: r-cran-cluster (>= 1.9.6-2) but it is not going to be installed
                 Depends: r-cran-kernsmooth (>= 2.2.14) but it is not going to be installed
                 Depends: r-cran-mgcv (>= 1.1.5) but it is not going to be installed
                 Depends: r-cran-matrix but it is not going to be installed
E: Broken packages

``` 
And so on and so on, I specify the deps manually in the command and it just throws more out at me, I've tried using the Synaptic Package Manager too and the same thing happens. Has anyone else experienced this or knows the problem?

Thanks, in advance, Ben W.

---

### Post by sanderd17 on 2011-10-01
first try
```

sudo apt-get update
sudo apt-get upgrade

```

And post all error messages.

If you get no error messages, try with aptitude:

```

sudo apt-get install aptitude
sudo aptitude install r-base

```

---

### Post by Axolotl9250 on 2011-10-01
I received no messages doing the apt-get upgrade.

Upon using apt-get to install aptitude it returned:
```
Package aptitude is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'aptitude' has no installation candidate
```

Thanks, Ben W.

---

### Post by sanderd17 on 2011-10-01
Do you have an internet connection? 
What version of Ubuntu are you using?
Are you able to install any other program?
Can I see the output of the first two commands, even if they don't have error messages?

---

### Post by PC_load_letter on 2011-10-04
> **sanderd17 said:**
> Do you have an internet connection? 
What version of Ubuntu are you using?
Are you able to install any other program?
Can I see the output of the first two commands, even if they don't have error messages?

What he said, I didn't have a single issue installing R from Synaptic on any of my laptops, zelch.

---

