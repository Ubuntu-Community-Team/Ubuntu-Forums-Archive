---
title: "Dual monitor user configuration causing a black screen."
date: 2014-04-30
forum: Desktop Environments
---

### Post by rtrask on 2014-04-30
Momma told me there'd be days like this....
The SSD on my desk top is failing. I work from home with remote login via citrix. When my desktop failed to boot, I grabbed my laptop which is running ubuntu studio, and loaded citrix, then connected my lap top to my 1920X1080 monitor, and went through "Settings Manager"->Display and checked the box to display to the flat screen monitor.  I'm not 100% certain, because it happened fairly quickly but I think I told it to keep the configuration. Then the screen went black. 

After I rebooted, The login screen came up, but as soon as I login both monitors go dark. On the next reboot, I was able to log in as guest, and everything is fine. The 1920x1080 monitor looks a little funky because the video on the laptop does not support that resolution, but both screens show video. After I log out and log back in and my normal user both screens go black, and the 1920x1080 monitor starts searching for an input.

I did the ctrl+alt+f1 to get to command line, added a new user with same groups & sudo, and after "service lightdm restart" I am able to login as that user, and the display is fine. Now the problem is that even after I change the configuration so that it does not go to 1920x1080 monitor, I get the same behavior. 

My laptop is a Lenovo G570.
 
root@John-1-13:~# lshw -C video
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:3000(size=64)

---

### Post by dannyboy79 on 2014-04-30
see if you can get to tty1 when you see the black screen, if so log in using your username and password. you'll need to delete a config file. this may be some help: [https://wiki.ubuntu.com/X/Config/Resolution#How_to_setup_a_dual_monitor](https://wiki.ubuntu.com/X/Config/Resolution#How_to_setup_a_dual_monitor)

---

### Post by rtrask on 2014-05-01
I was finally able to poke around and find the problem. in ~/.config/xfce4/xfce-perchannel-xml/displays.xml There was a line that set the screen resolution to 1024x768. I don't know why this would cause a problem, since the resolution of the screen is 1366x768, but it did. Changing the property "Resolution" to match the native resolution of the screen fixed the problem.

---

