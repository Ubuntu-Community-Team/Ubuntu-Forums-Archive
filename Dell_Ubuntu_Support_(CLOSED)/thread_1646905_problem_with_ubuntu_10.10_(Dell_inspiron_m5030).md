---
title: "problem with ubuntu 10.10 (Dell inspiron m5030)"
date: 2010-12-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mpetrovickg on 2010-12-16
Hi!

Few days ago, I have bought a dell inspiron m5030 (Processor: AMD Athlon(tm) II P340 Dual-Core, Main board: AMD M880G, Grafic card:   ATI Mobility Radeon HD 4200). When I tried to install ubuntu 10.10 (I selected option to install from live cd), I got a black screen with blinking white dash, and installation has stopped. Does somebody knew how to solve that problem?

P.S: I have also tried to upgrade from 10.04 to 10.10. When I had restarted a PC, I got the same black screen with blinking white dash.

P.S2: Sorry for my English.

---

### Post by larry139 on 2010-12-18
Hi all,

I am having the same problem. I am able to get puppy Linux, Dream Linux, and Fedora to run.  No version of Ubuntu, or Debian will load. Both CD and USB. I really want to run Ubuntu on this laptop. Hope someone can help.

Larry

---

### Post by mpetrovickg on 2010-12-18
Hi,

after I had turned off ACPI mode(during installation), I was able to install system. Now, when I want to start system in grub, I am getting the same black screen with blinking white dash.
Any ideas how to solve this problem with ACPI?

---

### Post by larry139 on 2010-12-18
FYI I was able to get Ubuntu 10.04 LTS to run on my Dell Inspiron M5030 live off the USB.  I am going to attempt to install it.

Larry

---

### Post by wilee-nilee on 2010-12-18
So if you guys when powering on 10.10 immediately hold the shift key down to see the grub menu if you're not already. 

At the grub menu hit e which brings up a edit screen. Using the arrow keys on the keyboard to get to the line that has no splash at the end remove no splash and put nomodeset in there. Hit crtl-x to boot from there.

This is a per-session boot into the safe graphics mode to see if a driver can be found and installed. You can do all the same things the screen will be limited to 800x600 I think is all.

I suspect it is a graphics driver needed.

---

### Post by mpetrovickg on 2010-12-19
> **wilee-nilee said:**
> So if you guys when powering on 10.10 immediately hold the shift key down to see the grub menu if you're not already. 

At the grub menu hit e which brings up a edit screen. Using the arrow keys on the keyboard to get to the line that has no splash at the end remove no splash and put nomodeset in there. Hit crtl-x to boot from there.

This is a per-session boot into the safe graphics mode to see if a driver can be found and installed. You can do all the same things the screen will be limited to 800x600 I think is all.

I suspect it is a graphics driver needed.

That doesn't work. :(

Edit:
Problem is solved! :)
I have edited grub as you said. But I wrote "acpi=off" instead of "nomodeset".

---

### Post by wgarider on 2010-12-26
> **mpetrovickg said:**
> That doesn't work. :(

Edit:
Problem is solved! :)
I have edited grub as you said. But I wrote "acpi=off" instead of "nomodeset".

Just bought one of these - thanks all for the great troubleshooting.

---

### Post by frankmb on 2011-01-21
> **mpetrovickg said:**
> Hi!

Few days ago, I have bought a dell inspiron m5030 (Processor: AMD Athlon(tm) II P340 Dual-Core, Main board: AMD M880G, Grafic card:   ATI Mobility Radeon HD 4200). When I tried to install ubuntu 10.10 (I selected option to install from live cd), I got a black screen with blinking white dash, and installation has stopped. Does somebody knew how to solve that problem?

P.S: I have also tried to upgrade from 10.04 to 10.10. When I had restarted a PC, I got the same black screen with blinking white dash.

P.S2: Sorry for my English.
i've got the very same issue with my m5030, 
y downloaded the 11.04 beta iso, and installed it.
y think it has a newer acpi support or something, cuz it worked without editting a thing.

then booted ok up to de gdm login screen, thats where it hanged when i tryied to log in with unity o ubuntu clasic desktop.
but it did ok when i changed to the ubuntu clasic desktop (no efect) option.

everything worked just fine so far, i am donwloading and installing the FGLRX (propietary graphic driver) as i type.

hope you guys find this usefull and good luck with your m5030's.

---

### Post by holch on 2011-04-25
> then booted ok up to de gdm login screen, thats where it hanged when i tryied to log in with unity o ubuntu clasic desktop.
but it did ok when i changed to the ubuntu clasic desktop (no efect) option.

I installed 11.04 as well and it worked fine, but after login in I just can see the background image and the cursor.

How do I start ubuntu with the classic desktop?

---

### Post by holch on 2011-04-25
Never mind, found the option to boot the classic screen without effects and I was able to login.

Also downloading the new driver. Let's see what happens. If it won't work I'll have to find a way to boot the classic screeen without effects automatically, because the installation is for a women with more than 80 years and I'll really have to make it as easy as possible for her to access Skype and Facebook (!!!)...

---

### Post by logicscience on 2011-06-02
> **holch said:**
> Never mind, found the option to boot the classic screen without effects and I was able to login.

Also downloading the new driver. Let's see what happens. .

Hi, how did you find that option please and how did it go with the new drivers, what did you download?

---

### Post by theOGRE on 2012-02-05
@logicscience:  After picking your name and before you put your password, click the little gear icon and choose your desktop.

---

### Post by circleinsideabox on 2013-02-24
> **mpetrovickg said:**
> That doesn't work. :(

Edit:
Problem is solved! :)
I have edited grub as you said. But I wrote "acpi=off" instead of "nomodeset".

this worked for me as well on an INSPIRON M5030, thank you very much

---

