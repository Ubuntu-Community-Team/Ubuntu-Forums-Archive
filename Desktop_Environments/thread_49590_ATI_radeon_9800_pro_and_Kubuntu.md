---
title: "ATI radeon 9800 pro and Kubuntu"
date: 2005-07-16
forum: Desktop Environments
---

### Post by GrAyRoCkStOnE on 2005-07-16
Hello to everyone.
I am fairly new to linux.  I installed Ubuntu Linux and managed to get the ATI drivers installed and running fine.  Now I have Kubuntu installed and I cannot get the ATI drivers to install following the help and Faqs and everything.  All the Help that I've found so far is for Gnome and, as you all know, Kubuntu is KDE.  I really like the KDE interface much better than Gnome, and would prefer to stay with Kubuntu instead.
Anyone point me to step by step instructions on how to get my ATI radeon 9800 pro installed in KUBUNTU would be great.  And any other good help forums/sites you might have too so I can read up on it. 
Thank you
Tom

---

### Post by GrAyRoCkStOnE on 2005-07-16
I should have noted in my previous that I'm using the i386 (NON-64Bit) version.

Also: here is a paste from the log file:

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.


Thank you.
Tom

---

### Post by radicaldreamer on 2005-07-17
I am getting the same thing

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Error] Kernel Module : No kernel module build environment - please consult readme.


Using a 9800XT with kubuntu

---

### Post by JLTB on 2005-07-18
Hey,

It looks like you are both trying to install the latest version of the ATI driver from the ATI website, correct??

2 Things to note, 1) Kubuntu/Ubuntu comes with an ati driver installer package ([https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)) specially made for ubuntu/kubuntu. (THIS IS EASY TO INSTALL). 2) You can upgrade to the newest driver if you work for it (THIS IS MUCH MUCH HARDER).

If you do want to go for the newest one you will need to 1) Install the "normal" ati driver as described in the BinaryDriverHowto (above), 2) Get the newest driver (.run package) from the ATI site, 3) Chmod it a+x so you can run it, 4) apt-get install build-essentials, 5) Probably apt-get install gcc kdelibs-dev and some other things, 6) Check out some other tutorials ([http://www.ubuntuforums.org/showthread.php?t=32495)](http://www.ubuntuforums.org/showthread.php?t=32495)), 7) Try to run the .run file with 'sudo sh ati-blah-blah-blah.run', 8) it just might work!

PS: I had a total headache trying to get the new drivers to install, the biggest thing i found was to first get the stock driver going ... if that doesn't work there's no way the new ones will.

Good luck.

---

