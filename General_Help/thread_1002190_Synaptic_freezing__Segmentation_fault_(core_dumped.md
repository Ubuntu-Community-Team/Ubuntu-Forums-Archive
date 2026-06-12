---
title: "Synaptic freezing / Segmentation fault (core dumped) with apt, aptitude apt-get, etc."
date: 2008-12-04
forum: General Help
---

### Post by csumm101 on 2008-12-04
I spent many long hours resolving this problem and thought I would wrap up the whole thing in one post instead of posting several posts in different forums.

I have a computer about 4 years old. Specs:

2.4GHZ intel p4
1.5GB RAM

It has 5 hard drives:
2 18GB SCSI
1 60GB IDE
1 20GB IDE
1 500GB SATA

I installed Ubuntu 6.10 last year and it ran fine. I didn't do much on it and haven't upgraded it regularly. I decided I wanted to upgrade to 8.10, but instead of doing step-by-step upgrade I downloaded Ubuntu 8.10 ISO and burned it to disk. I then attempted to start fresh by formatting the partition (a 7 GB partition on my 20GB drive) and going from there.
It turns out that the manual disk partitioner on the new Ubuntu would not work with my system. The old 6.10 installer worked fine. After long hours I decided to reinstall my 6.10 and start from there.
After reinstalling, it wouldn't upgrade to 7.04 because 6.10 is no longer supported. After long and painstaking searches I found a way to upgrade to 7.04, so I did. That wasn't all. I wanted to install music production programs like rosegarden and video applications like kino so i downloaded and installed all i could find along the audio/video line.
somewhere down the line i noticed that my synaptic froze! and the hard drive kept running! i waited for a long time, after which i decided to power off.
upon restarting synaptic still wouldn't start fully. the window would come up and then just as the packages are loading it would freeze.
i then decided to try it from the shell. i tried upgrading using apt-get upgrade. it showed an error "Segmentation fault (core dumped)" I tried starting up in recovery mode. any apt-like command i used ended with a segmentation fault. in recovery mode it said "segmentation faultsts"
i searched the internet extensively and tried everything until finally i found the solution... here it is (hopefully it will save you much time and headaches)...

Open a terminal (if you are running gnome click on the applications menu, then accessories...terminal.. type:

sudo gedit

when the file editor appears, open the file named 20arhive found in /ect/apt/apt.conf.d/20archive
add the following to the end of the file:

APT::Cache-Limit "20000000";

Save the file.

Viola! your problem is fixed. Synaptic should work, and no more segmentation faults with apt

---

