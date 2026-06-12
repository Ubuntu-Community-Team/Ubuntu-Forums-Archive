---
title: "Disabling A TouchPad when connecting An external Mouse"
date: 2009-03-03
forum: General Help
---

### Post by Qsl1pknotp on 2009-03-03
Hi,

This seems like a relatively easy problem.  I have created 2 scripts called EnableTPad and DisableTPad.  They enable/disable the Touchpad (respectively).  However, I would like to automate the process so they would automatically execute when I plug in my mouse.  I have a thread 

here: [http://ubuntuforums.org/showthread.php?t=1086107](http://ubuntuforums.org/showthread.php?t=1086107) (I don't know how to mark as solved so I copied it over, if someone could tell me how to do so it would be greatly appreciated :D).  

I also when through this guide ([http://ubuntuforums.org/showthread.php?t=502864](http://ubuntuforums.org/showthread.php?t=502864)), and still couldn't get the rules to work.  My Rules file is : 
[code]ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="041e", SYSFS{idProduct}=="1053", RUN+="/home/(name)/bin/DisableTPad"[code]

Also, if I would like to have the touchpad Enabled after I take out the mouse, would I just change the "Action=="remove" ? Once again, thanks for any help.  You guys are awesome :)

---

### Post by Qsl1pknotp on 2009-03-03
Bump

I also tried changing SYSF to ATTRS (In the guide it said to try that too) But still no success.

---

### Post by Qsl1pknotp on 2009-03-05
Bump

---

