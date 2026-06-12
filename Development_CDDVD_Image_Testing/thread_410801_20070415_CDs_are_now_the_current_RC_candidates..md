---
title: "20070415 CDs are now the current RC candidates."
date: 2007-04-16
forum: Development CD/DVD Image Testing
---

### Post by Henrik on 2007-04-16
20070415 CDs and 20070416 DVDs are now the current RC candidates. 

Get the images 
from [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

Tracking information and md5sums can be found here as usual: 
[https://www.stgraber.org/ubuntu/isotesting/](https://www.stgraber.org/ubuntu/isotesting/)

---

### Post by sgornick on 2007-04-16
So correct me if I'm wrong.  
Feisty release will be DVD only (if you want the GUI (ubiquity) installer), with the alternate being text-only?

If so, that suits me fine, but it is kind of suprising since all the Herd-x alphas and the beta were LiveCD (under 700MB).

---

### Post by v8YKxgHe on 2007-04-16
nope, the LiveCD/Desktop CD is the one with the GUI installer and Live Gnome preview.

---

### Post by TimJBart on 2007-04-16
So if I grab this image, any bug fixes from now will just be automatically updated yeh?

---

### Post by JanDM on 2007-04-16
That's right, but that's always the case with development versions.

Unstable versions are automatically updated to the stable version, from stable to development or next stable you need a dist-upgrade :)

---

### Post by TimJBart on 2007-04-16
so cool we don't have to wait for the release date!!  I like the flexible timings

---

### Post by Henrik on 2007-04-17
These are likely to become final images, unless the sky falls down (ie. we discover some very bad breakage. That's why we need widespread testing.

See more details at [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-April/000281.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2007-April/000281.html)

---

### Post by leibowitz on 2007-04-17
Excuse me, but I think the sky is falling (at least for the x86_64 iso).

Yes, the current kernel provided by these 64bits cd images (2.6.20-15); both Ubuntu and Kubuntu; is incompatible with the kernel module driver rt61 from serialmonkey, also provided by default in the cd images.

The result is a system freeze. That's a big problem. I found that issue during ISO testing more than three weeks ago. My bug report can be found here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94944](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94944)

I did everything I can to test the CD and found a bug! I did everything I can to find where it cames from, and found that the kernel module was implicated. Then, I did everything I can to submit the bug. And then I did everything I can to find useful information on the serialmonkey website. I even submitted a bug in the project bugzilla.

Still no reaction here. And the bug is still.

What should I do now ? The release is tomorrow, and the ISO (tested one hour ago) is shipped with _the same_ rt61 kernel module version !

I don't know who is to blame, but that's not the focus. Something should be done now!

Solution n°1 : blacklist the rt61 kernel module in the 64bit ubuntu and derivatives
Solution n°2 : do nothing.
Solution n°3 : update the rt61 kernel module to the CVS version, recompile, make iso, and test it again. That will be short as the release is in one day! That's less than one day to do each step.

PS: oh, and this bug has been confirmed by many different users.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20?field.searchtext=rt61](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20?field.searchtext=rt61)

---

### Post by bagguley on 2007-04-18
Sorry slightly confused. Whats the difference between the DVD and CD release candidtaes? Is it just additional packages?

---

