---
title: "Odd Artifacts"
date: 2009-05-01
forum: Desktop Environments
---

### Post by Sevets on 2009-05-01
Hello!

When running a clean install of Ubuntu I get very odd dots that are rendered all over the screen. They will appear on the edges of things as well as on the desktop in general.  Some will stay where they are and some will move with the window where they appear.  I couldn't find any mention of this kind of graphical error anywhere else.

I have even included a screen shot. For some reason I am able to capture the effect in a screen shot.

I am running:

Newest image of Ubuntu 9.04

AMD 1600+ (1.4ghz)
512 MB Ram
Radeon 9500

---

### Post by Sevets on 2009-05-01
I thought of a few things to add:

I tried using envy to install the flgrx driver but that just makes the login screen get corrupted whenever I try to login; I am not even able to use ctrl-alt-f1 or any other f key for that matter to switch to another console.

I turned the desktop effects to none and also installed fusion-icon and tried using metacity which I believe used to work on an older Ubuntu release (I want to 6 or 7, but it has been a while since I used it).

---

### Post by andrea000 on 2009-05-01
Are you using proprietary drivers?Sounds like a driver issue proprietary drivers may solve this for you.

---

### Post by Sevets on 2009-05-01
I used envyng to install the latest ATI binary driver and it made it unusable pretty much... not sure if there are other drivers or a safer method to install the driver.

---

### Post by andrea000 on 2009-05-01
I only use envyng when all else fails it's good and getting better
try going too  system-> administration-> hardware drivers
and installing from there

---

### Post by andrea000 on 2009-05-01
you may need to restart your pc when your
done.

---

### Post by arashiko28 on 2009-05-01
Yeap, looks like a driver issue, luckly you'll solve it going to system> administration> hardware driver.

Good luck

---

### Post by Sevets on 2009-05-01
When I open hardware driver menu, it shows up empty.

I then went into synaptic and tried to install fglrx from there, nothing showed up in the *hardware menu still, so I logged out the screen went blank then to a scrambled screen with what looked like the initial 'Ubuntu loading screen' like when you first start up.

After a bit the monitor goes into 'sleep' mode.

Upon a restart it does the same thing... I try breaking into console mode with ctrl-alt-f2 but it loads the GUI anyway and then I am unable to get into any other console.

Any other ideas?

*edit

---

### Post by andrea000 on 2009-05-02
go to system-> administration-> software sources 
and check on the ubuntu software tab and see if 
there is a check by the proprietary drivers box
if not put one by it then close when it says 
reload do it.

---

### Post by utnubuuser on 2009-05-02
Hello Sevets
Please post the solution if you find one.  I've got an old-ish laptop that's exhibiting similar behaviour, and the machine is way to old to use any of the proprietary drivers.  Something to do with xorg maybe.
On mine, I've got less than ideal ram (246) and it's a Debian *Lenny* install.


Oh, and apparently there are a couple different versions of the fglrx driver?  A proprietary, binary only version, and the open-source version, -- the binary version is supposedly better, (and available at the ATI site)?

Oh,  and I think you can get at the hardware-driver-control through your rescue/recovery screen with > jockey-gtk

---

