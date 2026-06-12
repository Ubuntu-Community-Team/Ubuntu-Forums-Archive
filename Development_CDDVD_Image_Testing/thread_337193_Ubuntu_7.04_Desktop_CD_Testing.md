---
title: "Ubuntu 7.04 Desktop CD Testing"
date: 2007-01-12
forum: Development CD/DVD Image Testing
---

### Post by leetcharmer on 2007-01-12
I need help filling out this standard template.

```
Test case type: **Ubuntu Herd 2, Desktop CD, manual partitioning**
Image ID: **Herd 2**
Date of testing: **2007-01-12**
md5sum confirmed: **Yes**
Pass/Fail: ???
Bugs identified: ???
Other comments:
Pass/Fail -- is this simply installation?
Bugs identified -- I've gotta check for all of them, can you help me find them?

1) when it boots up, the screen brightness resets to lowest settings
2) during upstart -- the graphical boot is all grayscale
3) Resolution is not set up properly out of box; should be 1280x800, not 1024x768
3a) When switching to 1280x800 -- the screen looks all garbled up.
4) bug [#76174]("https://launchpad.net/bugs/76174") Unable to edit wireless network properties.
Clicking "Properties" makes the window close
```

I hope I did this right so far.

---

### Post by tormod on 2007-01-12
> Alright, md5sum -- how do I check that?
Run this command, and compare the output hash with the relevant one in the **MD5SUMS** file in the download directory: ```
md5sum feisty-desktop-amd64.iso
```

PASS/FAIL is hard to say, but most items under Testing/Short should have been tested to work well.

(4) sounds like bug [#76174]("https://launchpad.net/bugs/76174").

(3) What exactly is your graphic card?

---

### Post by Henrik on 2007-01-12
Yes, PASS/FAIL is a bit tricky. The important thing is to list the bugs you find and then someone with more experience (or ultimately the release team) can decide if it is serious enough for a FAIL.

---

### Post by leetcharmer on 2007-01-12
my laptop stats can be found here:

[https://wiki.ubuntu.com/LaptopTestingTeam/EmachinesM6805](https://wiki.ubuntu.com/LaptopTestingTeam/EmachinesM6805)

Quick answer: ATi Mobility Radeon 9600

---

### Post by leetcharmer on 2007-01-12
Thanks for the md5sum command, I added the results.

---

### Post by pochu on 2007-01-13
Hi leetcharmer.

The ID is not the name of the iso. All the isos have the same name (all x86 Desktop, all the x86_64 alternate...). It doesn't matter if they are alpha, beta, RC, or final, the name is the same for one version (feisty here).

The ID is the number of the image. It has a date structure: YYYYMMDD[.N] (N appears when for one day, there have been some images).

For example, 20070113, or 20070113.1 (this will be the second image of today).

The ID number is the folder where you can download the daily build. Or if you have installed an official release (as Herd 2), you can post the name.

Another way to look what is the ID is to uncompress the .iso and search the .disc file, which has the ID number of the image (I haven't tried this myself, but I'll the sooner I can).

Best regards
Pochu

---

### Post by leetcharmer on 2007-01-15
Thanks :D!
Noted above!

---

