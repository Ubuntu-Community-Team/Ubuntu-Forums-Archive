---
title: "Launch pad and CCSM"
date: 2012-01-14
forum: Desktop Environments
---

### Post by chenxinghao on 2012-01-14
Installed Ubuntu 11.10 on an IBM ThinkCentre A50P desktop, along side with Windows XP Pro on the master HD, on the slave HD with dual-boot option several days ago, with the default settings (I did not key in anything to change) in the installation process. No tweaking on my part of any kind.

I have three questions related to the desktop:

(1) After opening the Home folder for the first time after the PC is turned on, the icons of the master and slave HDs would show up in the Launcher pad/bar, further crowding the space which is already limited. Functionally speaking, they are basically the same as the Home folder. Right-click on the HD icons in the Launcher produces the name of the HD and the "Eject" option. What can I do to not letting the two HD icons to appear in or to remove them after they pop into the Launcher space?

(2) I want to reduce the icon size in the Launcher. As some posts suggested I installed the CCSM via the Software Center and open it and changed the icon size from 48 to 32; clicked two more buttons following the instructions and closed the CCSM application. The icons 's size remain the same as before. Then I rebooted the PC and opened CCSM and it reads the icon size to 32; but the Launcher icons are still as big as before (at 48). What do I miss?

(3) How to rearrange the order of icons in the Launcher?

---

### Post by Double.J on 2012-01-14
Hi there, think I'm only going to be able to help with Q1! (sorry I gave up editing unity's compiz settings - I kept breaking it!) run CCSM, then experimental>show devices>change to never.

Sorry I can't be more help - anything else I offered would just be google knowledge, and I'm reluctant to change anything I don't need to atm with unity - cowardice! 

Hope it helps though!

---

### Post by Krytarik on 2012-01-14
1) Already sufficiently answered.

2) It seems you are running the fallback Unity 2D session, not the regular Unity. Googling for the specs of your system, I learned that it sports an ATI Radeon 9600 Pro video card, which, I'm afraid, isn't sufficient for running the regular Unity, hardware-wise (in case anyone suggests that, the proprietary driver doesn't support it anymore).

There are numerous ways to check/see if Unity 2D or the regular Unity is running, the most obvious and clear is checking the running processes:
```
ps ax |grep unity
```If a couple of processes with "unity-2d" in their names turn up, it's obviously Unity 2D.

3) Just drag & drop the respective launcher inside the Launcher to relocate it, you need to keep the mouse button pressed for 1 sec. before you can start dragging it. For more customization options of Unity 2D (!), please see this guide:

[http://www.tuxgarage.com/2011/10/customizing-unity-2d-ubuntu-natty.html](http://www.tuxgarage.com/2011/10/customizing-unity-2d-ubuntu-natty.html)

Regards.

---

### Post by chenxinghao on 2012-01-14
Thank you both for the inputs.
 
 
On (1) I recall that the first and last time I used CCSM there was an "experimental" entry in the selection. Now I cannot find it any more. What is the pathway to find this "experimental" entry in CCSM?
 
 
On (2) Typed "ps ax | grep unity" in a Terminal window and a number of "unity-2d-...." entries. So the search to reduce the size of Launcher icons on my this installation hits the dead end. I will live with it.
 
On (3) Tried and successful!

---

### Post by Krytarik on 2012-01-15
1) Oops, since you are running Unity 2D, not the regular Unity, you can't tweak that via CCSM either; forgot to get back to that question. :P For that, also refer to the guide I linked to.

---

### Post by Frogs Hair on 2012-01-15
This option is also available for Unity 2D. [http://www.addictivetips.com/ubuntu-linux-tips/myunity-comprehensive-unity-tweak-for-ubuntu-11-04-and-11-10/](http://www.addictivetips.com/ubuntu-linux-tips/myunity-comprehensive-unity-tweak-for-ubuntu-11-04-and-11-10/)

---

### Post by chenxinghao on 2012-01-15
Back to (1): opened CCSM and found the "experimental" tab and selected "Never" for Device; reboot to Ubuntu and opened the "Home folder" and the two HD icons appear in the Launcher soon after - basically the same as before: no effects on the CCSM selection in terms of Launcher icon appearences.
 
It all seems that CCSM is useless on my Ubuntu 11.10 installation.

---

### Post by MG&amp;TL on 2012-01-15
> **chenxinghao said:**
> Back to (1): opened CCSM and found the "experimental" tab and selected "Never" for Device; reboot to Ubuntu and opened the "Home folder" and the two HD icons appear in the Launcher soon after - basically the same as before: no effects on the CCSM selection in terms of Launcher icon appearences.
 
It all seems that CCSM is useless on my Ubuntu 11.10 installation.

It's all in the name of the application. "Compiz". Unity 3d is based around compiz, unity 2d, I believe, is not. Therefore tweaking compiz settings will have no effect. :( Sorry.

---

### Post by Krytarik on 2012-01-15
> **chenxinghao said:**
> Back to (1): opened CCSM and found the "experimental" tab and selected "Never" for Device; reboot to Ubuntu and opened the "Home folder" and the two HD icons appear in the Launcher soon after - basically the same as before: no effects on the CCSM selection in terms of Launcher icon appearences.

It all seems that CCSM is useless on my Ubuntu 11.10 installation.
This ;-) :
> **Krytarik said:**
> 1) Oops, since you are running Unity 2D, not the regular Unity, you can't tweak that via CCSM either; forgot to get back to that question. :P **For that, also refer to the guide I linked to.**

---

