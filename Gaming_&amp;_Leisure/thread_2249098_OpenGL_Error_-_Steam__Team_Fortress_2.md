---
title: "OpenGL Error - Steam | Team Fortress 2"
date: 2014-10-19
forum: Gaming &amp; Leisure
---

### Post by miguel.renaud on 2014-10-19
After installing and running Team Fortress 2 I am displayed a message box of the following:
```
Error!: Could not find required OpenGL entry point 'glGetError'! Either your video card is unsupported, or your OpenGL driver needs to be updated.
```

I have installed drivers from the official AMD website for my AMD Radeon HD 7500 Series Graphics Card.

Any help would be greatly appreciated. When answering please try to be specific as possible as I have been on Ubuntu for less than a week and am a bit of a noob.

Specifications:
OS: ubuntu 14.04.01 LTS
Memory: 9.6 GiB (10GB)
Processor: AMD A10-5700 APU with Radeon(tm) HD Graphics × 4 
Graphics: AMD Radeon HD 7500 Series
OS Type: 64-bit 
Disk: 304.5 GB

---

### Post by miguel.renaud on 2014-10-19
Please forgive this post I think I'm going to swap for Windows 7. Overall I was happy with Ubuntu.

---

### Post by lip25022 on 2014-10-19
I had the same issue with Half Life, it appears it comes from a bunch of libraries which are not up to date.

Problem solved, look here : [http://ubuntuforums.org/showthread.php?t=2247842&p=13147009#post13147009](http://ubuntuforums.org/showthread.php?t=2247842&p=13147009#post13147009)

---

### Post by cosy2 on 2014-11-28
> **lip25022 said:**
> I had the same issue with Half Life, it appears it comes from a bunch of libraries which are not up to date.

Problem solved, look here : [http://ubuntuforums.org/showthread.php?t=2247842&p=13147009#post13147009](http://ubuntuforums.org/showthread.php?t=2247842&p=13147009#post13147009)


> you do not have permission to access this page. This could be due to one of the following reasons:

is imposible to view the post

---

### Post by dannyboy79 on 2014-11-29
> **miguel.renaud said:**
> After installing and running Team Fortress 2 I am displayed a message box of the following:
```
Error!: Could not find required OpenGL entry point 'glGetError'! Either your video card is unsupported, or your OpenGL driver needs to be updated.
```

I have installed drivers from the official AMD website for my AMD Radeon HD 7500 Series Graphics Card.

Any help would be greatly appreciated. When answering please try to be specific as possible as I have been on Ubuntu for less than a week and am a bit of a noob.

Specifications:
OS: ubuntu 14.04.01 LTS
Memory: 9.6 GiB (10GB)
Processor: AMD A10-5700 APU with Radeon(tm) HD Graphics × 4 
Graphics: AMD Radeon HD 7500 Series
OS Type: 64-bit 
Disk: 304.5 GBthe problem is most likely you're steam was installed before you installed the graphics driver or the other way around I forget. basically the libGL symlinks that AMD driver package is suppose to create don't get created so steam thinks you're not using the fglrx libGL files. try reinstalling steam by completely removing it and then install it again. if that doesn't work, try removing the AMD drivers and reinstall them. it's a shittty error cause i see it all the time.

---

