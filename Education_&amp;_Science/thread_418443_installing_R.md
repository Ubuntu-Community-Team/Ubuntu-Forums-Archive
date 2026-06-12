---
title: "installing R"
date: 2007-04-22
forum: Education &amp; Science
---

### Post by merlin666 on 2007-04-22
I had R installed in edgy but could not update. The problem may be that some of the required packages come from canonical ubuntu repositories while most R packages are on CRAN servers. I finally unistalled everything and tried again, and now I can'r get anything to work anymore related to R. Specifically the following happens:

rolf@ubuntu:~$ sudo apt-get install r-base r-recommended
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:rolf@ubuntu:~$ sudo apt-get install r-base r-recommended
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.rolf@ubuntu:~$ sudo apt-get install r-base r-recommended
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  r-base: Depends: r-base-core (>= 2.4.1-1edgy0) but 2.3.1-1 is to be installed
  r-recommended: Depends: r-base-core (>= 2.4.1-1edgy0) but 2.3.1-1 is to be installed
                 Depends: r-cran-boot (>= 1.2.19) but it is not going to be installed
E: Broken packages

The following information may help resolve the situation:

The following packages have unmet dependencies:
  r-base: Depends: r-base-core (>= 2.4.1-1edgy0) but 2.3.1-1 is to be installed
  r-recommended: Depends: r-base-core (>= 2.4.1-1edgy0) but 2.3.1-1 is to be installed
                 Depends: r-cran-boot (>= 1.2.19) but it is not going to be installed
E: Broken packages

  r-base: Depends: r-base-core (>= 2.4.1-1edgy0) but 2.3.1-1 is to be installed
  r-recommended: Depends: r-base-core (>= 2.4.1-1edgy0) but 2.3.1-1 is to be installed
                 Depends: r-cran-boot (>= 1.2.19) but it is not going to be installed
E: Broken packages


I.e. the 2.3.1 version of r-base-core comes from ubuntu and is so out of date that the rest can not be installed. I really would like to find a solution for this.

---

### Post by forcotton on 2007-04-22
what repositories are you using? It looks like a problem in your /etc/apt/sources.list , maybe you have both edgy and feisty repositories?

---

### Post by akniss on 2007-04-22
> **forcotton said:**
> what repositories are you using? It looks like a problem in your /etc/apt/sources.list , maybe you have both edgy and feisty repositories?

I agree... post a copy of your current sources.list.  It appears as though you've used an external repository (probably a CRAN mirror) to get 2.4.1 installed at some point.

---

### Post by merlin666 on 2007-04-23
> **akniss said:**
> I agree... post a copy of your current sources.list.  It appears as though you've used an external repository (probably a CRAN mirror) to get 2.4.1 installed at some point.

I have inserted the canadian CRAN mirrors. What is a good repo to get R?

---

### Post by sgsong on 2007-04-23
I had the same problem. Then I decided to uninstall the binary and install from the source. It seems to working well.

---

### Post by akniss on 2007-04-23
> **merlin666 said:**
> I have inserted the canadian CRAN mirrors. What is a good repo to get R?

The best repos to get R is the Ubuntu repos.  Its in there.  The only reason you should need to use a CRAN mirror is if you absolutely need the most up-to-date version.  (for new packages that depend on the latest version, bug-troubleshooting, etc.)

---

### Post by merlin666 on 2007-04-24
Thank, you that was easy enough and worked fine in Edgy. Is it also in the Feisty repositories?

---

### Post by akniss on 2007-04-24
> **merlin666 said:**
> Thank, you that was easy enough and worked fine in Edgy. Is it also in the Feisty repositories?

Yep.  It is also in the Feisty repos.  Feisty even has the latest version (2.4.1).

---

