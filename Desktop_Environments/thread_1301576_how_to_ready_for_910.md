---
title: "how to ready for 910"
date: 2009-10-26
forum: Desktop Environments
---

### Post by bellnas on 2009-10-26
My laptop is windows7 and ubuntu904,and I have find one blank cd to update ubuntu.
so, data is very important and I want to update ubuntu from 904 to 910 smoothly.
thank your advice.

-------------------------

Thanks , it was resolved.
And I remove ubuntu 904 partition in windows7 ,restart ,can't logon windows because . Don't care about it, install ubuntu910, which where recognized windows7 loader and rebuild grub item.

---

### Post by MelDJ on 2009-10-26
put all your stuff in a pendrive. then uninstall ubuntu and then do a clean install of karmic

---

### Post by undecim on 2009-10-26
Also, when you install, it's a good idea to have your home directory on a seperate partition so that when you upgrade to the next version, you don't have to worry about moving data. (anytime there is a new filesystem, you should do a clean install)

Though if you do that, be careful not to format your home partition when you upgrade.

EDIT: Also, make sure that you give your root partition enough space for any apps you want to install, and temporary files, etc. I would recommend a minimum of 5G. I personally have mine set to 20G, with a home partition of 200G, but really, you should just set it to what you think you will need.

---

