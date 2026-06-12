---
title: "konqueror freezes X"
date: 2006-01-28
forum: Desktop Environments
---

### Post by yoshic on 2006-01-28
hi everybody, i've got a  problem with konqueror.

first i'm using an nv gforce 4 mx 440, kernel 2.6.15 with ck1 patch, an the nvidia 7667 driver compiled.

if i enable the render accel option or NvAgp option in the xorg.conf and start konqueror, it crashes my x. even kdm sometimes does too... :confused: :confused: 

i'm confussed, please help ! :cry:

EDIT:
no problem guys, if any1 has this problem too, this is the way to solve it:
Add
```
 Option "NvAgp" "2" 
```
to the "Device" section for the NVidia card, in XF86Config. The above option just says to use the Linux agpgart module instead of Nvidia's own. Thanks to Scott Lanham for this advice.

---

