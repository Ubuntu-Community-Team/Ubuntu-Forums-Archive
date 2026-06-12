---
title: "gnone-cups-icon process ALWAYS &gt; 75% CPU"
date: 2006-06-02
forum: Desktop Environments
---

### Post by flub on 2006-06-02
After installing the Dapper I've noticed (via system monitor) that gnome-cups-icon is taking over 80% of the CPU time.

How do I reduce the CPU load caused by gnome-cups-icon (without stopping it)?

Thanks in advance

---

### Post by flub on 2006-06-02
Some more info.

If I kill the process my system returns to normal, and this did not happen in Breezy.

Anyone else getting this?

---

### Post by FuturePast on 2006-06-02
I can confirm this, but I can't help.
I've been running Dapper for 1 month+ and today is the first time I've seen this.

Cheers

---

### Post by wrtrdood on 2006-06-02
I confirm -- on three separate systems.  Only in my case it consumes all available CPU.  I always start the monitors for CPU and Network and have watch each system's processor get pegged.  I've seen this problem happen before and then it seemed to be resolved.  I just updated all my machines (x86, AMD, Crusoe) and every one exhibits this symptom under Gnome.  I think it's been there a while but didn't give it much thought as I usually run E17.

I've also tried killing the process which usually drops the CPU use to less than 10% but the process will be restarted eventually and it's not long before the CPU is being hammered again.  Oddly enough, on one box I've not even set up any gnome printing so I don't think it's related to that.

This bug has already been reported (#45421):
[https://launchpad.net/distros/ubuntu/+source/gnome-cups-manager/+bug/45421]("https://launchpad.net/distros/ubuntu/+source/gnome-cups-manager/+bug/45421")

---

### Post by flub on 2006-06-02
Thanks for confirming, much appreciated.

---

### Post by precinto on 2006-06-04
I confirm this too. Same thing happens on my Acer laptop since upgrade.
Don't know how to solve it, though. I'm not using any printers either.

---

### Post by celem on 2006-06-04
I don't see it on my machine. Gnome-cups is sleeping, even after I print a page - I assume because it was too fast for me.

---

### Post by Irony on 2006-06-14
This just happened to me today, gnome cups icon uses 100% cpu but if I stop it, it stops the problem.

The only thing different from yesterday is that a laptop has been removed from the network, however this is usually off anyway. Also doing sudo ifdown eth0 doesn't stop the problem - I'll see if the problem goes away when the laptop is returned.

---

### Post by GadgetsGuy on 2006-06-14
this may help you if you are using the 686 kernel

[http://ubuntuforums.org/showthread.php?t=196430](http://ubuntuforums.org/showthread.php?t=196430)

now I just need to figure out how to edit the damn file .... LOL!

---

### Post by Irony on 2006-06-15
Now the laptop is connected (but not on) this seems to have sorted itself out - perhaps it was just a coincidence or maybe something to do with samba.

---

### Post by adam.skinner on 2006-06-25
I can confirm this behaviour as well.

---

### Post by el davo on 2006-06-26
I had the same problem, but enabling "Detect LAN printers" has the CPU use back to normal for me.

System/Administration/Printers
Global Settings/Detect LAN printers <- check this

or

gedit /etc/cups/cups.d/browse.conf
Browsing On

---

### Post by Yleeyas on 2006-07-09
Hi folks,

I had this problem (100% useage) occur for the first time today AFTER a bunch of cups related updates :confused: 

I managed to kill the process (gnome-cups-icon) and got my cpu back .

Is there any further info on the problem? 

Yleeyas

---

### Post by unnes on 2006-07-10
Ditto on this problem... Synaptic just updated several CUPS-related  files, and all of a sudden gnome-cups-icon started hogging 100% CPU. Killing it released my CPU.

---

### Post by epanepucci on 2006-07-10
hi,

this gnome-cups-icon also slurps parts of my CPU on a system with:
   dapper 6.. with  all current updates on a dell insp.6000.

I was wondering if there is a way to configure this applet to only show certain printers and here is why: 

my network has approximately 200 printers and this applet is dutyfully showing me that a printer on  the other side of the river is printing something, on a building I don't even know where it is...

Right now I am just renaming the applet so it doesn't get started at all.

Spare knowledge very welcome!

Cheers,
   Zac

---

### Post by uglysmurf on 2006-07-11
Just another confirmation of this behavior...I have no printers connected to this box or on my network at all.

---

### Post by Topper_H on 2006-07-30
I confirm this issue on Dapper LTS, Athlon 3800 X2. Gnome-cups-icon eats 100% of one out of 2 CPU cores.
The CPU temperature climbs so high it could damage the hardware if you stay away from your running computer for long !

---

### Post by chadk on 2006-08-04
ditto on the problem.  setting detect network printers doesn't do anything for me, killing the process does.

---

