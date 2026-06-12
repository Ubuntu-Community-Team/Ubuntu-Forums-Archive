---
title: "Ubuntu 7.10 running incredibly slowly"
date: 2008-01-27
forum: Desktop Environments
---

### Post by Reconcilliation on 2008-01-27
My Specs:
Ubuntu 7.10
--Kernel Linux 2.6.22-14-generic
--Gnome 2.20.1

AMD Athlon XP 2000+
1.2GB RAM [I'm assuming it's two 512 sticks, and one 256 stick.]
Nvidia GeForce 6800 [Yes, the restricted driver is installed.]

Problems:
-CPU usage constantly at 20% or more. It almost never goes below this.
-Hangups every couple seconds.
-Java programs lag and hangup a great deal
-Moving the mouse increases processor usage from 20% to 50% for minutes after startup.
-Sound is automatically muted on startup, and requires a power off/on cycle to turn it on again.
-Firefox randomly breaks, saying something about a configuration file. Rebooting fixes the problem.

My System Monitor tells me that Firefox, Java, and Gnome-System-Monitor are using up the most CPU-time. The CPU history shows large spikes going from ~20% to 80%-100% CPU usage every couple seconds.

My solution:
-I've downloaded 7.10 and burned it onto a live CD. I am going to try a fresh install.
-Dual boot Windows and Ubuntu, with Windows on the 100GB HDD, and Ubuntu on the 40GB HDD.
-Ask Ubuntu forums for help.

Edit:
I Downloaded Envy [[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)] and let it install the necessary files. After reboot the computer seemed to run slightly faster. The CPU now idles at ~15%.
However, it still hangs up every couple seconds, especially when loading script-heavy webpages or flash movies. [Like gametrailers or youtube.] I still think a full-reinstall is going to be necessary. As right now, the computer is running more slowly than when Windows XP was installed.

---

### Post by jpeddicord on 2008-01-27
> **Reconcilliation said:**
> However, it still hangs up every couple seconds, especially when loading script-heavy webpages or flash movies. [Like gametrailers or youtube.] I still think a full-reinstall is going to be necessary. As right now, the computer is running more slowly than when Windows XP was installed.
Firefox is... not the greatest at handling complex web pages. Firefox 3.0 is a lot better at it, so this might not be just your problem. What extensions do you have installed? I find Tab Mix Plus is a CPU eater when loading pages.

Java can use a lot of resources as well; do you know what Java applications you have installed?

---

### Post by Reconcilliation on 2008-01-27
I don't have any firefox extensions installed, save a theme, and adblock. I'll try installing Firefox 3, though. 
Edit: I suppose Flash counts as an extension, too.

As for Java, the only program I've been running is Megamek; a computerized version of Battletech. It's not a very [**graphics-intensive**](http://img175.imageshack.us/img175/2005/potm01oq8.jpg) [imageshack.us] java program. But it's enough to drop this computer to its knees.

---

