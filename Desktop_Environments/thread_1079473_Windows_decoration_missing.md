---
title: "Windows decoration missing"
date: 2009-02-24
forum: Desktop Environments
---

### Post by jawana on 2009-02-24
Hi Guys,

since a recent system update i have lost all the windows decoration ie minimize, maximize and close buttons.oddly enough i can see the decoration in certain applications but firefox, open office etc don't have any.

i have followed advice from saint google and have tried disabling compiz , modifying compizsetting manager enabling windows decoration. i have also uninstalled compiz but no luck. 

i think there might be a issue with metacity as when i installed xfce i could see all the windows decoration.

i would really appreciate any advice in resolving this.

regards

---

### Post by binbash on 2009-02-24
go to compizconfig settings manager > workarounds plugin and untick legacy fullscreen support.And report if it works or not.

---

### Post by jawana on 2009-02-24
tried your advice, still not working.

---

### Post by jawana on 2009-02-26
i still don't have a solution, but i have discovered that if you right click and choose unmaximised you can get the windows decorations back. but as soon as you maximize you loose it again.

still if any ubuntu lovers have a better workable solution share it with me.


thanks

---

### Post by haile46 on 2009-02-27
You may have installed maximus. 
Remove it "sudo apt-get remove maximus" or configure it in gconf-editor apps>maximus

---

### Post by jawana on 2009-05-08
thank you very much, after uninstalling maximus. everthing is fine

---

