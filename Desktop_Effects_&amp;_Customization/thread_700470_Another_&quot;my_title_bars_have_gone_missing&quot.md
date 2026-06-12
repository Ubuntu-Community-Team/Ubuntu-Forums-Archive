---
title: "Another &quot;my title bars have gone missing&quot; thread"
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by Radiobuzz on 2008-02-18
Hey,

I was using compiz with no problems, although the title bars did dissappear from time to time I could restore them by using "emerald --replace". I've recently tried to upgrade Compiz using [http://kwatrow.nl/repo](http://kwatrow.nl/repo) repository, and after installing it the bars were gone for good. I tried uninstalling Compiz and Emerald and re-install them and didn't work. "Emerald --replace" does nothing, neither the nVidia command which is somewhere around here, neither adding "emerald" to the command of the window decorator in ccsm.

What can I do? I'm using Ubuntu 7.10 and my video card is nVidia 5500. I have the restricted drivers installed.

---

### Post by Radiobuzz on 2008-02-18
By the way, I should comment that if I try to write "compiz &" or "compiz --replace" (I think it was), it seems to load but it also says:

starting emerald
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'

Despite this, Compiz seems to work :S.

---

### Post by Radiobuzz on 2008-02-18
Oh, and a little update. Compiz is not "working fine". What works is AWN, but I've got no effects on the windows or taskbar.

---

### Post by chavanak on 2008-02-18
AWN is compiz dependent, are you able to run AWN?

For your first query try to remove compiz and emerald config files and try!!! Though am not sure it works you can give it a try!!!

---

### Post by Radiobuzz on 2008-02-18
Yes, AWN works fine, that's the weird part. And how do I remove the config files? Deleting the program's folder?

---

### Post by Radiobuzz on 2008-02-18
Ok, using Synaptic I uninstalled once again both Compiz and Emerald and their conf files, then reinstalled. Everything kept the same. I then uninstalled it again and removed the repository I was talking about in the first post, which apparently has the latest Compiz release. After removing it, I used aptitude to clean the packages. I thought that this way it would of download the supported packages that I was using before. And either way, it all keeps being the same.

Ideas?

---

### Post by Radiobuzz on 2008-02-18
Ok, I've fixed it. I uninstalled it one again but this time I also deleted the folders. Important step :P.

---

