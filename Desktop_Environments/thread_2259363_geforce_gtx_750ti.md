---
title: "geforce gtx 750ti"
date: 2015-01-03
forum: Desktop Environments
---

### Post by elliott4 on 2015-01-03
The computer I built is running windows and ubuntu dually. I have a geforce gtx 750ti graphics card from evga. Ubuntu is running fine but the screen has poor resolution and it looks ugly. My windows install looked the same way until I installed the nvidia drivers, now it looks great. My problem is that I cannot download any drivers for my gpu. I would appreciate any helo. (EDIT) I have solved my problem using ppa. THanks to all that responded

---

### Post by papibe on 2015-01-03
Hi elliott4.

Is there any driver offered in 'Additional Drivers' 

Regards.

---

### Post by grahammechanical on 2015-01-03
If you installed Ubuntu and ticked the box "Install third party software" then the installer would have automatically installed an Nvidia driver. To check go to About this computer or System Settings>Details and see what is listed under Graphics. I am not using Nvidia proprietary video drivers and I get Gallium 0.4 on NVA5. Gallium = open source video driver. NVA5 = Nvidia code name for GT220.

What monitor are you using and what connection to the monitor? A VGA connection cannot give the same high definition that DVI or HMDI gives. I recently purchased a HD TV to use as a monitor and at first I had to use a VGA cable as I did not have an HDMI cable. I could not get the high screen resolution the the monitor was capable of until I used a HDMI cable.

Regards.

---

### Post by Bashing-om on 2015-01-04
elliott4; Hi !

linux playing catch up as Nvidia is slow to offer direct support to us for their newer hard ware.

Your 750ti needs version 334.xx or later, and it's not in the Trusty repo.
One way to get the needed driver and remain within the 'buntu support structure:
so you're going to have to use a PPA:
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
Or one may do so direct from Nvidia; More here:
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)

And the latest info on this situation:
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)

So, the bottom line is
[INDENT][INDENT][INDENT]yes, it is doable
[/INDENT][/INDENT][/INDENT]

---

### Post by elliott4 on 2015-01-04
I am using an hdmi and know that isnt the issue because it works fine on windows. thank you for the suggestion, i will try it as soon as im done with homework.

---

### Post by elliott4 on 2015-01-04
I am not sure and will check after I am done with the homework I neglected over break. Thank you and I will get back shortly.

---

### Post by elliott4 on 2015-01-05
No there are no drivers offered.

---

### Post by elliott4 on 2015-01-05
VESA: GM107 Board - 20100050 THese are the graphics im supposedly using. HOw would I install Gallium?

---

### Post by Bashing-om on 2015-01-05
elliott4; hey;

Re-read my post #4 . There are no drivers for that card available in the repository, so yes "No there are no drivers offered " is true.

Driver can be installed:
see also:
[http://ubuntuforums.org/showthread.php?t=2259214](http://ubuntuforums.org/showthread.php?t=2259214)

[INDENT][INDENT]it is doable
[/INDENT][/INDENT]

---

