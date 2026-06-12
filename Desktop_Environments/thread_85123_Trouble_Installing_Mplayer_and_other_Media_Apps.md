---
title: "Trouble Installing Mplayer and other Media Apps"
date: 2005-11-01
forum: Desktop Environments
---

### Post by hzs202 on 2005-11-01
Hello All,

I have been trying to install mplayer, realplayer and other media plugins for Mozilla Firefox. Apparently these apps depend on a libc6 file that is nolonger supported or possibly a backport. Below is what I have done so far and I am wondering if someone could steer me in the right direction to install these items.```

sudo apt-get install mplayer-386
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
  mplayer-386: Depends: libaa1 (>= 1.2) but it is not installable
               Depends: libartsc0 (>= 1.4.2-1) but 1.4.0-0pre1ubuntu3 is to be installed
               Depends: libasound2 (> 1.0.9) but 1.0.8-1 is to be installed
               Depends: libavcodeccvs (>= 3:20051016-0.0) but it is not going to be installed
               Depends: libc6 (>= 2.3.5-1) but 2.3.2.ds1-20ubuntu14 is to be installed
               Depends: libdirectfb-0.9-22 but it is not installable
               Depends: libfaac0 (>= 1.24-0.4) but it is not going to be installed
               Depends: libfaad2-0 (>= 2.0.0-0.7) but it is not going to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libfribidi0 (>= 0.10.5-4) but 0.10.4-6 is to be installed
               Depends: libgcc1 (>= 1:4.0.1) but 1:4.0-0pre6ubuntu7 is to be installed
               Depends: libglib2.0-0 (>= 2.8.0) but 2.6.3-1 is to be installed
               Depends: libjack0.100.0-0 (>= 0.100.0) but it is not installable
               Depends: libncurses5 (>= 5.4-5) but 5.4-4 is to be installed
               Depends: libpango1.0-0 (>= 1.8.2) but 1.8.1-0ubuntu2 is to be installed
               Depends: libpostproccvs0 (>= 3:20051016-0.0) but it is not going to be installed
               Depends: libslang2 (>= 2.0.1-1) but it is not installable
               Depends: libstdc++6 (>= 4.0.2) but it is not going to be installed
               Depends: libvorbis0a (>= 1.1.0) but 1.0.1-1 is to be installed
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
E: Broken packages
```

Please help me out here?

---

### Post by teaker1s on 2005-11-01
I've tried three of your missing dependancies synaptic advanced refresh and search but leave version number off eg. libc
also if you use synaptic and configure it to also install dependancies and search and install mplayer it will save you all the apg-get stuff

---

