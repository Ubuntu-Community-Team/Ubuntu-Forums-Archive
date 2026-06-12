---
title: "Dell XPS M1330 - Warm Palmrest"
date: 2008-06-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dagurb on 2008-06-26
I have recently started using a WUPI install of Ubuntu 8.04 on my laptop. The problem is that the palm rest gets very warm, even if the computer is just idling. The problem is not confined to either side of the palm rest. The whole thing gets uncomfortably warm for my wrists.

Windows Vista does not have this problem and the computer remains quite cool under most circumstances when running it. Even while running intensive computer games such as Half-Life 2.

I have paid close attention to CPU usage on my computer and that does not seem to be a problem. As I'm writing this the CPU remains at a rather steady 5-15% @ 800MHz.

---

### Post by atlas95 on 2008-06-26
I have the same problem ! same computer, but I have memory which is warmest than the default, and a hdd 7200rpm :/
Maybe we can tweak something for make it coolest?

---

### Post by IamReck on 2008-06-27
Same problem!  Only when I do not have it on my cooling station though...

I don't use Vista, so I don't know if it happens there or not.

---

### Post by atlas95 on 2008-06-27
What is your cooling station? Is it expensive? Could you give me an ebay/ebay like link please?
Thanks :)

---

### Post by IamReck on 2008-06-27
You can't but it anymore, it is just a platform with two fans that you put under your laptop, just google around for Laptop Cooling, or something to that effect.

It works though.

---

### Post by sdennie on 2008-06-27
I was seeing this too.  The things I did to fix it were:

1) Bought some compressed air and cleaned out the vents on the machine.

2) Upgraded to BIOS A11 (which states, "Added enhancement for thermal control" but, it doesn't say anything specific about what that means)

I'm not sure which made the difference (maybe both) but, the machine is running nearly 10C cooler.

---

### Post by Kernel Sanders on 2008-06-28
Same problem with the M1330, and mine has been running Windows since I bought it.

I'm about to upgrade to Mint though :guitar:

---

### Post by IamReck on 2008-06-29
> **vor said:**
> I was seeing this too.  The things I did to fix it were:

1) Bought some compressed air and cleaned out the vents on the machine.

2) Upgraded to BIOS A11 (which states, "Added enhancement for thermal control" but, it doesn't say anything specific about what that means)

I'm not sure which made the difference (maybe both) but, the machine is running nearly 10C cooler.

How did you upgrade the BIOS?

---

### Post by sdennie on 2008-06-30
I more or less followed the Dell instructions from here: [http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx](http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx).  The final step didn't actually work for me and so I ended up having to manually select the system-bios-xps-m1330 package via synaptic.  However, now I get BIOS updates via the update manager whenever they become available.

Note: If you do this, on my machine, when you do the reboot, it's a bit worrisome in that the screen has a bunch of vertical lines that gradually fade in and then the machine reboots again.  It's my second BIOS update and it's done it both times.  It doesn't appear to be anything to worry about.

---

### Post by dagurb on 2008-06-30
Well, I've just updated the firmware to A11 and it's still too hot! :(

---

### Post by flakrat on 2008-07-01
Dang, didn't realize you could upgrade the BIOS that way.

I just used a USB floppy drive from work, copied the EXE BIOS update file to a DOS bootable floppy and ran it after booting the laptop to DOS. The BIOS updated without any spooky messages, which is comforting.

As for the warm palm rests, I don't have them, however the touchpad is warmer than I'd like, but it may be the same in Windows for all I know.

How do you tell what the CPU temperature is?

---

### Post by sdennie on 2008-07-01
For the temperature, try:

```

acpi -t

```

---

### Post by flakrat on 2008-07-01
Cool, thanks:

```
acpi -t

Thermal 1: ok, 38.0 degrees C
```

---

### Post by dagurb on 2008-07-02
My CPU goes up to ~80°C during heavy processing but while browsing or watching videos at 800MHz it stays around 56°C. Is that too hot? All the while my palm rest is still very hot.

---

### Post by sdennie on 2008-07-06
I've been testing this out the last few days and I think a lot of the palmrest heat is coming from the hard drive (and possibly the wifi card).  I've been using my m1330 on battery a lot lately and, basically using the instructions [here]("http://ubuntuforums.org/showthread.php?t=847773"), the difference in palmrest temperature is noticeable (it wasn't too bad before but, now it's almost room temperature on battery).  I honestly can't say if it's a function of my guide or a function of the BIOS doing something automatically when on battery power but, it might be worth it to try it for a day and see if you notice a difference.

---

