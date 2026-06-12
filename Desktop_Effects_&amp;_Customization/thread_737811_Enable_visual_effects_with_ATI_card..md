---
title: "Enable visual effects with ATI card."
date: 2008-03-27
forum: Desktop Effects &amp; Customization
---

### Post by ZerXonE on 2008-03-27
I installed Ubuntu 7.10 yesterday and I've been very happy with the change from Windows. There is one problem which I have encountered and I've spent several hours trying to find an answer with no luck.

The visual effects can not be loaded and I get a message which reads "the Composite extension is not available". My graphics card is an ATI Radeon 9700pro which has the restricted driver "fglrx" installed. The visual effects works fine with the lice cd or by disabling the restricted driver. I've found out that many have faced the same problem and most have got it working by installing "xserver-xgl". That does indeed enable the effects but another problem occurs; the system freezes when moving windows or starting Firefox. When I uninstall "xserver-xgl" it goes back to normal.

Is there another solution to this problem(using other drivers perhaps?) or is installing "xserver-xgl" my only option? If so, is there any way to fix the freeze problem?

---

### Post by Lantesh on 2008-03-28
Edit: deleted comment due to new information I didn't know about posted below.

---

### Post by el-mar01 on 2008-03-28
Try the latest 8.3 drivers ... when I installed 8.3 I no longer needed to have xserver-xgl installed. (I think) ... also download Envy which makes driver installation easy.

---

### Post by ZerXonE on 2008-03-28
> **el-mar01 said:**
> Try the latest 8.3 drivers ... when I installed 8.3 I no longer needed to have xserver-xgl installed. (I think) ... also download Envy which makes driver installation easy.

I installed the newest driver from ATI and it's working now. I haven't tested out all of my applications yet but if everything works as it should then thank you;)

---

