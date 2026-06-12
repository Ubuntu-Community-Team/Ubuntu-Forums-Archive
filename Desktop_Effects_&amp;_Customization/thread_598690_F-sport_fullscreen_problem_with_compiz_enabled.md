---
title: "F-sport fullscreen problem with compiz enabled"
date: 2007-10-31
forum: Desktop Effects &amp; Customization
---

### Post by jlinho on 2007-10-31
Hi, 

with** Desktop Effects enabled** and if I try to see my photos in **Fullscreen mode with F-spot** , photos doesn't display correctly.  For instance if I click on the "slideshow" button, there is a mini-slideshow (maybe 100x100 pixels) on the bottom-right corner of my screen that hovers on top of my main f-spot window .... Very strange.

If I disable desktop effects I have no problems.

Do you have the same problem ?

Please let me know..

Thanks for your attention...

NB: My graphic card is a** NVidia 8400 GS**. I also have some other little Nvidia driver issues. For instance the  "Screens and Graphics" dialog displays two possible refresh rates "52 Hz and 54 Hz", but the "Monitor" section of my xorg.conf is totally ok (HorizSync, VerticalRefresh, Modelines ar ok)... If I use the" nv" driver instead of" nvidia" I have the choice between the right refresh rates in the "Screens and Graphics" dialog box. If I use the nvidia-settings tool I can select the right refresh rates but when I select one of them ==> PC freeze (even Ctrl+Amt+Backspace doesn't work)

---

### Post by jlinho on 2007-11-04
Ok. The bug is already  in launchpad
here: [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/105150](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/105150)
and here: [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/130085](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/130085)
and also here : [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/149291](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/149291)

---

