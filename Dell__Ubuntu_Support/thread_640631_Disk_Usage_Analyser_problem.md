---
title: "Disk Usage Analyser problem"
date: 2007-12-14
forum: Dell  Ubuntu Support
---

### Post by Threlkeld on 2007-12-14
As will become clear, I'm inexperienced and confused.
I'm running Ubuntu 7.04 on an Inspiron 6400 which I've had for a couple of months. The partitioning is 'as delivered' from Dell. All I've done is installed applications, the largest of which is probably Google Earth.
The Disk Usage Analyser gives (on scan Filesystem):
Total filesystem capacity 52.3 GB
Used: 38.4 GB
Available: 14 GB
However, the 'Usage' column in the analysis gives, for the '/' directory, 12GB, and indeed the sum of the subdirectories seems to add up to this value.
Clearly, I'm not understanding this properly, because there seem to be about 26.4 GB of files that I can't list.
Where should I be looking for them, or has the system lost track of a large chunk of HDD space?
du -c -h gives a total of 8.2G, which I can't relate to any of the above numbers.

---

### Post by Threlkeld on 2007-12-14
PS
du -c -h  gives 12G when I remember to change to the root directory first
:-)

---

### Post by Threlkeld on 2007-12-18
The machine is reporting less and less free memory as days go by, although I'm not installing new applications. The Disk Usage Analyser only reports 12 GB of files when it lists them, but in the toolbar at the same time now claims that 44.9 GB of disk space is occupied.
I am now wondering if disk space is becoming unavailable when I suspend or hibernate? When scanning, the Disk Usage Analyser spens a lot of time looking at the /usr folder, but only returns 3.1 GB (9 items).

HELP!!

---

