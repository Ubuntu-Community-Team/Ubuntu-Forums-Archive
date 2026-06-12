---
title: "Changing where Synaptic installs to?"
date: 2005-12-18
forum: General Help
---

### Post by barebones on 2005-12-18
Hello all,
My father decided to install linux on an old computer, and luckily he chose to use Ubuntu (which I am fairly familier with). However, he decided to use two small harddrives to install on (one just under 5 gigs and the other about 13 gigs) with the smallest one being the root drive. The small drive is full already (I had to boot in failsafe mode and clean up some stuff just to get gnome to start) and I would like to install future programs on the other, larger hard drive. I realize that the .debs that synaptic uses determin where the files go, and not synaptic itself, but can I at least tell it which drive to send them to? Is there any sort of config file that determins which drive that synaptic targets? Any sort of help would be greatly appreciated.

---

### Post by 23meg on 2005-12-19
As you've figured out, install locations in the directory tree are fixed in package files; all you can do is have partitions for these fixed locations in different physical drives. For example you can create a /bin partition in your drive with a lot of empty space so that application installed binaries will go there. You normally create partitions for different folders at install time, though you should be able to create new partitions with the parted program and move your files from your current installation there as well. I haven't done this myself; I create all partitions at install time and stick to them, so there may be some pitfalls you have to avoid that I don't know of. 

Take a look at this, which may clear some confusion: 

[http://www.builderau.com.au/program/work/soa/10_things_you_should_know_about_every_Linux_installation/0,39024650,39219801,00.htm](http://www.builderau.com.au/program/work/soa/10_things_you_should_know_about_every_Linux_installation/0,39024650,39219801,00.htm)

---

### Post by barebones on 2005-12-19
Thanks for you help 23meg

I'm still a bit confused about what to do though, even after looking at that article. I'm more confused about what synaptic will do, I guess, than the actual file system. How does synaptic know which partition to look at? It seems like just creating a /bin directory on the second hard drive won't do anything because synaptic is already using the one on the first hard drive. Should I move the old /bin in its entirity to the second hard drive, and eliminate the first /bin? Are there any settings that need to be changed?

---

