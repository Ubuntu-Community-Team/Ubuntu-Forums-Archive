---
title: "Change ubiquity release name"
date: 2011-01-09
forum: Development CD/DVD Image Testing
---

### Post by n~kf)}BW% on 2011-01-09
Hello,

I'm creating a custom Ubuntu live cd.

How can i change the release name in ubiquity? (For example, where it says "Try Ubuntu" - "Install Ubuntu"

PS: casper.conf doesn't do the job

---

### Post by Happy Frog on 2011-03-23
Hi,

I'm in the process of creating a custom distro myself and have been searching for help with this. It uses the ${RELEASE} variable for the distribution name so set that.

Having said that I'm having issues with it :) so I'll post again when I've resolved it.

---

### Post by Happy Frog on 2011-03-23
There's a hidden directory on the CD (or whatever) that has the release info in it.

Look in the root of the media for a **.disk** directory, and in there is a file called **info** , if you edit that it will be used throughout ubiquity.

---

