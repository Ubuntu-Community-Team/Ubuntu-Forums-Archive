---
title: "Extremely High Memory Usage"
date: 2005-03-19
forum: Desktop Environments
---

### Post by spartas on 2005-03-19
On my Hoary upgraded (I did not install the preview release from the CD; only upgraded 4.10 to 5.04 through apt-get) system I have extremely high memory usage.  Often throughout the day I will have many firefox tabs, thunderbird, gaim and a terminal window open.  I used to have 384Mb of RAM until I noticed ubuntu was gnawing at it until it started using my swap space.  I bought a 512Mb module and now I have 768Mb (only 2 RAM slots in my laptop), and top tells me that ubuntu is using about 95% of the 768Mb (737988/776360) as well as swap space.  

The important thing to note is that while gnome and my background processes are running, nothing that is running is very CPU intensive (0.3% CPU usage), and I don't have any windows open right now, not even terminal (I'm SSHed into the box).

This appears to build up, but it looks like no memory is being given back to the system (unallocated).  Can anyone tell me where the memory leak/resource hog is and if they're experiencing a similar situation (especially if you're running Hoary, but not from the PR CD).

---

### Post by Joeb on 2005-03-19
I think it's normal for Linux to report high memory usuage.  It's going to keep things cached as long as the memory isn't needed for something else at which point it allocates it for the something else.  Are you saying that you have a high memory usuage and a high swap usuage both?  If memory usuage is high and swap low, then I believe that is normal (if not, I'm sure someone will correct me).

Joeb


ps for comparison, top show my memory usuage at 506MB out of 512MB but swap is less than 2MB.  If I open a bunch more apps, that usuage stays about the same.

---

### Post by DJ_Max on 2005-03-19
As long as everyones updated, regardless if they have used Array -5 or the Preview, they are on the same boat as you. You have the NT mentallity regarding ram usage. Stop worrying so much about the memory, They work different depending on the OS,
Linux will free up cache memory as other tasks require it.  It dumps all 'free' memory toward disk cache.

The more ram you buy, the more thats going to be used, thats what it's there for. Having a high mem% is normal, worry when your swap is high.

---

### Post by emuman on 2005-03-21
Try 
'free -m'
in a terminal window. Let's say you have the following output:
                  total      used      free     shared    buffers     cached
Mem:          1012     625        387     0            44           332
-/+ buffers/cache:    248        763
Swap:         1027          0      1027

It says we have 387 Mb free physical space. Free space for your application is 763 Mb, because 332 Mb is used for cache and 44 Mb for buffers. Linux will release the cache and buffer if an application needs the memory.

---

