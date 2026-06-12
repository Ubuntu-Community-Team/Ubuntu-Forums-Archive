---
title: "problem installing R - lucid on a powerpc ibook"
date: 2010-09-20
forum: Education &amp; Science
---

### Post by bigturko@yahoo.com on 2010-09-20
Hi everybody, 

I'm a very new ubuntu user (5 hours?), so I apologize if this has an obvious solution...

I need to use R statistical software. Following the instructions of their site, I added an entry like 
 deb [http://<my.favorite.cran.mirror>/bin/linux/ubuntu]("http://%3cmy.favorite.cran.mirror%3e/bin/linux/ubuntu") lucid/

to my etc/apt/sources.list file, having replaced <my fave mirror> with the 
URL of a real mirror. Then, in a terminal, I typed

sudo apt-get update
sudo apt-get install r-base 

And got the following info:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  r-base: Depends: r-base-core (>= 2.11.1-5lucid0) but 2.10.1-2 is to be installed
          Depends: r-recommended (= 2.11.1-5lucid0) but it is not going to be installed
E: Broken packages


I'm using Lucid Lynx on a PowerPC iBook G4 from 2005. 

Any idea how to solve this? Any help would be greatly appreciated!
:guitar:

---

