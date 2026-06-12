---
title: "unity"
date: 2012-01-17
forum: Desktop Environments
---

### Post by tj107us on 2012-01-17
im running ubuntu 11.10 and its using the Unity 2D, are there a better version of Unity like Unity 3D or something?

---

### Post by grahammechanical on 2012-01-17
Yes there is but does your hardware support it? Have you used the Additional Drivers to activate any proprietary video drivers for your video card? What video or graphic card do you have by the way?

Activating a proprietary video driver may allow you to run Unity 3D if your video card is capable of it. After activating or installing the driver log out and as you log back in click on the cog icon. If you see Ubuntu listed with Ubuntu 2D underneath, then click on Ubuntu and when the desktop loads you will be using Unity 3D.

To modify how 3D works you need to install CompizConfig Settings Manager. Search for CCSM in the Ubuntu Software Centre. Once it is installed you load it from the Dash by searching for CCSM. When it is open look for Ubuntu Unity Plugin. Make sure that it has a check mark against it and then click on the words Ubuntu Unity Plugin to get options to modify Unity behaviour.

Regards.

---

### Post by tj107us on 2012-01-18
Its a lappy with a 7400 nevida and an intel t5600 cpu

---

### Post by Frogs Hair on 2012-01-18
Run the following command to see that unity is supported .```
/usr/lib/nux/unity_support_test -p
```

There have been Unity 3D compatibility problems reported with Nvidia 7 series cards.

---

### Post by tj107us on 2012-01-18
My computer dont support it!!

---

### Post by phibxr on 2012-01-19
What drivers are you running? You may need to install the restricted NVIDIA-drivers for proper Unity compatibility.

---

