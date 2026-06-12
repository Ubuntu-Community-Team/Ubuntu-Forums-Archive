---
title: "Desktop Effects Suddenly Stopped Working &amp; Can't Be Re-enabled (Driver issue?)"
date: 2011-10-19
forum: Desktop Environments
---

### Post by beccatoria on 2011-10-19
Hi guys, 

I run 10.04 and have never had any issues with desktop effects until this point.  

My computer crashed, I rebooted it and desktop effects were set to "none".  I tried to enable them to "extra" and it told me that it was searching for drivers but then threw up an error that that desktop effects could not be enabled.  

I went to the Hardware Drivers section but it just says that there are no proprietary drivers in use and gives me no further options - it's a blank window, essentially.  I think this is correct, though, because I do not recall previously having used any proprietary graphics drivers on this machine - unfortunately, I'm not 100% certain as I haven't touched that side of the computer since I set the machine up over a year ago.  

All the help I can find online seems to revolve around reinstalling nvidia or other proprietary drivers, but I don't have that option as nothing comes up as available for me and I don't know how to reinstall the driver I have at the moment.  

I did find out about Compiz Check and ran it with the following results:  

> Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

Any help would be deeply appreciated.  I don't want to have to reinstall everything on this machine and I'd rather not upgrade until 12.04 is released.  But I really need to sort this out.  

I don't have a huge amount of Ubuntu knowledge - I'm still pretty much a newb, so if there's any other information you need, please let me know.

---

### Post by grahammechanical on 2011-10-19
You have an Intel graphic chip. The driver for it is most probably built into the kernel. That is why Hardware Drivers does not offer you a proprietary drivers.

Have you tried re-installing Compiz? The crash might have done something to Compiz and it is the utility that composes the images on the screen for advanced effects, if I understand things correctly.

Open Synaptic Package Manager and search for Compiz and mark anything connected with it for re-install. Afterwards reboot and see what happens.

Regards.

---

### Post by beccatoria on 2011-10-19
Thank you for the extremely swift response.  Ironically, right after giving up on several hours of googling to find a solution on my own and deciding to post here, I stumbled on the following page:  

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

Since I determined I didn't have that driver anyway and it would be good to upgrade, I did so, and it fixed the issue (though I'd note that for anyone else trying that, the instructions work fine until the final command to upgrade the kernel because that's no longer available as time as moved on.  I swapped "2.6.35-6" for "2.6.35-30" in both applicable places).  

I had to re-enable extra effects after rebooting, but this worked fine, and after a few compiz tweaks I was back to where I was.  

I apologise for not being able to comment on the reinstallation of compiz as a factor - certainly that would have been a less dramatic step to take (though the new drivers are actually noticeably better when playing back HD stuff).  

Again, thank you so much for the quick reply and the fact I now look a bit daft having found the answer I needed mere minutes after abandoning hope.  This probably has something to do with that universal law about everything being in the last place you'd look for it.  :)

---

