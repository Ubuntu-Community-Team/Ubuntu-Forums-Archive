---
title: "Dual Screen Problem"
date: 2009-02-19
forum: Desktop Environments
---

### Post by huruixd on 2009-02-19
Another curious question:

I have a 12'1 wide screen laptop with Ubuntu 8.10, plus a 21" Samsung SyncMaster 213T LCD. I would like to connect the 21" screen to my laptop and get it to display papers while I am working on the laptop. I guess it could be a dual screen problem.

Does anyone know how to configure it? A step by step guide is appreciated. Thank you.

---

### Post by Regnulify on 2009-02-19
If you have an Nvidia card with the proprietary driver you can use the NVidia X Server Settings in System Administration. The second menu item "X Server Display Configuration" will show both monitors. Select the disabled monitor and click configure. Then set the option to TwinView (one big desktop). Click ok then apply on the next page. you can adjust position and resolution from here. 

If !NVidia then you can use the System Preference Screen Resolution Applet. It should work in a similar (but simpler) manner.

If you don't see both displays then you are having issues detecting the second monitor and I am unable to help with that.

---

### Post by huruixd on 2009-02-19
It is an integrated video card: Intel X4500.

---

