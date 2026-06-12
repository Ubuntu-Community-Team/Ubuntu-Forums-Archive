---
title: "Windows can't be &quot;touched&quot;"
date: 2012-09-16
forum: Desktop Environments
---

### Post by JorgeGhersa on 2012-09-16
Hi everyone. I'm using Xubuntu 12.04.1 (but the same happens on Xubuntu 12.10 alpha) on a Asus T91MT Convertible netbook (i.e. with a propietary touchscreen). Everything is nice and responsive, but the window bars are unresponsive to the touchscreen: no clicking "X" to close, no moving them around or rolling them up, no resizing. All of this works, if done with the touchpad.

Any suggestions?

PS: Found this link:
[http://permalink.gmane.org/gmane.comp.xfce.user/26122](http://permalink.gmane.org/gmane.comp.xfce.user/26122)
...but i can't get much more from it.

---

### Post by Epodx64 on 2012-09-16
I don't have a touch screen and I haven't worked with many but you could try installing "tsconf" either through a terminal with ```
 sudo apt-get install tsconf 
``` or through the Software center add/remove whatever it's called in Xubuntu nowadays really that's about the extent of what I know about configuring touch screens on the *buntu family.

---

### Post by JorgeGhersa on 2012-09-17
Thanks for the answer... unfortunately, tsconf is already installed.

Besides, now i believe (as XFCE's Fourdan) that this behaviour is created by xfwm4 as it tries to "read" the touches as mouse clicks; since it's specific to the window borders... I'll see if i can dig up a solution with Xfce people. Thanks again!

---

### Post by schebe on 2013-02-23
Hello,
I'm also Xubuntu user for several years. I installed 12.10 just yesterday and I'm surprised how good Xubuntu works with my Lenovo Yoga 13 convertible ultrabook. The behavior of the windows that can't be closed using touchscreen by a button [x] is really uncomfortable. Is there any suggestion - it seems this thread is sleeping a longer time. I found another threads on xfce forum but none with a sufficient solution. 

Thanks
Dan

---

### Post by offgridguy on 2013-02-25
> **schebe said:**
> Hello,
I'm also Xubuntu user for several years. I installed 12.10 just yesterday and I'm surprised how good Xubuntu works with my Lenovo Yoga 13 convertible ultrabook. The behavior of the windows that can't be closed using touchscreen by a button [x] is really uncomfortable. Is there any suggestion - it seems this thread is sleeping a longer time. I found another threads on xfce forum but none with a sufficient solution. 

Thanks
Dan
I'm surprised that it works that well, as it wasn't designed as a touch OS.

---

### Post by schebe on 2013-02-27
ok, maybe "well" is too strong word, but I'm able to control almost all applications. Click, drag&drop and scroll works fine. Sure, there is no multi touch option. I think due to the amount of touch devices this time should OS developer try how behave his system with touchscreen even when OS is not primarily targeted for touch devices. Its really pity for Xubuntu.

---

