---
title: "Need help 7.10 is maxing out my laptop"
date: 2007-10-22
forum: Desktop Environments
---

### Post by timay91 on 2007-10-22
Hey all I just recently upgraded to 7.10 from 7.04 and now my computer is constantly maxed out at 97-100% when ever i move a window or open one. I'm not running compiz with any effects what so ever. So i'm guessing its the enviroment that its in xgl or fxgl or aiglx what ever it is. Can i disable it frome going into this enviroment at start up? i tried to put it into gnome but i just get the same problem.     

I had compiz working on my 7.04 with no problems an no cpu spikes like this. I just never enabled the 3d stuff

anyway i have an hp dv5129us laptop with a an ati radeon express 200m integrated graphics card if that helps

thanks,

NOOB  Tim

---

### Post by benerivo on 2007-10-22
I would guess it's some of the new startup programs that gutsy has. Take a look at 'Services' and 'Sessions' in the main menu, and disable anything to do with 'tracker', and also anything else that you might not need (i'm not too sure what else there may be as i'm in kde), and then reboot.

---

### Post by timay91 on 2007-10-22
I tried that but it's still just maxing my computer to the limit whenever I open new windows or even scroll down o a screen.

---

### Post by benerivo on 2007-10-23
Add the system / process monitor applet to your panel and check what process it is that is using so much of the cpu. Hopefully it's something that you don't need and can just kill.

---

### Post by indosupremacy on 2007-10-23
the same thing has happened to me,but,after i disabled tracker d,there's no more problem again...

---

### Post by timay91 on 2007-10-23
I alreay disabled the tracker but my comp is still maxed out. When I lokk at the process it says gnome-system monitor is only using 12% and XGL is using about 9% and nothing else is using up anything but when I move a window or scroll up and down in on google or anything else like a openoffice doc it gets real choppy and the cpu spikes when you look at system monitor/ cpu history.

---

