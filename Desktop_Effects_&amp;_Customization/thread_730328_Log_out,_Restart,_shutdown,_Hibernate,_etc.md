---
title: "Log out, Restart, shutdown, Hibernate, etc"
date: 2008-03-20
forum: Desktop Effects &amp; Customization
---

### Post by huviduc on 2008-03-20
I am having issues with all power functions. The only way to reboot is sudo halt. This works for now but i would like to fix the issue. I have tried several work arounds and nothing helps. When logging out, the screen goes blank and the fan RPM's shoot up and it just sits there and you can not do anything. When hibernating, i get the errors in the attached images. Switch user does the same as logout. Any ideas?

---

### Post by theparticle010 on 2008-03-20
do you have a dell 1501 or a computer with the Radeon Xpress 1150 gfx card and the fgrlx driver enabled?

---

### Post by huviduc on 2008-03-20
i have Compaq with an ATI 200m and the fglrx driver ( i believe, i installed beryl and drivers over a year ago, and tried several methods before success). Log out hasn't worked since, but hibernate used too. it does eventually hibernate now, but i get those strange errors and a loooong pause.

---

### Post by huviduc on 2008-03-21
anyone?

---

### Post by theparticle010 on 2008-03-22
There is an Xpress driver at the ATI site, it's been updated, I really think that you have the Xpress 200 card, the fgrlx driver has support for Radeon cards, but it has a glitch in the Sleep And Hibernate, with smaller gfx cards you get REALLY bad support, so just pick up the driver here:



[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)


It's under: Linux x86 > Integrated/Motherboard > Radeon Xpress 200.

Sleep works, but the hibernate is still really slow. ( Thats what I've read )

---

