---
title: "Faulty commands have messed up Ubuntu"
date: 2009-03-16
forum: General Help
---

### Post by cookhequeen on 2009-03-16
Hi,

I am a newbie to linux and ubuntu. I installed ubuntu on my old Dell laptop, a Dell Inspiron 2200. The wireless card was not recognized ( it's a broadcom 4318 ) so I followed [this guide]("http://blog.sampbar.com/2009/01/broadcom-bcm4318-ubuntu-intrepid/") to make sure it was recognized.

Well, I ended up entering some faulty code, so now Ubuntu will not start up properly, nor can I get wireless internet to work.

Is there any way I can reinstall Ubuntu or do something to reverse the code?

Thanks.

---

### Post by LegendofTom on 2009-03-16
If you want to reinstall, the best way is just to put that install disk back in and start over.  This guide looks like it uses some bash scripts, and if you used those, it will be hard to find what happened, unless you can post some error messages.

Also, when you do your reinstall, plug an ethernet cable into your laptop, because I imagine ubuntu has a restricted driver you can use.  Ubuntu install usually goes a lot smoother when you have internet.

---

### Post by cookhequeen on 2009-03-16
I accidentally put in some faulty code in the terminal for ubuntu. It's completely messed up my system now.

Can I reinstall Ubuntu? If so, how?

---

### Post by cariboo on 2009-03-16
You can reinstall Ubuntu the same way you originally installed it. Put the LiveCD in the drive and reboot and follow the instructions.

Jim

---

### Post by mhgsys on 2009-03-16
You don't need to do a complete reinstalling to get rid of this faulty wifi startup.
I just red the guide you followed and found this:
Step 6.
Now I have included a wifi.sh file in the zipped folder near the top. You need to put this file in &#8220;/etc/init.d/&#8221; then type these commands in a terminal:
sudo cd /etc/init.d/
sudo update-rc.d wifi.sh defaults
sudo chmod +x wifi.sh

This ensures the wifi starts on bootup!
 
So , to unable the startup just boot into recovery mode and in console typ:

```

sudo rm /etc/init.d/wifi.sh

```

Then reboot like normal.
 
also:
I found this, hope this guide will keep your wifi going.
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

> 
compwiz 18


This process is vastly simplified in Hardy. The easiest way to do it is to open the Hardware Drivers program (go to the System menu in the top left corner of the screen, and click Administration, and then Hardware Drivers) and check the Broadcom B43 wireless driver box, and reboot.
Done.

A couple of notes about that procedure:

It installs the b43 driver, which is semi-open source. The b43 driver works decently and will cover most peoples' wireless needs, and is easy to setup. However, you can also choose to use ndiswrapper, which will provide you with a slightly faster connection. For information on how to set that up, see [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560).


---

### Post by cookhequeen on 2009-03-16
Thanks for the help, everybody. I inserted the CD in and tried to autorun it, but ubuntu claims that cannot find the autorun program.


mhgsys- I typed in what you said, and since ubuntu claimed that wasn't the proble, I tried undoing the /etc/modprobe.d/blacklist line that caused the problem. That seemed to work.

I am using Intreprid, and I tried using the guide you provided. It did the automatic Gusty setup, but that didn't work. Thanks for the guide anyways.

---

### Post by perrti-y02 on 2009-03-16
You need to put the CD in before booting up the entire machine. then let the BIOS find it and boot from it. Then follow the destructions as you presumably did in the first place.

---

### Post by sampbar on 2009-04-08
The commands shouldn't have caused ubuntu to not boot but once you've reinstalled try running the .sh scripts as it removes any chance of human error.

Samuel

---

