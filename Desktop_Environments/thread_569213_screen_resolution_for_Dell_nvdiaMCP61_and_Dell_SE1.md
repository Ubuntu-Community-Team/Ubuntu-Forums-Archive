---
title: "screen resolution for Dell nvdiaMCP61 and Dell SE198WFPV monitor"
date: 2007-10-06
forum: Desktop Environments
---

### Post by newwithubu on 2007-10-06
I just installed Ubuntu in my new dell inspiron 531S pc... i am hoping to use Ubuntu as my default operating system .. it works fine except i cant maximize the resolution .. the maximum i can go is 1024by768...which is fine but it is not as sharp as 1500 resolution.. when i use vista the resolution is 1500 and it looks very sharp.. how do i make it work under high resolution..

video card is nvdia mcp61 and monitor is 198wfpv ( it is the wide screen).. 
THanks

---

### Post by MrFSL on 2007-10-06
Have you read here:
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

Also, once you have correct drivers installed and correct settings for your Display a:
```
sudo dpkg-reconfigure xserver-xorg
```will probably get you where you need.

---

### Post by ryanVickers on 2007-10-06
This is (sadly) totally normal for ubuntu and it tends to happen to everyone.  To fix it, try installing the video drivers and see if it adds more options.  If not, you may have to add them manually in the /etc/X11/xorg.conf file and then restart X (ctrl alt backspace)

---

