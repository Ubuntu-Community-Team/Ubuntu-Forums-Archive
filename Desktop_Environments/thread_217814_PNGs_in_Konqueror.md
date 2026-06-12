---
title: "PNGs in Konqueror"
date: 2006-07-17
forum: Desktop Environments
---

### Post by SnuffThePunk on 2006-07-17
Hello all. I'm having a problem with Konqueror in Kubuntu 6.06. I started with reqular Ubuntu then did apt-get install kubuntu-desktop. EVer since I did this PNGs have not been displaying thumbnails in Konqueror and when I try to open them I get a "select the application" thing. Also, when I try to change my desktop background the "Configure Desktop" tool doesn't see them either so I have to enter the full location of the files. Once I enter them though my background does change and if I choose to open the files in The GIMP then they do display.

I've tried sudo apt-get upgrade libpng but it tries to upgrade the entire distro for some reason.

I had the same problem with the AMD64 version (my CPU is AMD64 but I use the 32-bit version for flash) and I had to reinstall.

Any help would be greatly appreciated.

---

### Post by Kilz on 2006-07-17
> **SnuffThePunk said:**
> 
I had the same problem with the AMD64 version (my CPU is AMD64 but I use the 32-bit version for flash) and I had to reinstall.


Well if you end up reinstalling, just to let you know. Flash works on the amd64 version. Check out the howto in my signature.

---

### Post by SnuffThePunk on 2006-07-18
Yeah, maybe I should just reinstall. What's holding me back is I've got a whole load of stuff on here. My book, my music... it'd take forever to back it up. I did try the Flash on AMD64 thing but Firefox would crash whenever I went to the "Go" menu for some reason. (Other than that it worked fantastically)

Maybe I'll just do an apt-get install ubuntu-desktop and see if that works.

If anyone could bring any more light on this issue I'd appreciate it.

**EDIT:** Okay, I fixed it. I just removed the .png extension and then put it back and Konqueror sees it with no problem.

---

