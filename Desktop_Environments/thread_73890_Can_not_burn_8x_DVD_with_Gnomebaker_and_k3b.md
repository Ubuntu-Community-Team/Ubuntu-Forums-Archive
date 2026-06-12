---
title: "Can not burn 8x DVD with Gnomebaker and k3b"
date: 2005-10-10
forum: Desktop Environments
---

### Post by steigweis on 2005-10-10
Hello, I cannot burn 8x dvd with gnomebaker and k3b. The gnomebaker output says, that it is 8x1385 KBps, but it lasts about 20 minutes to burn a dvd-r. 

With Windows/Nero, there is no problem with 8x burning. 

What is the problem? Can gnomebaker and k3b only burn dvd+r? Is there a setting to say the burnprogram to burn 8x?

Thanks in advance...

---

### Post by Perfect Storm on 2005-10-10
You could try NeroLinux, if you already Nero for Linux then you don't have to pay for it. Just type your license code in the NeroLinux.

---

### Post by steigweis on 2005-10-10
NeroLinux even burns in 2x only :/

How can i tell gnomebaker or k3b to recognize my DVD-RW as a 8x device?

---

### Post by professor_chaos on 2005-10-10
did you try turning on dma?

done something like this..

```
sudo hdparm -d1 /dev/hdc
```

---

### Post by steigweis on 2005-10-11
[QUOTE=professor_chaos]did you try turning on dma?

done something like this..

```
sudo hdparm -d1 /dev/hdc
```[/QUOTE]

dma is already enabled. somebody told me, that my problem could be a driver issue, i.e. that cdrecord does not use the best drivers for my device. :confused:

---

