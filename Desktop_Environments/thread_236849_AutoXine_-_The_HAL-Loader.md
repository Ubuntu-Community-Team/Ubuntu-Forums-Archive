---
title: "AutoXine - The HAL-Loader"
date: 2006-08-15
forum: Desktop Environments
---

### Post by Amnon82 on 2006-08-15
I hated always when Xine gave me error messages when I put the DVD in the "wrong" DVD drive. So I created AutoXine. I'm coding with REALbasic. It should work with every 386 release. If not, post me.

```
AutoXine 0.01.1 for Ubuntu 6.06 by Amnon82

What does AutoXine?

It's simple. As everybody know. Xine uses '/dev/dvd' as default dvd-drive.
AutoXine get rid of that. The Gnome-Desktop supports throuh HAL a autostart feature
for VIDEO-DVDs. Now you can use AutoXine to start Xine in fullscreen with the
DVD you just put in in your drive. It dosn't matter if it is linked with '/dev/dvd'.

How to setup AutoXine?

Save it into a folder where you have write access.
Go to 'System' > 'Preferences' > 'Removable Drives and Media'
Go to the 'Multimedia'-Tab.
Click on 'Browse' at 'Video DVD Discs' and search for AutoXine.
Example: '/home/programs/autoxine/AutoXine'
Click on 'OK'.

On next time when you put in a DVD AutoXine will do the rest.


History:

0.01.1 - 15.08.06
* log-feature added

0.01 - 15.08.06
* inital release for Ubuntu 6.06 386
* scanning for 'cdrom', 'cdrecorder', 'dvdrom' and 'dvdrecorder' in '/media'


(C) 2006 AMSOFT

p.s. 'xine --auto-play=fh dvd://%m' will do the same, but you won't have a nice log ;)
```

---

