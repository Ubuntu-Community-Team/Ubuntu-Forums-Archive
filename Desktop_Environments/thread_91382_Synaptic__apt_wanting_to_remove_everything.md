---
title: "Synaptic / apt wanting to remove everything"
date: 2005-11-17
forum: Desktop Environments
---

### Post by darkstarshadow on 2005-11-17
Yea, so when I go to intsall ANYTHING or remove anything it says it whants to remove basically everything.

 sudo apt-get dist-upgrade Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  cpp-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-3 is installed
  g++-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-3 is installed
  gcc-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-3 is installed
  gij-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-3 is installed
  libgcj6: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-3 is installed
  libstdc++6-4.0-dev: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-3 is installed
E: Unmet dependencies. Try using -f.

and if i go to just apt-get install
sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cpp-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-3 is to be installed
  g++-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-3 is to be installed
  gcc-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-3 is to be installed
  gij-4.0: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-3 is to be installed
  libgcj6: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-3 is to be installed
  libstdc++6-4.0-dev: Depends: gcc-4.0-base (= 4.0.1-4ubuntu9) but 4.0.2-3 is to be installed
  mplayer-386: Depends: libdirectfb-0.9-22 but it is not going to be installed
               Depends: libfaad2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not going to be installed
               Depends: libggi2 (>= 1:2.0.5) but it is not going to be installed               Depends: libjack0.80.0-0 (>= 0.99.0) but it is not going to be installed
               Depends: libmad0 (>= 0.15.1b) but it is not going to be installed               Depends: libpolyp0 but it is not going to be installed
               Depends: libsvga1 but it is not going to be installed or
                        svgalib-dummyg1 but it is not installable
               Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

and then as i siad if im in synaptic its all like wanting to remove everything any suggestions ? need more info ? what ?

---

### Post by Miguel on 2005-11-17
I guess you have repositories other than the ubuntu ones enabled in your sources.list. Especially since 4.0.1 is the GCC version that shipped with ubuntu breezy (this is EXTREMELY unlikely to change).

In the case you are using backports, I suggest disabling them (at least momentarily) to see what the problem is. If you have installed gcc 4.0.2 from another repository, disabling this one should help.

---

