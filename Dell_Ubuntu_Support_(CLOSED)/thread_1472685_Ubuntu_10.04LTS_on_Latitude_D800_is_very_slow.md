---
title: "Ubuntu 10.04LTS on Latitude D800 is very slow"
date: 2010-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ysap on 2010-05-04
Hello,

I have a Latitude D800 that I am trying to revive by installing Ubuntu. I have the installation CD from the Ubunto download page (10.04 LTS Lucid Lynx). Using it, I performed a fresh installation. Once booting in the system, I have everything seems to be running (including the WiFi support).

The (big) problem is that the system is very slow in terms of responsiveness. So, first thing, I installed the recommended nVidia drivers (v173) using the Hardware Drivers applet.

Now it became even worse. You can literally see how the menus and windows are being drawn on the screen. It takes it 1-2 seconds to update a small pop-up.

I really don't know if I am doing something wrong here, but this laptop was running WinXP pretty well for a couple of years, so I don't see why there should be a problem with Ubuntu. It could be a problem with some other part of the system (other than the display drivers, that is), but I have no clue what to start looking for.

Ubuntu 10.04 LTS
Gnome 2.30.0
1024MB RAM
GeForce FX Go5200 32(?)MB @ 1920x1200
TOSHIBA 40GB PATA HDD (System Test reports 35MB/sec cached)

Any help here will be appreciated.

Thanks.

---

### Post by tgalati4 on 2010-05-04
Could be indexing going on.  Install htop and watch it for a while:

sudo apt-get install htop
htop

---

### Post by ysap on 2010-05-04
> **tgalati4 said:**
> Could be indexing going on.  Install htop and watch it for a while:

sudo apt-get install htop
htop

Thanks. What is htop?

EDIT: OK, I see that htop is some kind of a process viewer, right?
I tried running the System Monitor applet. What I see  is ~100% CPU usage and ~40% mem usage. Looking at the processes, I have just the Monitor process with ~35% CPU and all other processes sleeping. Were are the other 65%???

---

### Post by my_linux on 2010-05-04
See the following at the known issues link below:

A memory leak in the X server's handling of 3D rendering will cause systems that use the default compiz window manager to become sluggish over time. This bug is being actively investigated and a resolution is expected for the final release of Ubuntu 10.04 LTS. (565981)*

[http://www.ubuntu.com/getubuntu/releasenotes/1004overview#Known%20issues](http://www.ubuntu.com/getubuntu/releasenotes/1004overview#Known%20issues)

* Check if Compiz / effects is disabled by simply going to System > Preferences > Appearance and setting Visual Effects to none.

What happens if you run at a lower resolution? GeForce FX Go5200 32(?)MB @ 1920x1200 seems like you may be connected to an external monitor; run only on built in display?

---

### Post by ysap on 2010-05-04
> **my_linux said:**
> See the following at the known issues link below:

A memory leak in the X server's handling of 3D rendering will cause systems that use the default compiz window manager to become sluggish over time. This bug is being actively investigated and a resolution is expected for the final release of Ubuntu 10.04 LTS. (565981)*

[http://www.ubuntu.com/getubuntu/releasenotes/1004overview#Known%20issues]("http://www.ubuntu.com/getubuntu/releasenotes/1004overview#Known%20issues")

* Check if Compiz / effects is disabled by simply going to System > Preferences > Appearance and setting Visual Effects to none.

What happens if you run at a lower resolution? GeForce FX Go5200 32(?)MB @ 1920x1200 seems like you may be connected to an external monitor; run only on built in display?

So, in the meantime, I found out (via Wikipedia, duh) that Compiz is just one option for a  windows manager, and that the low resource option is actually Metacity. I found a post with the command to switch between the WM's: Alt+F2 and 'metacity --replace'. This immediately improved the situation. The screen update is much faster now, but still, slower than what I got used to under WinXP.

I doubt that that it was that mem leak responsible for the slowness, because it happend immediately after installing the nVidia drivers. Now, I need to find out how to change the WM to Metacity permanently, as the Compiz is loaded by default at restart. Any suggestions here?

Anyway, I believe I am running the 10.04 LTS release. This is what the system info reports. However, the image was downloaded about a week ago, which is prior to the official release, if I understand correctly. How can I make sure I have the absolute latest release?

Now, a few problems still apply; maybe one of you experienced users can help me here: First, as I mentioned above, the System Monitor applet shows 100% CPU utilization in the resources tab, but only 1 process - the monitor itself - consumes some CPU, and it is 35%. How can I know where are the missing 65%?

Second, even with Metacity, the performance are mediocre relative to WinXP. There must be a reason for that, as my GPU is the widely-spread Go5200. I am running on the laptop's LCD. This is its native resolution (WUXGA). It can't be that I am the only one with this kind of problem, so there must be a way to get to the roots of this situation. Unfortunately, I am not familiar with the system maintenance and monitoring tools available to Linux operators.

Thanks.

---

### Post by my_linux on 2010-05-05
As previous: Check if Compiz / effects is disabled by simply going to System > Preferences > Appearance and setting Visual Effects to none.

Instead of GNOME consider using XFCE or LXDE also you'll need to confirm the Nvidia drivers are being used by looking at the Log File Viewer. Did you reboot after installing the Nvidia driver?

Using the update manager should get you up to date assuming you are using the RC version. Alternatively you can downlod the full release by going to releases.ubuntu.com and do a clean install.

---

### Post by ysap on 2010-05-05
> **my_linux said:**
> As previous: Check if Compiz / effects is disabled by simply going to System > Preferences > Appearance and setting Visual Effects to none.

Instead of GNOME consider using XFCE or LXDE also you'll need to confirm the Nvidia drivers are being used by looking at the Log File Viewer. Did you reboot after installing the Nvidia driver?

Using the update manager should get you up to date assuming you are using the RC version. Alternatively you can downlod the full release by going to releases.ubuntu.com and do a clean install.

Thanks, my_linux. It appears that the Compiz is loaded with Normal effects settings by default. Once I reduced it to None, it now behaves similar to Metacity. Still not great, but at least you can work with. I just wonder - are any Go5200 users able to get the nicy effects on their desktop?

Now I seem to have a new problem - my wireless connection is disabled and I can't make it to work. I guess I will start a new thread for that. I need it to update the system, so until this is solved, I can't go further with your recommendations.

Thanks.

---

### Post by ysap on 2010-05-06
> **my_linux said:**
> As previous: Check if Compiz / effects is disabled by simply going to System > Preferences > Appearance and setting Visual Effects to none.

Instead of GNOME consider using XFCE or LXDE also you'll need to confirm the Nvidia drivers are being used by looking at the Log File Viewer. Did you reboot after installing the Nvidia driver?

Using the update manager should get you up to date assuming you are using the RC version. Alternatively you can downlod the full release by going to releases.ubuntu.com and do a clean install.

After some playing around, and updating all modules recommended by Synaptic, I now have a somewhat workable system. I am currently using Metacity instead of Compiz as it tends to be a little more responsive.

I also found out that a 'backend' process from checkbox was loading my CPU to 100% and killing it make it a little better yet.

I would like to try a lighter WM, like the XFCE. How do I install and run this? Synaptic shows dozens of related files, so I am not sure what to install.

Thanks.

---

### Post by my_linux on 2010-05-06
See 

[https://help.ubuntu.com/10.04/index.html](https://help.ubuntu.com/10.04/index.html)

[https://help.ubuntu.com/10.04/config-desktop/C/other-desktops.html#other-desktop-xfce](https://help.ubuntu.com/10.04/config-desktop/C/other-desktops.html#other-desktop-xfce)

---

### Post by neilmaclennan on 2012-02-23
One of the major problems that I see (from my experience with Windows more than Linux) is that yo are using an ancient HDD, which is probably on l=its last legs but that may not be the end of it. I am no expert. But HDD's are the first to show signs of wear and tear resulting in slugishness, the next is the MOBO, and then on down for performance degredation due to failing hardware. When it;s the cpu it's all or nothing most of the time, same with the RAM. If you are proficient enough try to create your own OS using SUSE, I tried and am far from building anything that I have the foggiest clue of what I've built. lol Failing that run Puppy linux or similar tiny linux OS, if running these doesn't have an impact on performance then start swapping out hardware for replacements one at a time, and replacing the previous part, to narrow down the hardware fault. If you are lucky enough to be able to have access to them. Make friends with a local kijiji or usedx.com where x is the city you live in. Good luck and please let me know if I am way off base with my suggestions and or if you have any further additions that I too an learn from.

---

### Post by BBQdave on 2012-02-23
> **ysap said:**
> How can I make sure I have the absolute latest release?

Running update manager (which should run automatically), will have your system up to date.

I suggest **Debian 6** (Squeeze).  I did run Ubuntu 10.4LTS, but found Debian 6 (what Ubuntu 10.4 is based on) to be more responsive and stable.

I am running Debian 6 on a Dell Inspiron 1100 (with Celeron 2.0 GHz and 1 gig of ram).  Debian 6 will be supported for a good while yet (a good fit for my almost decade old hardware).

Plus **Debian 6** features **Gnome 2  :D**

Though as noted in previous posts, you could have hardware failure occurring.  :-(

---

