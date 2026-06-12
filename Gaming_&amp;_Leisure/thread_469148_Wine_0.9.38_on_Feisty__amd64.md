---
title: "Wine 0.9.38 on Feisty  amd64"
date: 2007-06-09
forum: Gaming &amp; Leisure
---

### Post by Gazimoff on 2007-06-09
Is there any information yet when this package will be released? I've been trying to update via SPM as it contains some major 64-bit improvements according to the news article, but I don't feel happy/confident about compiling it myself.

---

### Post by Peetke on 2007-06-10
Official 64bits Feisty binary packages are available here:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Gazimoff on 2007-06-10
I've tried updatiny my WIne install using the instructions provided, but I get the following error:

```
sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Checking in SPM, the version that I'm running is 0.9.37, but according to winehq.org, 0.9.38 has been released with a load of 64-bit compilation fixes. Since I'm running Feisty 7.04 amd64 version, I was hoping to use the new version.

---

### Post by Gazimoff on 2007-06-13
Bumping this in the hope of a response :)

---

### Post by jusmurph on 2007-06-14
I believe that updating wine does not delete the old version in attempts not to break something that previously worked.

Someone can confirm this but try launching wine 0.9.38 from the terminal.

---

### Post by misha680 on 2007-06-14
> **jusmurph said:**
> I believe that updating wine does not delete the old version in attempts not to break something that previously worked.

Someone can confirm this but try launching wine 0.9.38 from the terminal.

Well it doesn't delete your .wine directory with your fake C drive, but the version of the actual package, if available, should update. You can also just type 
```
wine --version
```
to see which version you are running.

Misha

---

### Post by sigmund1898 on 2007-06-14
> **jusmurph said:**
> I believe that updating wine does not delete the old version in attempts not to break something that previously worked.

Someone can confirm this but try launching wine 0.9.38 from the terminal.

As of this post, the link for Wine 0.9.38 for Feisty 7.04 x86_64 users is broken.  Apparently it hasn't been built yet.  :(   [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Gazimoff on 2007-06-15
Thanks for the update. I was wondering why it wasn't showing as updated in SPM :)

Any idea on how long it'll take for the build to be ready?

Many thanks!

---

### Post by Petengy on 2007-06-16
I confirm 0.9.38 for amd64 is not ready yet

[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

but someone could explain how to compile it ?


I saw now there's 0.3.39 version....

TnX

Pet

---

### Post by sams2100 on 2007-06-18
It appears that the last two version releases of Wine were not built for amd64.  Whoever the maintainer is of this build, is slacking off a bit because he's almost a month behind at this point.

You can still remove your amd64 version of wine and install the latest i386 version to take advantage of some of the other nice fixes, such as the sound and video fixes.  Of course you will not be able to take advantage of the 64 bit fixes they are reporting, but from what I understand, these are only compiler fixes, not so much runtime fixes.

---

### Post by jayson.rowe on 2007-06-18
I don't know what version it is, but I got Wine for AMD64 from winehq.org - is the newer version supposed to be a lot better? The version I have is running VERY well for me.

---

### Post by Gazimoff on 2007-06-22
OK, I've managed to snaffle Wine 0.9.39 for AMD64 from this link:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

From what I understand, it's not been loaded into the APT repository yet, so SPM's not picking it up.

Al I can suggest is to get it - there are some huge performance improvements here!

---

