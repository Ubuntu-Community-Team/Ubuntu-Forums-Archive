---
title: "Unity?????"
date: 2011-05-13
forum: Desktop Environments
---

### Post by JPman on 2011-05-13
I do not understand something here.   Unity is the new standard desktop?  I just installed 11.4 and cannot boot into it.   I get a message saying something like "inadequate hardware please select classic....".   OK so here I am wondering.

I've read everything I can find regarding Unity and no where is any hardware mentioned except that it was developed for netbooks.   No one else seems to have this problem.   I probably will not like Unity but I don't like not understanding something.   Is Unity more than just the new menus?

What is all this about "special hardware"?  My computer is not an 

antique.   

???????????????:confused::confused::confused::confused:

Thanks

---

### Post by tajreed on 2011-05-13
You're video card must support 3-d in order to use Unity.

---

### Post by ajgreeny on 2011-05-13
> **tajreed said:**
> You're video card must support 3-d in order to use Unity.
It's a bit more complicated than that!

I have a video card which works superbly in 10.04 and runs compiz with absolutely no problem, but when I try 11.04 it defaults to the classic desktop.  This is running the live CD, I admit, but the graphic card is an old ati which uses the open source radeon driver, so it is nothing to do with the proprietary driver requirement, which I believe is a problem in the live CD for nvidia cards.

At the moment I am not prepared to try 11.04 as an install, so will probably wait for the next couple of ubuntu versions before I move to a new version.

From what I have seen on my netbook, which will run unity as a live USB, unity is certainly not for me at the moment as it is not nearly configurable enough.  I use a very non standard layout of gnome classic at the moment with only a single panel, and use single clicks to activate, so unity is much slower for me to use than the one click I need to get anything running.

---

### Post by kn0w-b1nary on 2011-05-13
Try unity-2d
OR try Xubuntu 11.04.

---

### Post by Frogs Hair on 2011-05-13
I was required to install a proprietary driver for my 8 series Nvidia graphics card to boot Unity . I would have installed this driver anyway.

I received the same message as the op on the first boot and with the driver installed it defaults to Unity at boot.

---

### Post by coffeecat on 2011-05-13
@JPman, it's the video card/driver combination that is important. As a general rule (and slightly over-simplified):

Most Intel video chipsets will give you Unity out of the box.

Many ATI chipsets with the default open source driver give you Unity out of the box. ATI graphics on my desktop and a laptop work just fine.

The default open source nouveau driver does not support 3d out-of-the-box. For nvidia cards you can install either an experimental package to get 3d working with the nouveau driver or install the proprietary nvidia driver.

What graphics card do you have?

> **JPman said:**
> I probably will not like Unity

That's the ticket! A nice positive, optimistic attitude. :wink: Give it time. Many people, myself included, didn't like Unity at first, but it has grown on them. I much prefer it to the old gnome desktop now.

---

### Post by Blasphemist on 2011-05-13
This describes the video requirements for 3D Unity.
[https://wiki.edubuntu.org/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.edubuntu.org/DemystifyingUnityGraphicsHardwareRequirements)
This is from the above link.
```
/usr/lib/nux/unity_support_test -p
```
You need to know what gpu you have. This will tell you if you don't already know.
```
sudo lshw -c Display
```
Please post the results of that for more specific help.

---

### Post by ghostborg on 2011-05-13
I think you have to go into the Additional Drivers and install the appropriate driver. This is located by left clicking the power button top right of the panel and selecting System Settings which brings up the Control Center. Select Hardware on the left and you should then see Additional Drivers toward the right.

---

