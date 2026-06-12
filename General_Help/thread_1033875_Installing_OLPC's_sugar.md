---
title: "Installing OLPC's sugar"
date: 2009-01-07
forum: General Help
---

### Post by jdelasalas on 2009-01-07
I just tried to install OLPC's sugar by adding this to my software sources:

deb [http://ppa.launchpad.net/sugarteam/ubuntu](http://ppa.launchpad.net/sugarteam/ubuntu) hardy main

when i follow the remainder of the instructures from [here]("http://sugarlabs.org/go/Community/Distributions/Ubuntu#Sugar_on_Ubuntu_8.10_.28intrepid.29"), I don't really accomplish much. When running sudo apt-get sugar sugar-emulator sugar-activities I get this boatload of missing dependencies:

~$ sudo apt-get install sugar sugar-emulator sugar-activities
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sugar: Depends: sugar-base but it is not going to be installed
         Depends: sugar-datastore but it is not going to be installed
         Depends: sugar-toolkit but it is not going to be installed
E: Broken packages


I'm just wondering if anyone has tried this and could shed any wisdom.

---

### Post by jdelasalas on 2009-01-07
Whenever I try to install anything, either through terminal or synaptic, I get some sort of error saying that it is dependent on a package and the dependency won't be installed.

---

