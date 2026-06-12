---
title: "Ubuntu stuck in low resolution mode"
date: 2008-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by argentotenebre on 2008-11-09
Ubuntu stuck in low resolution mode,

I can't find a way to fix it. My screen resolution is stuck at 800 x 600 (ugly) and my screensavers won't work

When I go into System - Preferences - Screen resolution the highest I can get is 800 x 600

It was fine this morning, I installed system updates this morning (47 of them), and it's been like this ever since I rebooted.

I also entered this command into Terminal this morning because I wasn't getting any sound with flash videos (YouTube etc.)
sudo apt-get install libflashsupport

I bought the laptop second hand last week, and everything was perfect apart from no sound in YouTube. So either the command line I typed in to try to fix the sound issue (which worked BTW) was what messed it up or the system updates messed it up.

I tired this code earlier to fix the screen resolution, But it didn't work
sudo dpkg-reconfigure xserver-xorg

So I'm stumped now as to how to get Ubuntu out of low resolution mode, mainly because I want a resolution of 1024, and I miss my screensavers

I am using a Dell Inspiron 9300 Laptop with an Optiquest Q73 Monitor

---

### Post by echovolutionx on 2008-11-09
ok.ill be looking for answer for that...

---

### Post by KyTiX on 2008-11-10
I see that your laptop comes with a Nvidia Go 6800 256MB graphics card. Try this 

sudo apt-get install nvidia-glx

reboot and then your res should be allowed to go higher :)

---

### Post by argentotenebre on 2008-11-10
thanks dude, it worked like a charm

You the man!!!!!!!!!!!!!
You the man!!!!!!!!!!!!!

---

