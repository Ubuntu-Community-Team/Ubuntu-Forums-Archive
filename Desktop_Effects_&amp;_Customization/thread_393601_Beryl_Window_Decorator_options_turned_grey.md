---
title: "Beryl Window Decorator options turned grey ???"
date: 2007-03-25
forum: Desktop Effects &amp; Customization
---

### Post by glenn69 on 2007-03-25
I am running Xubuntu 6.10.  Nvidia driver 9755.

I installed beryl and it operated fine, but now it simply doesn't work.  I can't correlate it with an upgrade or anything else.  It just stopped working.

If I access beryl-manager by right clicking the icon and following the drop down menu. the options of reload window decorator and select window decorator are disabled (greyed out)  If I select - Select Window Manager I am given 2 options * Beryl and * XFCE Window Manager.  XFCE window manager is selected, but if I select Beryl the screen redraws itself then nothing.  i cannot get beryl to manage the screen anymore.  What can I do to troubleshoot?

---

### Post by Waappu on 2007-03-26
Hi

If you type in terminal ```
beryl
```what errors/messages it gives you?

---

### Post by glenn69 on 2007-03-26
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension

---

### Post by Waappu on 2007-03-27
Hi

Add these lines to your xorg.conf
```
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

### Post by lazyrussian on 2007-04-16
I am having a similar problem. Inserting the code mentioned above stops beryl from working. Instead of Enable, I had the word false before.

---

