---
title: "Why is python using 49% of my CPU?"
date: 2009-04-03
forum: General Help
---

### Post by gatorbrit on 2009-04-03
I am running 64 ubuntu 8.10.  With the no programs running (on the desktop) I took this screen cap of conky.  It shows that python is using 49% of my CPU time.  I understand that python is a programming language, but I don't explicitly use it.

When I type "top" it also shows python running 

Any ideas of what is causing this, and what is running?

(I have attached screenshots of conky and also the "top" output)

Thanks

---

### Post by xenophed on 2009-04-03
try to kill python and see what dies in top go k pid -9 
should work does not do it on mine must be something that starts at boot look at time active and it is using all extra resorces

---

### Post by kuja on 2009-04-03
If you have a dual core CPU what it's using is roughly 100% of one core. Python is a programming language and it is also the process name of the python interpreter.

I would assume it's probably caused by bad code. File a bug in whatever you're running with Python. 

And to deal with it in the meantime, there's always "killall python", or if that doesn't work, "killall -9 python"

---

### Post by gatorbrit on 2009-04-03
> **kuja said:**
> If you have a dual core CPU what it's using is roughly 100% of one core. Python is a programming language and it is also the process name of the python interpreter.

I would assume it's probably caused by bad code. File a bug in whatever you're running with Python. 

As far as I know I am not running anything in python - but I'll try the suggestion below:

> 
And to deal with it in the meantime, there's always "killall python", or if that doesn't work, "killall -9 python"


Thanks

---

### Post by gatorbrit on 2009-04-03
killall python took care of it.  I have no idea what was running - very puzzling.

---

### Post by BryanFRitt on 2009-04-03
I have the same problem with **python** taking up I think it was 70% CPU (but I not sure the exact amount) I can *kill* **python** using KDE System Guard (**ksysguard**) and the total CPU usage goes down tremendously.  I haven't noticed any bad side effect on *kill*ing the **python** process.  Any ideas on how to fix it so I won't have to kill the process again?  I don't know what is launching python.  

I used to notice something similar with *kdesu*, don't know what's changed, but I haven't seen that problem as much lately.

Any help with the **python** CPU problem would be appreciated.

Thanks,

BryanFRitt

p.s.
I have 
Dell Latitude D830 Notebook
Intel Dual Core 2 2.2GHz
KUbuntu 8.04.2_x86-64
256MB Nvidia NVS 140 Card
4 GiB Ram
WUXGA (1920x1200) monitor
abgn wireless, gigabit ethernet card
...

---

### Post by The Cog on 2009-04-03
Run top and then hit the C key. This turns on the display of the command line arguments so you can see which program python is running.

---

### Post by mlissner on 2009-04-16
Huh. For me it was a script running in Amarok - the googlyric.py script. That's a good tip about pressing c in top. Worked like a charm.

---

### Post by BryanFRitt on 2009-04-26
Thanks for the top command then c idea! It really helped!

-

I just figured out that this happens every time when I log out and restart-X. (only one might be necessary, but I didn't test.)

For me, it said:
*python /usr/bin/hp-systray*

Now on to figure out how to get "*python /usr/bin/hp-systray*" to stop running on re logging in , etc...

[https://answers.launchpad.net/hplip/+question/42327](https://answers.launchpad.net/hplip/+question/42327)
"
Try removing the file from the /etc/xdg/autostart directory (its named
hplip-systray.desktop).
"

It didn't work after a simple log out, but after a restart, (and log out and restart-X to test) CPU usage is back to normal, no python taking up way too much CPU.

Thanks "The Cog" and "dwelch91"!

note: That's for my printer, but I haven't tested printing after this fix, as of typing this.

---

### Post by ruipedroca on 2009-05-03
> **BryanFRitt said:**
> 

[https://answers.launchpad.net/hplip/+question/42327](https://answers.launchpad.net/hplip/+question/42327)

"Try removing the file from the /etc/xdg/autostart directory (its named
hplip-systray.desktop)" 

Thanks!
Removing "/etc/xdg/autostart/hplip-systray.desktop" solved my problem also (after that i didn't try to log out and then in again, but did a restart).
And i still can print like before. :)

I'm running Debian Lenny 5.0 and Python was making my dual core 2 working at 100%, thus making my system very slow.
This was caused by "python" due to the process /usr/bin/hp-systray", as i could see in the menu "Applications/System Tools/System Monitor".
I've installed HP-Lip not using the repositories, but downloaded the more recent version from it's site. I've also made some experiments to make my scanner work with Xsane, so i guess it can all be related.

All's well that ends well :guitar:

---

### Post by AlmaTlust on 2009-10-20
mmh - i had the same problem with hp-systray (and it won't show its systemtray-icon), but I have the same problem with update-notifier and elisa, both of wich use python. So to me, it more looks like a python problem, maybe some missing libraries?
Other python-using programs seem to run fine.

---

