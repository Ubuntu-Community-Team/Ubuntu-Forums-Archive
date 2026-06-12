---
title: "Ubuntu Screen Resolution VMware"
date: 2006-06-02
forum: Desktop Environments
---

### Post by jdt05 on 2006-06-02
Hey everybody, I'm reasonably new to linux and this is my first time with ubuntu. I use Mandriva in our university labs.

I've just installed Ubuntu 6.06 in VMware and the maximum resolution i can get is 1024x768.

Is this a VMware problem or something I can't configure correctly in Ubuntu?

Any help would be appreciated, thanks very much

---

### Post by ferdush on 2006-06-09
Dude, I've also the same screen resolution from with VMWARE. Everytime I need to scroll up-down and left-right. I changed the screen resoltion but it did not work. I installed ms windows 2003 and there is no problem with screen resolution. I mean I don't have to scroll. I wanted to learn Ubuntu on VMWARE but it's not easy there. I am requesting any advanced vmware user or ubuntu folks to help both of us.
-Ferdush

---

### Post by chanders on 2006-06-09
In the vmx file there are settings for max resolutions. Set it to what you want. Make sure however you set standard resolutions for your display eg. 800x600 1024x768, 1600x1200 etc

---

### Post by jdt05 on 2006-06-09
I've fixed it. You can the way chanders said. I found a guide on hear on how to do it. VMware only works in 16 bit so make sure you chose when you are configuring it.

Simply changing the .xorg.conf file did not work for me. I reconfigured the Xserver.

I followed this guide,

[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

