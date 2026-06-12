---
title: "[SOLVED] Desktop with Kernel 2.6.24-17-server, Is this 64 bit now?"
date: 2008-05-30
forum: Desktop Environments
---

### Post by heatpumpcontrol on 2008-05-30
Hello,

To solve the issue of limited ram in my Desktop 32 bit installation, I followed a topic that advised me to install the server kernel which is a 64 bit kernel. I have done so and I can now see my 4 GB of ram (well 3.9) instead of just 3.2 GB. 

My question is however, am I now running 64 bit or is my installation of still a 32 bit? Everything else seems to be the same but for future app installs I want to make sure I select correctly between i386-32 bit or x86_64 bit.

[IMG]http://ubuntuforums.org/picture.php?albumid=211&pictureid=661[/IMG]

Thanks guys

---

### Post by heatpumpcontrol on 2008-05-31
bump

---

### Post by shae on 2008-06-02
You are still using 32bit.

---

### Post by sdennie on 2008-06-03
As said above, you are still running 32-bit.  Installing the server kernel allows you to use 4G of RAM because it enables something called PAE.  You can think of that as like a hybrid 36-bit kernel but, all applications will run as 32-bit and you can still consider your machine as being 32-bit.

---

### Post by heatpumpcontrol on 2008-06-05
Great and thank you both!

happy surfing :)

---

