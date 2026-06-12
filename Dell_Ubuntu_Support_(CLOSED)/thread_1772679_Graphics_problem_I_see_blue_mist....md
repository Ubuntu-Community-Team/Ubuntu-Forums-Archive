---
title: "Graphics problem? I see blue mist..."
date: 2011-05-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tomkat3 on 2011-05-31
Hello forums,
I've used Ubuntu 10.04 on a Dell Latitude d630 for about 6 months, so I'm still quite new to this.

I just learned how to use program called [VMD]("http://www.ks.uiuc.edu/Research/vmd/") at a workshop I'm in right now, but today I tried to run the program on my laptop, it froze. After waiting awhile I could move the mouse a bit, but I couldn't click on anything. I didn't know what to do. Is there a Ubuntu version of ctrl+alt+delete I could have used to get out of this? I held down the power button to force my computer to shut down to get out.

Things haven't been normal since. Whenever I try to run VMD or even watch random videos on the internet (except Youtube), a blue 'mist' suddenly appears on the screen and the computer stops working. It freezes like before. The only way out I know is to force it to shut down by holding down the power button.

The next time I log on, the blue mist is still there. I boot into recovery mode, and after watching random character fly across the screen Matrix style, pick the dpkg option. When I restart this time the blue mist is gone, and everything is back to normal...I think. A little while ago I watched a google video and the blue mist came back!

I'd like to blame everything on VMD and walk away, but I ran VMD on my computer yesterday and it worked. Only today have I had problems!

What's happening and what can I do to stop this?


Thanks for reading all that. Sorry if it was a bit scatter-brained. Here's some things that may be relevant, let me know if you need more!

```


$ sudo lshw -class display
  *-display               
       description: VGA compatible controller
       product: Quadro NVS 135M
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:e0000000-efffffff(prefetchable) memory:fa000000-fbffffff ioport:ef00(size=128) memory:fc000000-fc01ffff(prefetchable)

$ uname -a
Linux mr-laptop 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux


```

---

### Post by tomkat3 on 2011-06-05
*bump*

Maybe it would help if I attached these pictures:

[ATTACH]194325[/ATTACH]

[ATTACH]194326[/ATTACH]

In the morning whenever I turn on my computer I get two squashed screens with lots of blue bars. After its done with the ubuntu splash screen, it flashes for a few seconds and drops me at the command line. I can use the command line as normal. EDIT: It works normally, except that there are two screens, one on top of the other.

Also, after an hour of googling my problem in the text based web browser and rebooting when I don't find anything, things seem to go back to normal! :confused: It occasionally goes crazy with the blue bars on me every now and then, but it goes back to the regular GUI when I reboot this time

The next morning, it goes back to the weird two screen mode in the pictues --- WHAT IS HAPPENING?!!?!? ](*,)

---

### Post by marcoftheknight on 2011-06-05
These are just ideas and I have no clue what's causing the problem but no ones posted so I thought I should try to give you some ideas.

One other thing forgot to add do you actually meet the requirements for that software?
Second other thing is this really may be a driver error. Unfortunately Im with ATI and in my experience you should be able to download the lastest driver from nvd site which will have a pdf on the install instructions. This new driver may help with this problem. 

OH and I forgot ! run the program as sudo from the terminal! then you might see indications of an error.

the other options
try the following
1- Change the settings on your actual monitor there should be a option to do auto adjustments. use that if possible scroll through you different settings.

2- Change you connection to DVI if you can or use a different VGA cable.
3- Try a different monitor if you have one available.
4- change your driver to the Ubuntu regular driver the preloaded one that you get at install I can't remember exactly how to do this but there should be doc on it.


Thanks

---

### Post by tomkat3 on 2011-06-05
Thanks for the response!

Like I said in the original post, I've get a Dell Latitude d630 laptop, so there isn't an easy way to switch monitors or change the settings...unless there's a way to do it in ubuntu?

This is kind of weird, but when I go to system->Administration->Hardware Drivers, it says that "Proprietary drivers are being used to make this computer work properly" and gives me a choice between 2 NVIDIA accelerated graphics drives, one a 'version 173' and the other is 'version current', this is the recommended one I'm using.

When I check NVIDIA X Server Settings, it says that my NVIDIA driver version is 270.29?

Anyway, I tried to follow [these steps]("http://ubuntuguide.net/install-nvidia-graphical-driver-in-ubuntu-lucid-10-04") to change the driver to one I got from the nVidia website, but I got this error:

FATAL: Module nvidia not found.

I didn't have any problems before I used VMD and (now that I think of it) installed a group of updates last Tuesday. Is there a place I can check a log of updates I've installed?

---

### Post by tomkat3 on 2011-06-08
\\:D/I think I fixed it! I think the problem was the nvidia kernel module I was using. My driver was version 270.29 and the kernel module was version 173. Perhaps this explains why my computer still worked a lot of the time, and most consistently broke when I ran graphically demanding applications? Thoughts on this assessment anyone?

I don't remember exactly what I did, but basically, in desperation I had uninstalled all my graphics drivers (in other words, went to ubuntu tweak/package cleaner/clean config/select all/clean up!) Going through a combination of the Xorg wiki and installing the updated nvidia kernel module using steps similar to [this]("http://ubuntuguide.net/install-latest-nvidia-graphics-drivers-in-ubuntu-linux"), I got things working again! I haven't seen blue mist for at least  12 hours. 

I thought it was a waste of time to download a text based web browser, but if I didn't have Lynx, I wouldn't have been able to troubleshoot or google error messages when I was stuck at command line.

---

### Post by tomkat3 on 2011-06-09
I spoke too soon! Now it only screws up for about a half an hour after I first turn it on. I just noticed that after a certain amount of time in blue double decked command line, the screen goes back to black like it should. After that, if I reboot, it works like normal. Last time I just spend the time going through system folders - not even modifying anything, and it changed like that.

Upgrading the nvidia kernel module definitely fixed my problems with VMD. Graphically intense things that would have freezed it up earlier work just fine now (when I get into the GUI).

**My only problem now is this:**
After not using my computer for about an hour, when I turn it on it looks like this:

And as I said before, after running around in circles in a blue misty, double screened command line, the mist 'clears' , the background becomes black, and I can reboot and enter Ubuntu normally.

Why is my computer behaving so erratically?

---

