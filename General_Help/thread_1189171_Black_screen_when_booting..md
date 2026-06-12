---
title: "Black screen when booting."
date: 2009-06-16
forum: General Help
---

### Post by prions on 2009-06-16
Whenever I boot Ubuntu, the splash screen appears, but in that time before the login screen, my screen turns black.

But, its not only black. Theres green and red streaks across it, and the screen flickers to that and solid black.

I had this problem yesterday and repartitioned my whole drive. It seemed fine but when I started up again it happened. :(

Running from my live cd.

---

### Post by Legace on 2009-06-16
Did you happen to install ATi drivers?

---

### Post by prions on 2009-06-16
I dont think I had any drivers installed.

According to EnvyNG, none of my drivers are compatible nor installed.

But my drivers were ATI before I used ubuntu.

---

### Post by prions on 2009-06-16
Still not fixed. I tried gdm start in start mode, but nothing worked.

---

### Post by wpshooter on 2009-06-16
Have you tried installing using the safe graphics mode parameter and if that does not work, then trying installing from the ALTERNATE (text based) CD version.

---

### Post by prions on 2009-06-16
I REALLY don't want to reinstall. 


It was working for a couple days then this happened, so I dont think thats the problem.

---

### Post by prions on 2009-06-17
Still not fixed.

Sometimes when I boot I can see fragmented pictures of what I was doing before I shut down.

---

### Post by martin_legion on 2009-06-17
It sounds like you may have updated the video drivers or something like that. I saw it happen many times.
All I can tell you to try is this command and see if helps:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorf.conf.bak
sudo dpkg-reconfigure xserver-xorg

```

It will ask some questions about keyboard and language, and when done, you can reboot or try:

```
sudo /etc/init.d/gdm restart
```

Good luck

---

### Post by prions on 2009-06-17
The first code doesnt do anything. 

The second one worked, but I got this after it was done"

```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20090617164118
```

Then I did the restart but the same thing happened.

---

Should I boot in safe mode and run these from the kernel?

---

### Post by prions on 2009-06-17
Sorry for bumping again, but this is serious. 

I havent been able to fix this yet, I hardly have a computer anymore. :/

---

### Post by prions on 2009-06-18
bump

---

### Post by t4thfavor on 2009-06-18
If reconfiguring the XServer did not fix anything, your best hope (for someone fairly new to Linux) is to reinstall, and then keep track of exactly when the problem happens.

I also highly recommend switching to a cheapo Nvidia card, or at least not using the ATI drivers.

I had onboard ATI graphics, so I picked up a PCI Express NVidia 8400GS for 39.99 and its worked flawlessly for months.


I have heard nothing but bad news with ATI as of late, really a shame since they used to be so good.

---

### Post by prions on 2009-06-18
Maybe. But I like to play games and I dont think installing a new card will solve my game problems also.

---

### Post by t4thfavor on 2009-06-18
I was just saying that since I got off the ATI cards I have had a much more enjoyable Linux Experience, all while getting 102fps on Nexuiz, and playing WoW (Not me, but my Brother, I stayed off the World of WarCRACK).

If you can find an old NVidia card, it will work better too, I have a few NVidia 6600 series AGP cards that are still working gread in my "old P4" machines.

I'm not saying you will never get the ATI card to work, its just going to be alot of work.

---

### Post by prions on 2009-06-18
Alright, I have a gateway mx6426 and I'm not sure if I can replace my card. If not, I'll repartition with Windows. 

I'm due for a new rig in the near future. I'll be sure to get Nvidia on it then.

---

### Post by candtalan on 2009-06-21
I guess that there is a typo here
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorf.conf.bak

```
is probably intended to read
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```

---

