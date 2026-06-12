---
title: "D630 machine won't power off"
date: 2012-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sbrbot on 2012-05-06
Few days ago I installed a brand new Ubuntu 12.04 on my Dell Latitude D630 machine. Everything seems to work fine but problem is with shutdown/poweroff. My machine won't power off correctly. After starting shutdown procedure Ubuntu shuts down, OS turns off, but machine won't completely power off! Screen is black but green power led is still on and ventilator works (probably like CPU, MEM and HDD) in background! How to solve this issue?

---

### Post by vistilarsen on 2012-06-28
Bog!
Just like you I have a Dell which won't power off.
Its my first spell with Ubuntu and have the lovely 12.04 version.
Dell Vostro 1500 Laptop. Everything shuts down properly but the machine doesn't power off in the end.
Have tried to edit the GRUB to reboot=bios and reboot=acpi, but without luck.
Everything else about the shutdown is fine, just not the power off bit.
Looking forward to some ideas!

---

### Post by Cookie11 on 2012-06-28
Just a hunch, but what you describe is the difference between halt and poweroff. Try a command line poweroff, or try playing around with some flags (there is one in /etc/), man halt also describes some switches...

---

### Post by vistilarsen on 2012-06-30
It worked thanx! sudo poweroff -p worked and ensured that the poweroff occurred. From the --help I can see that -p is intended to interpret a halt as a time to poweroff. But how do I ensure this happens without the need to open the terminal each time?
Also this doesn't solve reboot, as it also halts on reboot and doesn't complete the reboot?

---

### Post by vistilarsen on 2012-07-15
Just saw an answer on this thread: [http://ubuntuforums.org/showthread.php?p=10489760#post10489760](http://ubuntuforums.org/showthread.php?p=10489760#post10489760)
The issue could pertain to a specific driver being faulty and in that particular thread it was the wireless driver. But trying the same commands didn't work in my case as I didn't have the same driver. How to know what is the name of my specific Wireless driver in this Ubuntu install?

---

### Post by BlackJack on 2012-07-16
This may not help,  but since your issue has the same symptoms as what I had experienced, I figured it couldn't hurt, and might help, to go ahead and post this here as well as in my thread. 



I had disabled Bluetooth in the system BIOS, but there was still a Bluetooth Manager loading when GNOME started. I removed the Bluetooth Manager from the Startup Applications and have not experienced this issue since. Of course, this is just since yesterday so I will need to watch it to make sure that this was the problem,  but so far it is looking good.

I am guessing that the Bluetooth Manager might have been hanging up while waiting for Bluetooth to shutdown. Of course, this would never happen since Bluetooth was disabled at the BIOS level. The one thing that has me still wondering is that the issue was intermittent and didn't happen every time. As I said though, it is looking good so far.

---

### Post by sbrbot on 2012-09-19
Sorry, false alarm! My system still does not power off correctly. Sometimes it does, but after several minutes of work not any more.

---

### Post by bayouoldguy on 2012-09-19
> **sbrbot said:**
> Today, after last system update, my machine again goes off correctly. I don't know what was the problem, and what solved it but now it's like on 11.10. Power off works.

sbrbot; glad you solved your problem. You need to post this thread as "solved", may alert & help others......"G":p

---

### Post by eombah on 2012-09-21
if you have nvidia, this may be your problem: [https://bugs.launchpad.net/bugs/987933](https://bugs.launchpad.net/bugs/987933)

---

### Post by sbrbot on 2012-09-24
> **bayouoldguy said:**
> sbrbot; glad you solved your problem. You need to post this thread as "solved", may alert & help others......"G":pSorry, firstly I thought it was solved but now I see that I have the same problem again.

---

### Post by sbrbot on 2012-09-24
> **eombah said:**
> if you have nvidia, this may be your problem: [https://bugs.launchpad.net/bugs/987933](https://bugs.launchpad.net/bugs/987933)
Hi,
I do have nVidia graphics card and use nVidia's driver v. 295.40. I tried the solution recommended in that post but without success! We'll see what future brings...

---

