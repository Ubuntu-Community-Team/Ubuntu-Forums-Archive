---
title: "Will my laptop be fully Usable with linux?"
date: 2009-01-30
forum: General Help
---

### Post by godfromdfo on 2009-01-30
64bit amd athlon x2 dual core cpu
x1200 ati radeon gpu
3gb ram
200gb hdd
Realtek RTL8187B Wireless 802.11b/g 54mbps USB 2.0 network adapter

Will all that hardware work ok with ubuntu or would I have problems? definitly need the internet to work.. please help guys, thanks :)

---

### Post by TheLions on 2009-01-30
ATI may give you a headache but cannot tell you for sure because i don't own x1200

also tell us which soundcard do you have, sometimes soundcards are problem.

---

### Post by khedron on 2009-01-30
What you should do is get the installation CD. When you use it, it runs Ubuntu off the CD before you install, so you can see whether it works.

Check:
-internet
-sound
-your monitor resolution is ok
amongst others.

---

### Post by estyles on 2009-01-30
Just the fact that you say Laptop would cause me to reflexively answer "no."  Try it with the LiveCD first and see if it works right.

---

### Post by godfromdfo on 2009-01-30
thanks for the live cd tip guys, is there a certain version I should get?

---

### Post by dabl on 2009-01-30
Any will run, but the 8.10 64-bit would be the most current and suitable for your CPU.  You might want to try both Ubuntu and Kubuntu and see which is best for you.  ;)

---

### Post by godfromdfo on 2009-01-30
> **dabl said:**
> Any will run, but the 8.10 64-bit would be the most current and suitable for your CPU.  You might want to try both Ubuntu and Kubuntu and see which is best for you.  ;)

Thank you, oh quick questions..

1: Is there a live cd/dvd for the 64bit one?

2: can the 64bit one do all those cool graphic things like burning windows like the 32bit one? lol

edit: by burning windows I mean window animations that look like the windows burning when you close it >_<

---

### Post by Maheriano on 2009-01-30
> **godfromdfo said:**
> Thank you, oh quick questions..

1: Is there a live cd/dvd for the 64bit one?

2: can the 64bit one do all those cool graphic things like burning windows like the 32bit one? lol

edit: by burning windows I mean window animations that look like the windows burning when you close it >_<

[www.ubuntu.com](www.ubuntu.com) has .iso downloads for both 32 bit and 64 bit Live CD.

---

### Post by godfromdfo on 2009-01-30
thanks :) will take half hour to download... 0_o *prays it works*

I'll give you guys an update in a hours time..

oh and can this 64bit one work all apps even 32bit ones? windows sometimes cant so thought I best ask XD

---

### Post by sedawk on 2009-01-30
I recommend a 32-bit version because you want to use USB WLAN and
drivers for 32-bit have been working better and I'm not sure that
the ndiswrapper (in case you need it for WLAN) works with 64-bit.

ATI provides graphic drivers, so graphics should be okay.
You might need to turn of Compiz, there are some issues
with video flickering and OpenGL games when compiz is active.

Check if someone already tested linux on our laptop model:

[http://www.linux-laptop.net/](http://www.linux-laptop.net/)
[http://tuxmobil.org/](http://tuxmobil.org/)

It is most likely that Ubuntu will run, but some small stuff
might drive you crazy:
What most likely will not work is the modem in your laptop (if any).
Special keys might not work. You might see shorter battery life.
Some exotic hardware build into your laptop might not work (webcam).
Suspend-modes might be tricky.

---

### Post by godfromdfo on 2009-01-30
my laptop is on neither of the sites its a L300D Pro..

---

### Post by Xamiga on 2009-01-30
I'm running 8.10 32-bit on an A215-S5080 (think so, cant remember) - anyway ATI, 1200 Radon.  I definitely need the restricted driver for the video.  Terrible without.
Same wireless card, works ok.

I don't know if the restricted driver is availiable for 64-bit.
Hope it works 4u.

---

### Post by godfromdfo on 2009-01-30
> **Xamiga said:**
> I'm running 8.10 32-bit on an A215-S5080 (think so, cant remember) - anyway ATI, 1200 Radon.  I definitely need the restricted driver for the video.  Terrible without.
Same wireless card, works ok.

I don't know if the restricted driver is availiable for 64-bit.
Hope it works 4u.

ok, all my hardware works I think.. the graphics card might be working ok? I could put in on extra special in display thing and the resolution looks ok.. one question.. how do I set up an internet connection? on windows you just click on the icon... find network.. enter password.. but on here im stuck, please explain what I need to do? thanks :>

---

### Post by Maheriano on 2009-01-30
> **godfromdfo said:**
> ok, all my hardware works I think.. the graphics card might be working ok? I could put in on extra special in display thing and the resolution looks ok.. one question.. how do I set up an internet connection? on windows you just click on the icon... find network.. enter password.. but on here im stuck, please explain what I need to do? thanks :>

It's likely that it'll have to install a proprietary driver for the wireless. I know when I installed 8.1 on my Dell D600 2 weeks ago it wouldn't let me connect to the internet. Then after plugging it into the wired connection and doing all the updates (about 300), it rebooted and told me there's a proprietary driver for the wireless. I downloaded it and it gave me an icon on the panel that let me see all the wireless connections around me. Try that.

---

