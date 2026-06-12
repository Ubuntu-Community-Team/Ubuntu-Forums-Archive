---
title: "X Server Screen Area Problem"
date: 2008-10-22
forum: Desktop Environments
---

### Post by camoanimal on 2008-10-22
OK everyone, here is the deal.  I have any HP laptop with a screen resolution of 1280x800 @ 60 Hz.  Today I tried EnvyNG at installing the latest drivers for my videocard (NVidia 7400) and after rebooting the X server crashed leaving me to restart my system again.  Apon restarting my computer into Ubuntu my GDM screen was over inflated to be off the screen.  I could only see the top left corner of the login panel.  I logged in and went to adjust the screen resolution assuming the most likely being that the screen resolution was too high and X overcompensated (or something to that effect).  But it was set at 1280x800 @ 50 Hz and my desktop too was inflated so that about 45% was out of the range of my screen.  How would I go about fixing this problem?  I have already checked the Xorg.conf file and everything is set to the native resolution of 1280x800.

Help please :)

---

### Post by kilroy423 on 2008-10-23
I had a similar problem with my laptop.  It detected as 800x600 on boot.  I went to a vty and ran 
```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by stevand on 2008-10-26
Hey guys,
I have a problem of a similar type. Namely, some of my applications do not work. I can run Paraview, Tetview and other similar applications. However, these applications give a picture only when I click on the mouse on the figure and move it through the GUI. I have not had this problem with Ubuntu 6.0 . My card is ATI Radeon X600, and I am using this accelerated drives for 2D and 3 D. Is this problem? or how to find what is wrong?
thanks a lot 
steve

---

### Post by tabarraei on 2008-11-02
Hi Guys,

I have the same serious problem, I had ubuntu 7.10 and I did not update to ubuntu 8.04, because I experienced many problems with it. Then I heard that in the new release of 8.10 many bugs are fixed. So I updated into it. Now I have the most serious problems with this release. I really don't want to format my hard drive to go back to a lower version. so please help.

**My problem is** that my system after being upgraded into 8.10 the screen resolution fell on 800*600.  everything is huge and I did not found a useful help on the Internet. would please help me if your problem was resolved. I tried the above solutions. did not work. disappointed. 
my graphical card is :  VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

thanks
HR.T

---

