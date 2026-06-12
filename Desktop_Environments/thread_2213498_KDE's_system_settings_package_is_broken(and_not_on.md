---
title: "KDE's system settings package is broken(and not only that, more as well)"
date: 2014-03-26
forum: Desktop Environments
---

### Post by djozone on 2014-03-26
For some reason that is unknown to me(why it happened) KDE's systemsettings package, yes the same one that IS the KDE system settings, is broken. It's not listed on my computer even though I never directly uninstalled/removed it.

I've tried almost everything I have thought of and looked up online, trying to fix the broken package via the fix broken packages option in Synaptic, using several lines of terminal code to fix it(including sudo apt-get update and upgrade and other copy and pasted lines I've found online that I have already forgot).

But ultimately what I think IS the problem as to why it is broken(along with Ubuntu software center and the GNU Grub), is that stupid sudo apt-get dist-upgrade I ran thinking that the line that I ran was going to get my system as up to date as I could. But no, I believe that did more harm than good seeing as now I am suffering now with KDE's system settings broken, the Ubuntu software center not starting at all(the cursor shows it tries to load but just stops loading altogether). Not to mention now my GNU Grub loader now instead of saying "Ubuntu" as a OS to load it instead says "LinuxDeepin" as though I have Linux Deepin installed(which is a complete lie being on the system as I never installed that desktop environment at all) even though it loads just fine.

so I'd like to know, is there an way to fix this problem.

actually I'd also like to know how to fix broken packages that are broken because of the fact I ran "sudo apt-get dist-upgrade".

---

### Post by speartip on 2014-03-27
I think more info would be helpful.
What version of kubuntu are you using?
Is this a pure kubuntu install? or have you installed kde on top of another ubuntu variant?
Running the command "sudo apt-get dist-upgrade" should not compromise your system at all. I run it regularly to upgrade to the latest available kernel, without ever having issues.
Also the fact Grub now lists Ubuntu as LinuxDeepin is strange if you have never had LinuxDeepin installed. It might also be usefull to know if you have any third party repos enabled.

---

