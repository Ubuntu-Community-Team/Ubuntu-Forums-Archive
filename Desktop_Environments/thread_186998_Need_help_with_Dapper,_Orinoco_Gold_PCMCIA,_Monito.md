---
title: "Need help with: Dapper, Orinoco Gold PCMCIA, Monitor Mode"
date: 2006-06-02
forum: Desktop Environments
---

### Post by icedcapp on 2006-06-02
First off I know it's likely this topic has been covered before but I have not found it so please don't flame me.  If you know where I can find the answer please just post me a link or tell me how.

I have the new i386 Dapper release dual booted on my laptop.  I'm using a Orinoco GOLD PCMCIA card which works fine for wireless connectivity fresh out of the box as it were.  However I cannot seem to get it to go into moniter mode.  I am trying to do this by going to a shell and typing, ipwconfig eth2 mode monitor.  It tells me it fails and cannot do this.  I know this card works in monitor mode as I can run an Auditor live cd and run all my utilities just fine.

I've read conflicting information about what firmware I should have on my card, special drivers for my card in linux and I was hoping someone here could just help clarify what needs to be done.  Thank you in advance for any assistance.

---

### Post by insyzygy on 2006-06-26
Hey.

You may have already founded an answer to this or given up but I might be able to help. 

I recently struggled trying to get a laptop with an orinoco card into monitor mode. There seems to be lots of old(not working with current kernel) and inconsistent information and it took me quite a while to find a solution that worked. Also although I have an orinoco chipset its not exactly the same card as you (its a mini pci card) so its possible this solution won't work as well for you. 

It turns out that the orinoco drivers included in dapper support monitor mode hower they have been compiled with this option turned off. You have to recompile them with it on. This is actually not too bad. First make sure you have (using apt-get or synaptic) the most recent kernel headers for whatever kernel you are using. 

Next download the driver source from sourceforge
[https://sourceforge.net/project/showfiles.php?group_id=44338]("https://sourceforge.net/project/showfiles.php?group_id=44338")

Extract it to a directory somewhere. Open the file orinoco.c
Find the line
[LEFT]**static int force_monitor; /* = 0 */**[/LEFT]
and change it to read
[LEFT]**static int force_monitor = 1;**[/LEFT]
Now in that directory type 
[LEFT]**make**[/LEFT]
You may have to edit the makefile to point to your headers but probably it will just compile. It should produce a bunch of *.ko files.  Assuming it compiled without errors lets continue.
Now lets find what drivers are currently loaded.  Type
[LEFT]**lsmod | grep orinoco  **[/LEFT]
This should tell what modules are associated with the card.
You should get some stuff with names like orinoco, orinoco*, etc as well as pcmcia. (I get pcmcia orinoco, orinoco_cs, hermes)
All the listed modules (except pcmcia which we won't touch) should have a corresponding newly compiled .ko file (there will be more of these than just the ones you are using).
Now we replace the old modules with the new ones. The wireless modules that your computer is currently using are located in the directory [LEFT]**/lib/modules/<kernel version>/kernel/drivers/net/wireless/**.[/LEFT] 
[LEFT]cd to that directory. [/LEFT]

Here there are also a bunch of .ko files. First you should back these up as this might not work and we will be overwriting your current drivers.
Make a directory say ~/backup and then cp *.ko  ~/backup.
Now copy your new .ko files (the ones in the directory where you ran make) to this directory. You can copy them all or just the ones that are being loaded (the ones listed by lsmod|grep orinoco). You will have to sudo or be root to do this.

Now cross your fingers and reboot. If this works your wireless will still work and you will also be able to go into monitor mode with iwconfig.  Strangely monitor mode will not show up still under iwpriv. 

Some observations. Even though this works, monitor mode seems to be somewhat finicky.
In particular in order to get Kismet to work I have to bring the interface down
[LEFT]Ifconfig eth* down, ifdown eth*.[/LEFT]  (where eth* is whatever your wifi is wlan0 or eth1 probably)
Then reset the card with
[LEFT]iwpriv eth*  force_reset.[/LEFT] After this, Kismet starts up. However it wasn't working  well until I edited kismet.conf and set it to look on a fixed channel. Then it worked great. I think with these drivers switching channels may not work so well in monitor mode. But on a fixed channel its fine. This may or may not be true for your card as it depends on the firmware version I think (mine is 8.10). Of course the reason that the these drivers have monitor mode turned off by default is that it is buggy with many firmwares so experiment.

If this doesn't work (happened to me compiling earlier drivers as suggested on some forums) then you will probably have to boot in recovery mode as it will hang during boot (just ctrl c past it) and change back to the original .ko files which you backed up.

One final comment. During the course of messing around with this I blacklisted my hostap module as it is rumored to conflict with the orinoco driver. I don't know if this actually is relevant or true since I didn't systematically experiment (and since I'm in the middle of typing I don't feel like restarting without it to see.). If weird things are happening you might try
putting 
blacklist hostap
blacklist hostap_cs in 
/etc/modprobe.d/blacklist
The hostap lets your wifi card act as an access point supposedly, I didn't really care about that so I blacklisted it to be safe.

Finally after doing anything in monitor mode do a 
iwpriv eth* force_reset 
to get back to normal.

I can be more explicit on any steps if you need.

---

### Post by mossholderm on 2006-08-12
Couple of things here... 


[LIST=1]
[*]You _shouldn't_ need to recompile... force_monitor is also a module option, so you should be able to just set the option in /etc/modutils... Haven't tried it myself,but...

[*]The other way around force_monitor is to downgrade your firmware below the 8.XX level. I use 6.16, and don't need to use force_monitor. You can get older firmware [here]("http://ftp.lucky.net/pub.radio/software/ORINOCO/PC_Card/Firmware")

[*]The 0.15 series drivers that come with Dapper don't work with kismet for monitoring signal strength. You can tell an AP is there, but not how strong the signal is, or how much noise there is. There is a version of the 0.13 series drivers that work with 2.6.17 on the kismet website. Unfortunately these drivers don't work with stock Ubuntu kernels.
[/LIST]

Unless someone is willing to port the 0.13 drivers to 2.6.15 or fix the 0.15 drivers, it looks like the old Orinoco cards aren't such a good choice anymore.

:???: 

     --Matt

---

### Post by insyzygy on 2006-08-13
You say force_monitor is a module option, exactly what do you think is necessary to enable this without recompiling. I've used the method I outlined above successfully on a mini-pci and pcmcia card, however it would be nice (especially for the pcmcia card) to not have to recompile the drivers on each new system.

---

### Post by eightysix on 2006-09-14
Sorry to bump an old thread up, but I was just wondering if this driver upgrade will add WPA support to the Orinoco Gold card.

---

