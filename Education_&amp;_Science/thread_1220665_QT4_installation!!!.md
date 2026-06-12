---
title: "QT4 installation!!!"
date: 2009-07-23
forum: Education &amp; Science
---

### Post by ajaymurthy123 on 2009-07-23
Hey there,i want to instal QT4 SDK.can anyone tell me how to proceed? I'v got the setup file downloaded which is--"qt-sdk-linux-x86-opensource-2009.03.1.bin".

---

### Post by whelanh on 2009-07-23
The Qt website where you downloaded the file gives you the steps ([http://www.qtsoftware.com/downloads/sdk-linux-x11-32bit-cpp):](http://www.qtsoftware.com/downloads/sdk-linux-x11-32bit-cpp):)

In a command shell (e.g., Konsole), type:

chmod u+x qt-sdk-linux-x86-opensource-2009.03.bin

Then:

./qt-sdk-linux-x86-opensource-2009.03.bin


An even better alternative is to install it from the repositories as then it will be automatically updated in the future.

Command is:
sudo aptitude install --with-recommends qtcreator


Best,
Hugh

---

