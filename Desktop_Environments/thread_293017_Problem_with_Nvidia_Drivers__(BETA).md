---
title: "Problem with Nvidia Drivers  (BETA)"
date: 2006-11-04
forum: Desktop Environments
---

### Post by jgio on 2006-11-04
Hi, i have a problem when trying: 
```
john@ubuntu:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx: Depends: nvidia-kernel-1.0.9625
E: Broken packages

```

Then i try:
```
john@ubuntu:~$ sudo apt-get install nvidia-kernel-1.0.9625 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-kernel-1.0.9625 is a virtual package provided by:
You should explicitly select one to install.
E: Package nvidia-kernel-1.0.9625 has no installation candidate

```

What's going wrong??

---

### Post by BitTorrentBuddha on 2006-11-04
You need to get a different version of linux-restricted-modules, you should reference the guide you're looking at to see how to do this, if you're following the guide I was you're probably looking for these repositories:
deb [http://amaranth.selfip.com/](http://amaranth.selfip.com/) edgy lrm
deb-src [http://amaranth.selfip.com/](http://amaranth.selfip.com/) edgy lrm

---

### Post by chopz on 2006-11-04
I have the same issue.  I have tried commenting out some of the non-defualt repos as recommended in other threads but no joy.  Any other suggestions?

---

### Post by jgio on 2006-11-04
> **BitTorrentBuddha said:**
> You need to get a different version of linux-restricted-modules, you should reference the guide you're looking at to see how to do this, if you're following the guide I was you're probably looking for these repositories:
deb [http://amaranth.selfip.com/](http://amaranth.selfip.com/) edgy lrm
deb-src [http://amaranth.selfip.com/](http://amaranth.selfip.com/) edgy lrm

Didn't work....

---

### Post by garretwp on 2006-11-04
I had the same issue and found this site with a repository that worked for me. It installed the latest 9626 driver.

Here is the link:

[http://albertomilone.com/driver_edgyunstable.html](http://albertomilone.com/driver_edgyunstable.html)

Go to the link and add the repository to your source.list and then do an apt-get update and then apt-get upgrade and all should work. I did this a few hours ago and everything is working well so far!

- Garrett

---

### Post by FedeXX on 2006-11-05
> **garretwp said:**
> I had the same issue and found this site with a repository that worked for me. It installed the latest 9626 driver.

Here is the link:

[http://albertomilone.com/driver_edgyunstable.html](http://albertomilone.com/driver_edgyunstable.html)

Go to the link and add the repository to your source.list and then do an apt-get update and then apt-get upgrade and all should work. I did this a few hours ago and everything is working well so far!

- Garrett

Ok, it worked perfectly! Now beryl is really charming... 8) 

Thank you!

---

### Post by jgio on 2006-11-05
Thnx guys it worked for me too :)

---

