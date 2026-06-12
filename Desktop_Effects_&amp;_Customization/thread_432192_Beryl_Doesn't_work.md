---
title: "Beryl Doesn't work"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by RyanFaith88 on 2007-05-03
I recently had to fix my video card driver ([http://ubuntuforums.org/showthread.php?t=432093](http://ubuntuforums.org/showthread.php?t=432093)) and got it fixed by following other posts([http://ubuntuforums.org/showthread.php?t=431628&highlight=Screen+Resolution+ATI)](http://ubuntuforums.org/showthread.php?t=431628&highlight=Screen+Resolution+ATI)), and now Beryl or the built in desktop effects won't work.  I try to enable the desktop effects but I get an error message "Desktop effects could not be enabled".  I tried to switch to the Beryl Window manager in the beryl context menu, but it keeps reverting itself to Metacity.  I have an ATI Radeon X600 and my coputer is perfectly capable of handling a lot of high end stuff.  Any help would be greatly appreciated.

---

### Post by rolf-c on 2007-05-03
Well, I don't have an ATI card but there are some issues with ATI drivers and compositing.  Let's see if direct rendering is enabled.  In a term window try this and check your results:

```
rolf@unit1:~$ glxinfo  |grep direct
direct rendering: Yes
rolf@unit1:~$ 
```

---

### Post by RyanFaith88 on 2007-05-03
> **rolf-c said:**
> Well, I don't have an ATI card but there are some issues with ATI drivers and compositing.  Let's see if direct rendering is enabled.  In a term window try this and check your results:

```
rolf@unit1:~$ glxinfo  |grep direct
direct rendering: Yes
rolf@unit1:~$ 
```
By typing in that first line, I got that direct rendering: NO

---

### Post by rolf-c on 2007-05-04
I see you started another thread on the direct rendering piece, so I am abandoning this thread in favor of the newer one.

---

