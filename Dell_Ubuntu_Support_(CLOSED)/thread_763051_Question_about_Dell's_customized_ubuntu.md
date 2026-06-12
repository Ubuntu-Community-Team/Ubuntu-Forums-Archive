---
title: "Question about Dell's customized ubuntu"
date: 2008-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shae on 2008-04-22
How long does it take Dell to release their customized install disks after a new release of Ubuntu?

---

### Post by fragos on 2008-04-22
I don't remember exactly but think Dell 7.10 came out weeks later. I've a 1420n that came with 7.04 and waited for the Dell release before updating. Everything worked.

---

### Post by shae on 2008-04-22
Thanks, how is your 1420N?

---

### Post by fragos on 2008-04-22
1420n is way cool. I got the 9 cell battery as my only option which gives close to 5 hours run time. It's great not having to be obsessed with find AC to charge in my local Starbucks. The default sensitivity and acceleration setting for the touch pad were too slow for my taste. This is the only thing that sent me to configuration file editing. I'm very satisfied. I mostly use it for writing and web site development. I like the mat screen finish of the base model -- reflections are never a problem.

---

### Post by shae on 2008-04-22
That is great to hear!  I just ordered one myself.

---

### Post by drsaamah on 2008-04-23
I personally prefer the non-Dell-customized version of Ubuntu.  From my experience the only thing that the Dell version did was add more stuff to my repositories list, add more stuff onto my hard drive, and forced a stupid nvidia splash screen to pop up before the log-in splash screen.  Right now, I'm running the beta version of Hardy, so obviously its completely non-Dell-customized and it runs just great with all my hardware (see signature) so you might want to try out both just to see if there's any reason to wait around for the Dell version.

---

### Post by notwen on 2008-04-23
I personally own a Inspiron 1420n and am currently using a install from Dell's custom Gutsy image.  It works great.  These custom images from Dell include additional drivers/packages for some of the Del's machines hardware that was not supported in the official Ubuntu releases.  Dell released their Feisty image about a month after they began offering the pre-installed machines.  The custom Gutsy image only took 3 weeks to be offered after Gutsy's official release.  They seem to be doing a good job w/ these custom images and are getting them out in a reasonable amount of time, they not only include the additional drivers/packages but also implement whatever bug fixes have been discovered in the actual Ubuntu release as well.  

This will be less and less of a issue as Ubuntu's kernel includes more and more of the Dell machines hardware.  I know the blacklisting of the Intel X3100 chipset is rumored to be lifted in Hardy, so maybe we'll eventually reach a point where these custom images are no longer needed, but until that day I will use them.  I tend to carry my custom Dell Ubuntu DVD around w/ me in case a quick re-install is ever needed.  Be sure to check out [Dell's Linux Wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10") for any issues you may encounter and how to correct them.  Congratulations on your new purchase and be sure to post if you run into any issues.  =]

---

### Post by shae on 2008-04-23
I ordered a Inspiron 1420N with:
Intel Core 2 Duo T7500
2GB, DDR2, 667MHz
NVIDIA (R) GeForce TM Go 8400M GS

By the way you can turn off the Nvidia splash screen with an option in xorg.conf.  Add this to your device section:

```
Option "NoLogo" "true"
```

Would this laptop be able to run Urban Terror or Warcraft 3 (through wine) acceptably?  What version of Nvidia's drivers should I use?

---

### Post by fragos on 2008-04-23
The version instaled by the Restricted Manager in Ubuntu will do the job for you. Doing otherwise can cause you trouble later. [http://winehq.org/](http://winehq.org/) has lists of Windows software that run under wine. Check out package "wine-doors". It's available as a deb package at [http://getdeb.net](http://getdeb.net). It will make getting wine up and running much easier.

---

### Post by shae on 2008-04-23
I was just wondering if it would run well (FPS wise, etc.).  I have no problems installing it; sorry for the mix up.  What kind of trouble later are you talking about?  Can Nvidia's kernel module use DKMS?

---

### Post by clavdivs on 2008-04-23
> **notwen said:**
> They seem to be doing a good job w/ these custom images and are getting them out in a reasonable amount of time, they not only include the additional drivers/packages but also implement whatever bug fixes have been discovered in the actual Ubuntu release as well.

If you install standard Ubuntu on a Dell machine, can you get these drivers off the Dell Ubuntu CD, or elsewhere online, without having to reinstall with the Dell version?

---

### Post by notwen on 2008-04-23
> **clavdivs said:**
> If you install standard Ubuntu on a Dell machine, can you get these drivers off the Dell Ubuntu CD, or elsewhere online, without having to reinstall with the Dell version?

I suppose if you know enough to single out those specific packages/drivers from the custom Dell-Ubuntu image, but I'm not familiar w/ doing this.  Why would you just pull the drivers off it when you could just install it and have everything working by default.  I personally would like Dell to offer a install w/ less pre-installed applications, but until they do I'm stuck removing un-wanted applications post-install.

---

