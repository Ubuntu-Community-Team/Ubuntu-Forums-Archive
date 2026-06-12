---
title: "Open Office 2.0.3 fails with broken packages"
date: 2006-07-29
forum: Desktop Environments
---

### Post by hrvelic on 2006-07-29
Hello.
After a few days ago, I tried installing the new update that included open office 2.0.3. Update manager notified me that I should use apt-get dist-upgrade or synaptics to update.
So, I went and used synaptics and ended up with the following error message:

[FONT="Courier New"]E: /var/cache/apt/archives/openoffice.org-calc_2.0.3-3dapper3_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/scalc.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
[/FONT]

The update resulted in broken packages:
language-support-it
language-support-ja
openoffice.org2-base
openoffice.org2-draw
openoffice.org2-impress
openoffice.org2-math
openoffice.org2-writer
openoffice.org-gnome
openoffice.org-gtk

Trying to fix them in Synaptics or by running apt-get -f install always results in the above error.
A few months ago I have upgraded from 5.10 to 6.06, and except having problems with reluctant ATI driver (common thing that >_> ), and some features like Lock Screen that do not work, my box ran ok.
I have no idea what to do. While I'm able to work my way around Linux, I'm really not an expert in using apt-get or with the whole debian/ubuntu package system.

Thanks in advance,
Hrvoje Velic

---

### Post by ThrobbingBrain66 on 2006-07-29
If you are able to uninstall the broken packages, do that and then use this to install OO2.0.3

[http://www.ubuntuforums.org/showpost.php?p=1223054&postcount=4](http://www.ubuntuforums.org/showpost.php?p=1223054&postcount=4)

(youll have to download the source code from openoffice.org)

---

### Post by hrvelic on 2006-07-29
Thank you for your help. I kind of managed to resolve the issue.
I have tried uninstalling the packages before, but to no avail. Today, I was a bit more persistent and managed to uninstall broken packages by using the "complete removal" option. I also went and removed ("complete removal too") the whole of openoffice. Afterwards I installed ubuntu-desktop to get open office 2.0.3 back.
It seems there was a conflict with help and language support files which the installer was unable to resolve, all due to a change in what was packaged in OO2.0.3. :/
Now I'm contemplating doing a wipe of my system, except for a few config files and my home and then reinstalling afresh 6.06. At least it might resolve the non-working features problem and prevent conflicts of this type.

---

### Post by hrvelic on 2006-07-29
Well, another update.
I tried installing:
language-support-en
language-support-hr
language-support-it
language-support-ja

I had no warnings when I marked them, but when I clicked apply in synaptics, I was welcomed by:

E: /var/cache/apt/archives/openoffice.org-help-en-us_2.0.3-3dapper4_all.deb: trying to overwrite `/usr/lib/openoffice/help/en/default.css', which is also in package openoffice.org-common

Oh, joy. I believe this is a bug or misconfigured dependencies in the packages. Should I report it, and if so where and how?

Also while I was doing all this, a new version, 2.0.3-3dapper5 came out. When I wanted to upgrade, two packages:
openoffice.org-common
openoffice.org-core
require that package openoffice.org-gnome, and by proxy ubuntu-desktop be uninstalled. :confused: 
I hope 2.0.3-3dapper6 won't require the kernel to be uninstalled. ~__~
Also, do I report this too?

---

### Post by tschaboo on 2006-09-03
> **hrvelic said:**
> 
I hope 2.0.3-3dapper6 won't require the kernel to be uninstalled. ~__~
Also, do I report this too?

Well, don't try the new one, You'll run into similar problems.
I ran into problems with 2.0.3-3dapper6. Someone else already reported a bug: [https://launchpad.net/bugs/58798](https://launchpad.net/bugs/58798)

---

