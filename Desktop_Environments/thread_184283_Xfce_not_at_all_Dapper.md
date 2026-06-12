---
title: "Xfce not at all Dapper"
date: 2006-05-29
forum: Desktop Environments
---

### Post by ahaslam on 2006-05-29
Hi, I've recently upgraded from Breezy to Dapper via the on-line update.
Out of curiosity I installed 'kubuntu-desktop' to try out KDE without a seperate install. This worked well, so I thought I'd give Xfce a try. I had to uninstall the 'ubuntu-desktop' (a shame, I prefered it over kde).

Once installed, I was very suprised. I'd heard that it was a lightweight and quick desktop. ***It certainly is lightweight, but it's very, very slow!***

See these screenshots of the System Monitor:
[ATTACH]10242[/ATTACH][ATTACH]10243[/ATTACH][ATTACH]10244[/ATTACH]

Both KDE & GNOME used about 4% CPU, not 25%! 
This has a HUGE IMPACT on the usabillity of my system. Everything is jerky and takes time to load. It's much slower than KDE with transparrent everything, shadows and every other option switched on!

Is this normal, or is something wrong?

Any comments are welcome.

Thanks,
Tony.

---

### Post by doobit on 2006-05-29
You must be doing something wrong. Xfce is not using 25% of your system resources. 
Run top in a terminal and see what's eating you.
Xorg with Xfce on my computer is using about 1.7% of cpu and 3.1% of RAM.

---

### Post by ahaslam on 2006-05-29
[QUOTE=doobit]You must be doing something wrong. Xfce is not using 25% of your system resources. 
Run top in a terminal and see what's eating you.
Xorg with Xfce on my computer is using about 1.7% of cpu and 3.1% of RAM.[/QUOTE]

It apears that It's X.org that's eating resources, see here:
[ATTACH]10248[/ATTACH]

It's fine with KDE, as it was with GNOME. I don't get what's happening:confused: 

Please help.

---

### Post by douga on 2006-05-29
I hate to barge in just to say "it works for me", but it does.

How far along are you with your updates? I got an xorg server update just yesterday (or was it today?), and firefox running, my system is using between 3 and 5% cpu.

For me, the VIRT column in top is about 42k -- doesn't even approach a meg.

For the record: how much memory do you have? It appears to be around 400M?

---

### Post by ahaslam on 2006-05-29
I've found & solved the problem.

For transparrent windows in KDE, I added the following to my xorg.conf:

Section "Extensions"
        Option          "Composite" "Enable"
EndSection

Removing this brought my CPU usage down to 6% and the system was much smoother.

Thanks for the guidance,
Tony

---

### Post by ahaslam on 2006-05-30
You proberly noticed from the screenshots that I had slight transparencies & shadows enabled. Once I changed my xorg.conf as above, these went.

When going through the settings menu trying to find how I enabled them, the system crashed. Once rebooted I could not bring up the main menu, either from the panel or by right clicking the desktop. I reverted my xorg and the visual effects came back, but still no menu. 

I have completly removed & re-installed 'xubuntu-desktop' and the problem still exists. All that I am able to do is customise the lower pannel & reboot (pressing the power buton brings up the 'log out' screen).

Any ideas?

Cheers, 
Tony.

---

