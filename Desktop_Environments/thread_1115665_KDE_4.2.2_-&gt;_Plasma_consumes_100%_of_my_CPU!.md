---
title: "KDE 4.2.2 -&gt; Plasma consumes 100% of my CPU!"
date: 2009-04-04
forum: Desktop Environments
---

### Post by CyberAngel on 2009-04-04
Hello,

I`ve just upgraded both of my computers (Laptop and Desktop) to KDE 4.2.2 from the ppa repositories but I have a problem with my Desktop one.

The "plasma" process eats all of my CPU resources and it is making the computer very slow of course when running everything else! Almost unusable.
I`m running the KDE desktop with or without the kwin effects and I have the same behavior.

The main difference in my computers is the graphics card.. My laptop (without the problem) has an ATI card and my Desktop (the problematic) has a NVidia card. Other than that both of them has 1GB of RAM and a single core amd64 processor (the laptop has the Turion series) running a 64bit kubuntu intrepid system.

Has anyone else noticed something like this or I`m all alone?
Any solution or suggestion?

Thanks

---

### Post by swiftscythe on 2009-04-04
I have the same problem as you with my laptop with a nvidia GeForce 9600M... I can work with the computer though, but the fan is working continuously... Hope they commit a patch to fix this ;)

---

### Post by CyberAngel on 2009-04-04
> **swiftscythe said:**
> I have the same problem as you with my laptop with a nvidia GeForce 9600M... I can work with the computer though, but the fan is working continuously... Hope they commit a patch to fix this ;)

At least I have some support :P
I`m not all alone :)

---

### Post by abn91c on 2009-04-04
try system settings>desktop>desktop effects>advanced>composting type and change to **XRender**, see if that helps

---

### Post by CyberAngel on 2009-04-04
> **abn91c said:**
> try system settings>desktop>desktop effects>advanced>composting type and change to **XRender**, see if that helps

But I have the desktop effects disabled and the problem is still here...

---

### Post by CyberAngel on 2009-04-04
SOLVED!

I created a new account and logged in to the computer that I had the problem.
Then I realized that the problem with that account was not there, so I logged back in again with my account and I started removing the plasmoids I had on my activity one by one and guess....

The Calendar plasmoid I had on my desktop was the problem! Now plasma is working fine again without eating all of my cpu resources!

---

### Post by swiftscythe on 2009-04-05
Yes you're right, the problem was caused by the calendar. (I also had that plasmoid!) Thaaaaaaaanks :)

---

### Post by Thomas Prague on 2009-04-08
Confirm. This bug has already been reported.
[https://bugs.kde.org/show_bug.cgi?id=188719](https://bugs.kde.org/show_bug.cgi?id=188719)

---

### Post by bradtem on 2009-09-27
> **swiftscythe said:**
> Yes you're right, the problem was caused by the calendar. (I also had that plasmoid!) Thaaaaaaaanks :)

I don't have the calendar (as far as I know) but I still see plasma often zooming up the CPU usage charts (though not at 100%) for no apparent reason.  Is there a way to list the plasmoids or other items that are running, to try to find the culprit?  I mean I can try to use top or ps in thread mode but they don't tell me that much.

---

