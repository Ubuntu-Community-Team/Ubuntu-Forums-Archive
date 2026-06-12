---
title: "No display when hot docking or undocking Latitude E6510 with 10.04 64 bit Ubuntu"
date: 2010-09-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by joculi on 2010-09-08
I have a Dell Latitude E6510 with Ubuntu 10.04 64 bit installed.  I have the 512MB NVIDIA NVS 3100M video card and have installed the proprietary nvidia driver.  I also have an "E/Port simple port replicator" docking station.  I have an external monitor, keyboard and mouse attached to the docking station.  When the laptop is in the dock, the lid is closed.

When I try to undock the laptop while it is running, I find I have no display when I open the laptop lid.  Similarly, if I have been working undocked, close the lid and dock it, I get no display on my external monitor.  I expect that after docking or undocking the system will recognize which monitor to use and switch to it automatically.  I had become accustomed to that working on my prior OS (XP).

Anyone know how to get this to work correctly?  Thanks in advance.

---

### Post by joculi on 2010-09-10
Anyone aware of *any *version of Ubuntu where this might work?  I see lots of posts where people complain about it, but no solutions.  I used to have a Lenovo laptop with Ubuntu 8 and a docking station, but I don't recall whether it had this problem or not.  I don't think I tended to try to hot dock back then.  

I'm getting ready to abandon Ubuntu 10.04 due to this problem.  I'm downloading fedora now to see if the problem exists there.  Pondering reverting to Ubuntu 8 as well.  But form what I see in other posts, the problem has existed in Ubuntu for a long time.  Not sure version 8 will solve it.

---

### Post by joculi on 2010-09-10
This blog posting suggests there is a way to write a script to switch between available monitors:  [http://cpbotha.net/2007/04/10/a-critical-look-at-ubuntu-feisty-beta-on-an-hp-nc8430-laptop/](http://cpbotha.net/2007/04/10/a-critical-look-at-ubuntu-feisty-beta-on-an-hp-nc8430-laptop/)
but the link to the actual script is broken.  Anyone know how to write such a script?  Binding a script to a hotkey would be an acceptable solution.

---

### Post by joculi on 2010-09-12
Fedora 13 64 bit has the same problem.  No luck there.

---

### Post by Denis on 2010-09-15
It appears that I have the exact same problem. 

My Dell Latitude E6510 had a default 64bit Ubuntu 10.04 install. When I just had the laptop it seemed to switch fine between the dock with monitor and the laptop screen. But now I can't get the laptop screen to work properly in Ubuntu. When the Dell is disconnected from the dock the laptop screen remains black.

Changing settings in the System>Monitors menu doesn't seem to help. The two monitors are recognized as separate screens, but they can't easily be switched on or off. 

I haven't tried installing any proprietary drivers. Considering your case, that may not solve the problem for me either. My hope is it gets fixed in Ubuntu 10.10. 

If anyone has a suggestion, I'll be glad to hear it.

---

### Post by A4orce84 on 2010-10-13
Unfortunately, the problem still exists in 10.10 with my Dell. =(

---

### Post by Denis on 2010-10-14
Updating to 10.10 didn't help here either.

---

### Post by joshr799 on 2010-10-24
Not for nothing but I have the same issue with Windows 7 Ultimate 64bit.  Came across this during a google search.

Josh

---

### Post by dontupanic on 2011-09-03
I am also running a Latatude e6510 with Ubuntu 10.10 When the system is in the doc it works fine. when I take it out and boot it I get dropped to a command line. When I go to system > monitors it only shows the external display. The following is part of /var/log/messages If anyone on the board can help me interpret it I would appreciate your help

Sep  3 20:23:36 ltop kernel: [    7.487023] acpi device:02: registered as cooling_device4
Sep  3 20:23:36 ltop kernel: [    7.488311] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input5
Sep  3 20:23:36 ltop kernel: [    7.488368] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)

---

### Post by tom.tom_j on 2011-09-07
Hi All,

        Try Installing or Upgrading to Ubuntu 11.04.All the External Monitor bugs have been fixed in it......):P


Regards

---

