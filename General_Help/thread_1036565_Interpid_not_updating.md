---
title: "Interpid not updating?"
date: 2009-01-10
forum: General Help
---

### Post by SidewinderX on 2009-01-10
The past few days I have been experimenting with different distros since 7.04 was giving me some memory problems. In the past 48 hours I have tried Fedora, Sabayon, Kubuntu, and now I'm back to Ubuntu 7.10 (feels good to be back home :P)

Anyway, after a fresh install of any operating system I always do the updates / upgrades. So I ran ```
sudo apt-get update
``` and it took a little longer than I had expected, but once that was done I did ```
sudo apt-get upgrade
``` and let it run while I watched ate supper and watched a movie, I come back 3 hours later and its still not done. It has been stuck "downloading" the same update:

```
Get:44 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:45 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:46 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:47 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:48 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:49 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:50 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:51 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:52 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:53 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:54 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:55 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:56 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:57 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:58 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:59 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:60 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:61 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:62 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:63 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:64 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:65 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:66 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:67 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:68 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:69 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:70 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:71 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:72 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:73 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:74 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:75 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:76 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:77 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:78 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:79 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:80 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]             
Get:81 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:82 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:83 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:84 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:85 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:86 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:87 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:88 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:89 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:90 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:91 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:92 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:93 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:94 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:95 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:96 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                 
Get:97 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]   
```

I canceled it, restarted, and once again tried ```
sudo apt-get upgrade
``` and it did the same thing. I then tried to use the GUI to update (I unchecked linux-image...), but this time it got stuck on on a different file. So I am not sure what to do, are they haveing issues with the repos? I'm out of ideas...

---

### Post by taurus on 2009-01-10
Wait a second.  Intrepid is not 7.10.  Which release are you running anyway?

```
lsb_release -a
```
Otherwise, go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and try another server.  Main Server should be good.

---

### Post by SidewinderX on 2009-01-11
Woops, my apologies. I am running 8.10. I did as you suggested then ran ```
sudo apt-get update
``` I started that about 30 minutes ago and it is still running. I am sure ```
sudo apt-get upgrade
``` will have the same results as before.

I would blame the "slowness" on my internet, but according to speedtest.net I am getting 11069 kb/s download so I don't think my internet is the issue. Any other ideas? I would have no problem reinstalling Ubuntu since it is a fresh install, but I was having this same problem with Kubuntu yesterday.

Edit 1:
Update just finished:
> Fetched 3373kB in 52min28s (1071B/s)  
The upgrade is running right now, and appears to be stuck in the same place as before:
```
Get:2 http://archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]                                    
Get:3 http://archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.4MB]  
```

Edit 2:
The updates appear to be installing but an an incredibly slow rate

---

