---
title: "Choosing the right Ubuntu..."
date: 2006-01-01
forum: General Help
---

### Post by mitdxiw on 2006-01-01
I am building a new AMD64 based PC this month that I plan to use primarily for software development in Java (using Eclipse). I have been using Windows XP for years and am fed up with it. I have deeply studied several different distributions of linux and after trying some live cd's decided that Ubuntu was my distribution of choice. I like the Gnome desktop and I find Ubuntu to be both user friendly and have all the power of the linux command line. I would like to install the 64-bit version of Ubuntu on my new machine, but after browsing through some posts on this forum, I'm a little turned off to it. I've heard multiple people say Eclipse doesn't run and that the 64-bit version is unstable. Since I do not have any experience with Ubuntu, its hard for me to decide between the 32-bit and the 64-bit version. Is there any way one of you could just break down the advantages / disadvantages of both, considering I am building a PC primarily for Java software development? If anything, could I alteast get some advice as to which one I should choose?

Thanks, I appreciate everything.

---

### Post by Lord Illidan on 2006-01-01
I think you should go 32 bit. I don't think java works correctly in 64 bit Ubuntu as yet. There are also the issues of multimedia codecs, flash etc.

---

### Post by drfalkor on 2006-01-01
and install a k7(amd) based kernel
'sudo apt-get install linux-k7'

---

### Post by mitdxiw on 2006-01-01
About the AMD kernel:

1) isnt the AMD64 the K8, so why is it better to install the K7 kernel?
2) what are the advantages?
3) how exactly do I do it? in the installation?

---

### Post by mitdxiw on 2006-01-01
bumpity bump

---

### Post by Lord Illidan on 2006-01-01
[quote=mitdxiw]About the AMD kernel:

1) isnt the AMD64 the K8, so why is it better to install the K7 kernel?
2) what are the advantages?
3) how exactly do I do it? in the installation?[/quote]

1. Well, there is no K8 kernel, only the K7.
2. The advantages are that it is optimised for your processor, basically, so you get a speed boost.
3. No, after the installation. Just type

```
sudo apt-get install linux-k7
```

---

