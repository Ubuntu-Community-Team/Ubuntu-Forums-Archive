---
title: "K3b Problem Burning Video DVD"
date: 2005-12-24
forum: Desktop Environments
---

### Post by ScoobyDan on 2005-12-24
Hi All,

I have just tried burning my first Video DVD using K3b, but I get the following error:

> 
Unable to link temporary file in folder /tmp/kde-daniel/k3bVideoDvd0.


I can normally burn ISO's no problem, but when I try to convert the DVD files to an ISO using

> 
mkisofs -dvd-video -o dvd.iso ./dvd


I get the errors:

> 
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
Using VIDEO000.IFO;1 for  ./dvd/VIDEO_TS/VIDEO_TS.IFO (video_ts.ifo)
Using VIDEO000.BUP;1 for  ./dvd/VIDEO_TS/VIDEO_TS.BUP (video_ts.bup)
mkisofs: No such file or directory. Faild to open ./dvd//VIDEO_TS/VTS_01_0.IFO
mkisofs: Can't open VTS info.
mkisofs: Unable to parse DVD-Video structures.
mkisofs: Unable to make a DVD-Video image.


Any ideas?

Daniel

PS - Sorry if this was typed a bit slowly - I am typing single-handed after breaking my right arm :(

---

