---
title: "FGLRX causes 9.10 to crash on ATI Mobility Radeon 2600 HD"
date: 2009-10-30
forum: Desktop Environments
---

### Post by Akkifokkusu on 2009-10-30
I know I made a thread for basically the same problem when 9.04 was released, but I'm hoping there's new insight. If I install FGLRX, either from "Hardware Drivers" or from ATI's site, X crashes on boot and brings me to the bash shell, but it's blinking and hangs and is unsuable.

Now, I always hear people saying that ATI dropped support for older cards in their drivers, but my card is specifically listed on ATI's list of supported cards for this driver. So... any idea what's going on?

---

### Post by markbuntu on 2009-10-30
Try this

Open a terminal and...

sudo aticonfig --initial -f

after the driver is installed and before you reboot. You should see some message like " found unititialized file...storing old xorg.conf as xorg.1" or something like that. 

I ran into this with my HD3650 a long time ago, maybe intrepid, so anytime that fglrx gets installed I do that before I reboot. I think what happens is the driver gets installed but xorg.conf is not initialized so X gets very confused.

---

### Post by Marrkk on 2009-10-31
did u try the Hardware drivers utility ?
it worked for my ATI 3200 HD ..
except in Kubuntu, 
(because jockey-kde is STILL broken best use jockey-gtk in KDE)

---

### Post by Akkifokkusu on 2009-10-31
Yeah, I've tried both. I've just looked at my Xorg log, and the error I get is:

Invalid video BIOS signature!

I've seen posts from different people who got that error changing their graphics modes in the BIOS from Hybrid to Discrete, but neither do I have that option, nor do I think I actually HAVE Hybrid graphics. So... yeah...

---

### Post by teilnehmer on 2009-11-02
I have the same card (not sure about "mobility", but all the rest is the same) and had the same problem on 9.04. I was planning to try again with my new 9.10, but your post makes me reconsider...

I've read that xorg.conf isn't really used anymore - if I do install the fglrx-drivers, how would I get my old settings back?
If I knew for sure using the old xorg.conf would do the trick, I'd be willing to try your tip, markbuntu. 

Bye, 

Jan

---

### Post by markbuntu on 2009-11-02
Some of the 3xxx and 4xxx integrated graphics processors had some problems if the memory for them was set to 512MB or lower in the bios. You could try increasing the memory for the gpu in the bios and see if that fixes the invalid bios signature problem. I have not heard of this effecting any Mobility gpus but you never know.

---

### Post by DougieFresh4U on 2009-11-02
Don't know if this will work for your card, but I have the HD3200 and I am using the [.32 kernel/rc5]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") with the [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") and my ATI card is working better than using the fglrx
I will say that fglrx did work in my Jaunty and Karmic installs.

---

### Post by Akkifokkusu on 2009-11-02
> **teilnehmer said:**
> I've read that xorg.conf isn't really used anymore - if I do install the fglrx-drivers, how would I get my old settings back?

I believe that aticonfig automatically creates a backup of your xorg.conf file. Either way, if things screw up, then deleting xorg.conf will cause the system to default to either the open source drivers (if you still have them installed) or to low-quality mode which you can then use to reinstall the open source drivers. At least, that's been my experience.

> **markbuntu said:**
> Some of the 3xxx and 4xxx integrated graphics processors had some problems if the memory for them was set to 512MB or lower in the bios. You could try increasing the memory for the gpu in the bios and see if that fixes the invalid bios signature problem. I have not heard of this effecting any Mobility gpus but you never know.

Sadly, I have to video card-related options in my BIOS.

> **DougieFresh4U said:**
> Don't know if this will work for your card, but I have the HD3200 and I am using the [.32 kernel/rc5]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") with the [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") and my ATI card is working better than using the fglrx
I will say that fglrx did work in my Jaunty and Karmic installs.

That looks delicious and promising, but I'm almost positive that I'll end up with the same error, because it seems that my problem is coming from the interaction between the driver and the BIOS. But it's definitely worth a shot. Thanks.

---

### Post by andrey.fr on 2009-11-09
I have Lifebook n6460 also, and after trying this and that in Jaunty I decided to hold on with Ubuntu as it is unusable for my hardware and for me.

I thought about checking if some notebook vendor sells notebooks with mobility radeon hd 2600 and some version of Linux, but didn't do so yet. If such vendor exists they may have correct drivers for our video.

Anyway, lets touch bases and see if we find the solution for the problem.

---

### Post by Angus77 on 2009-11-09
> **DougieFresh4U said:**
> Don't know if this will work for your card, but I have the HD3200 and I am using the [.32 kernel/rc5]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") with the [xorg-edgers ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") and my ATI card is working better than using the fglrx
I will say that fglrx did work in my Jaunty and Karmic installs.

I just tried this, and my HD 3200 is working great!

---

### Post by dmglouis on 2009-11-09
This is regarding the original post. I had the same problem with Karmic, it has to do with xorg.conf not being generated.

[QUOTE=Akkifokkusu]I know I made a thread for basically the same problem when 9.04 was released, but I'm hoping there's new insight. If I install FGLRX, either from "Hardware Drivers" or from ATI's site, X crashes on boot and brings me to the bash shell, but it's blinking and hangs and is unsuable.[/QUOTE]

Basically using the instructions from [this]("http://ubuntuforums.org/showthread.php?t=1299188") thread, all you have to do is boot into recovery mode and run the following command:

```
sudo aticonfig --initial -f
```

I don't know about the acpi_services command in the thread I linked but the one above should solve your problems. It worked for me.

---

### Post by tai1spin on 2009-12-10
I have the same 'bios' problem and x won't start either. I have mobility 2600 radeon hd w/256 dedicated and up to 512 shared. However nothing I try, including the aticonfig --initial-f helps. 

Any ideas?

---

