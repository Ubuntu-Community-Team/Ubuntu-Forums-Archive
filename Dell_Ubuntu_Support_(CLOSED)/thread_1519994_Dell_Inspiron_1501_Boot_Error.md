---
title: "Dell Inspiron 1501 Boot Error"
date: 2010-06-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rws0005 on 2010-06-29
I used the Wubi Ubuntu Installer for Windows so that I could maintain my Windows 7 boot and have the option to boot Ubunti; however, when I went to boot Ubuntu for the first time after having everything download, I received the error:

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert windows installation disc and restart
2. Choose language setting, click next
3. Click repair

File: \ubuntu\winboot\wubildr.mbr
Status: 0xc000000f
Info: The selected entry could not be loaded because the application is missing or corrupt

So, the question is, what do I do?

Thanks,
rws0005

---

### Post by bcbc on 2010-06-29
I've seen a couple of threads on this over the past couple of years. Most solved by reinstalling wubi.

this is taken from the [wubi guide]("https://wiki.ubuntu.com/WubiGuide") (maybe relevant if the wubildr.mbr file is missing)
> Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet). If Wubi fails to start, boot into Windows, run chkdsk /r from Windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again.

Note that sometimes files are moved by Windows into a hidden folder called c:\found.000. You need to have c:\ubuntu\disks\root.disk and c:\ubuntu\disks\boot. If you do not see those, look for found.000. You need to change the Windows Explorer settings to be able to see hidden folders first, then move the files from found.000 to their original location.

---

