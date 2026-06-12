---
title: "Compiz limited functionality on Hybrid graphics AMD Radeon 6630M 1GB DDR3 VRAM / Inte"
date: 2011-07-31
forum: Desktop Environments
---

### Post by opodaniel on 2011-07-31
I own a new laptop Sony Vaio VPCSA with [COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=Verdana]Hybrid graphics AMD Radeon 6630M 1GB DDR3 VRAM / Intel HD 3000 and  I installed Ubuntu 11.04 alternate on it. There are some small problem since the hardware is new but the one thing that I need fix now is the grid plug-in of compiz is not working. 
What I want is to be able to maximize/tile windows when I drag them to the left/top/right edge of the screen. In this moment I drag and it stay where I drag them. So now, in order to have 2 windows side by side , each taking half of the screen, I need to use the mouse to accomplish this. It is ok once or twice, but when I need to open more files and do same thing again and again is frustrating.
I don't know if it is :
- because of the distro : Ubuntu alternate cd
- because of the hardware
- because of some settings

Software  I installed
- Ubuntu 11.04 32-bit
- compiz Settings Manager
- open community driver Ati for the Radeon card ( official non-free was not so good)
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by opodaniel on 2011-08-11
Found temporary solution 
- switch off the radeon card
- blacklist radeon
The system use now just the intel HD 3000 Sandy Bridge graphics. Sometimes there are some strange problems and the laptop have really poor battery autonomy but the overall experience is livable.

---

### Post by sadata on 2011-08-14
> **opodaniel said:**
> Found temporary solution 
- switch off the radeon card
- blacklist radeon
The system use now just the intel HD 3000 Sandy Bridge graphics. Sometimes there are some strange problems and the laptop have really poor battery autonomy but the overall experience is livable.

I know how to blacklist the radeon driver, but how exactly do you 'switch off the radeon card'?  I have a similar situation with a Sony Vaio VPCSB11FXB where the Radeon card is generating a lot of heat (70 deg C) and since I'm only using the Intel adapter, I'd like to literally power down the Radeon if possible. The fan on this unit is insane. Runs all the time (even in 800 MHz Powersave mode)  and sounds like a jet engine trying to take off. Thanks.

---

### Post by sadata on 2011-08-14
> **sadata said:**
> how exactly do you 'switch off the radeon card'?

Looks like you can power down the card by echoing OFF to the file listed below. This path only exists if radeon is loaded, hence the 'modprobe radeon' if it's blacklisted.

modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

Overall system temperature has dropped by 10 to 15 degrees Celcius. My fan hardly runs at all now and I've got the CPU applet set to Ondemand. 

I found this information in the following post:

[http://ubuntuforums.org/archive/index.php/t-1752202.html](http://ubuntuforums.org/archive/index.php/t-1752202.html)

---

### Post by opodaniel on 2011-08-15
Thanks for the post. I was making a big mistake. By blacklisting Radeon I wasn't switching it off. I was simply disabling the drivers from loading, hence no more switcheroo. I re-enabled the Radeon by commenting in *$sudo gedit /etc/modprobe.d/blacklist.conf*
> # blacklist radeon and using switcheroo I switch off Radeon *$sudo gedit /etc/rc.local*, before exit 0:

> chown -R $USER:$USER /sys/kernel/debug
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch


Now I got like 4 hours of battery life in Ubuntu.

---

