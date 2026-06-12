---
title: "Can't boot ANY Linux distro!"
date: 2009-01-25
forum: General Help
---

### Post by Muphin Man on 2009-01-25
I've been having this problem for the past year and I've finally gotten sick of searching around for a solution. I cannot boot into ANY Linux distribution. Literally. They all hang when they try to boot. Only when I go cancel the load and go into console to type "startx" does it actually boot. The place this problem occurs (at least with Ubuntu and Fedora) is when trying to start Bluetooth. Which my computer doesn't have. There is no option to disable Bluetooth in the Bios. I find this problem to be even more unusual because I have actually changed motherboards to find the same exact problem. Totally different manufacturers too, I went from MSI to Gigabyte. So at least we know the problem isn't the motherboard. I'm using a Intel Dual Core processor running at 2.89 GHz. I have a NVidia GTX 260 graphics card, which used to be a 8600 GTS, so we know it's not that either. I have 4 GB of RAM and a Lite-On DVDRW drive. If you think I need to go into more detail about my system specs then let me know.

I would love to be able to use Linux again!

Thank you for your help

---

### Post by BLTicklemonster on 2009-01-25
Exactly where do you first see the problem? I had a computer that had onboard video, and put a pci-e card in it. I couldn't boot to linux for anything. I did finally notice that the bus id address in the error I got about x not being configured properly showed my card at the address of 2:0 or something. I just had to reconfigure x to point there, and it loaded right up. Watch your error messages if you get any and see if they tell you anything like that. Hopefully it's that simple, and you can edit something and get going. 

As far as killing bluetooth, System, Preferences, Sessions and kill bluetooth. Hope that helps.

---

### Post by Muphin Man on 2009-01-25
I'll try to write down the error next time I see it, but as far as I can remember what happens is when it gets to the loading bar, it stops about 7/8ths of the way done and when I go to the text version of the loader it has all the normal things but then hangs at bluetooth. So it would have something like:

USB                                [OKAY]
VIDEO                              [OKAY]
BLUETOOTH

And then it would just hang there.

Also, I would disable bluetooth in the Preferences, but I can't even GET to that menu because of the hang up.

Thanks!

---

### Post by BLTicklemonster on 2009-01-25
You said you can cancel, startx and it would boot? If I read that right, try killing bluetooth there, then reboot. Hopefully you'll be in business.

---

### Post by txcrackers on 2009-01-25
Have you tried removing the Bluetooth packages? That would pretty much guarantee that it doesn't try to start...

---

### Post by Muphin Man on 2009-01-27
How would I go about removing the Bluetooth packages from my ISO?

---

