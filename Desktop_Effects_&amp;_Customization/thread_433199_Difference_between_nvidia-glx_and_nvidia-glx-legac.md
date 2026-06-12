---
title: "Difference between nvidia-glx and nvidia-glx-legacy?"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by ubnewbie2 on 2007-05-04
OK, I installed beryl on feisty as per many how tos and stuff I read.   It isn't starting right. It just removes the 
Window's borders and the desktop crashes (ctrl-alt-backspace to restart back to normal gnome).  

Also, trying to start desktop effects crashes gnome (the panels disappear) and again a ctrl-alt-backspace is required.

My nvidia drivers are in use, according to the restricted drivers manager, but I don't see an nvidia splash screen as X starts.
I read somewhere about reinstalling the drivers and when I try I get the information below.


```
$ sudo apt-get install nvidia-glx --reinstall
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-kernel-source
The following packages will be REMOVED:
  nvidia-glx-legacy
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 4492kB of archives.
After unpacking 3658kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```


So, what is the difference, and can I go ahead and install the new package (my video card is an old nvidia TNT2 M64)?

---

### Post by BoneKracker on 2007-05-04
I think with the TNT 64 you probably need the legacy drivers.

---

### Post by ubnewbie2 on 2007-05-04
> **BoneKracker said:**
> I think with the TNT 64 you probably need the legacy drivers.

I think you are right.  I decided to risk trying the real ones, and X would not start.  I have to remove the new ones and put the legacy ones back to get it to work again.

I also noticed the legacy drivers are not the 9000 servies - they are 7000.  So does that mean I can't use any desktop effects at all?

---

### Post by Ric95 on 2007-05-04
Legacy drivers are for the older video cards. Usually those older card have the fuctions you need, but may run noticably slower. I found some older cards are very trouble free if you set the color depth to 16 bit.
that driver nuber 7xxx , or 9xxx just refers to the driver, not the card. ( odd...)
Here is a list of video card that need the legacy driver.
[http://www.nvidia.com/object/IO_32667.html]("http://www.nvidia.com/object/IO_32667.html")

---

### Post by BoneKracker on 2007-05-06
I have glx/dri on older cards, including an nvidia TNT2 (32MB) and an ATI Rage 128 Pro (16 MB).  My experience with compositing window managers on these is that they run, but they produce a heavy enough load that normal video effects like dragging windows or scrolling a browser window are slow or don't look right.

So my advice would be to go ahead and use the drivers, use 3-d acceleration, but don't waste the resources on the "desktop effects" which are of little value anyway.

---

### Post by ubnewbie2 on 2007-05-06
Yes that's about what I have concluded as well.  Thanks.

---

