---
title: "X Server refuses to start - Fatal server error: Caught Signal 11 Server aborting"
date: 2007-05-23
forum: Desktop Environments
---

### Post by russelljsmith on 2007-05-23
Hi,

I built a new system at the weekend, installed Ubuntu and was up and running in an hour or so, nice.

However, I needed to switch screen resolution up from 1024x768 to 1440x900 and also wanted to get my graphics card running at it's best (I've heard Beryl may be worth a look once I've got this working).

I downloaded the Nvidia restricted driver from the ubuntu repository but was a bit confused by all the options in the xorg.conf configuration utility, so I had a look on the web and downloaded the drivers directly from Nvidia (a newer build) and installed these and tried them out, then used Nvidias app to set my screen resolution, this all worked fine, I even had desktop effects working.

Later I had the computer off and when I restarted X Server chucked an error on startup with the message:
[INDENT][FONT="Courier New"]Fatal server error: Caught signal 11. Server aborting[/FONT][/INDENT]

So far I've tried:
[LIST]
[*]Restoring xorg.conf to a backup I made when I first began installing new drivers
[*]Changing "nvidia" in xorg.conf to "nv"
[*]Renaming "xorg.conf" entirely so it isn't found (I read somewhere this will cause X Server to use default settings)
[/LIST]

To date, no joy getting X Server running, any ideas much appreciated?

Also, what is the best and most reliable way to setup xorg.conf to get the best out of my graphics card and system?

---

### Post by russelljsmith on 2007-05-23
PS. More info:

My system is running Ubuntu x64 on an Asus motherboard with an AMD X2 processor and integrated GeForce 6150 graphics system. Please let me know if I can supply any more info.

---

### Post by russelljsmith on 2007-05-24
Update:

I tried running X Server reconfigure again last night to get a working xorg.conf file, but nothing I tried worked, I'm still getting the red white and blue screen of death when I try to start GDM.

I looked again at the error log and there is nothing I could interpret easily, X Server appears to start all modules okay, this is then followed by several lines of backtrace, then the fatal error.

I'm still foxed by this one, any help much appreciated, I'm considering re-installing Ubuntu from scratch but that feels like a windows style solution to a problem! Also, I can't be sure I wouldn't end up here again.

Thanks / Russell

---

### Post by matty_b_1000 on 2008-01-07
Having the same problem here with an ATI card. Also, this just happened out of the blue, have had it working (with dual screens) for months now. Just turned my PC on one day and WHAM. Blank screen, startx produces exacly the same output you just described, /etc/init.d/kdm start says that KDM is still running, and won't let me stop it.

---

### Post by djgenesis on 2008-01-18
any news on this issue? I am having the same problem...

---

