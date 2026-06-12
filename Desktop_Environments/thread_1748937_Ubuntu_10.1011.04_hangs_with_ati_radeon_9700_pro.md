---
title: "Ubuntu 10.10/11.04 hangs with ati radeon 9700 pro"
date: 2011-05-04
forum: Desktop Environments
---

### Post by alethesnake on 2011-05-04
Hi all,

I read lots of messages about this problems between ati radeon graphic cards and ubuntu, but till now I was not able to solve my problem.
My problem is that my desktop with ubuntu hangs after a variable running time (10', 30', it depends).
I assumed that responsibility of this is of my graphic card, because my desktop freeze and I must restart with power button.

I installed ubuntu 10.10 with open drivers ("radeon") and I got the problem. 
I then generated the Xorg.conf file, and forced AGP to 1x, but the problem remains.
I then disabled fastwrite and dri, but the problem remains.
I did a reconfigure of xserver, but no good news.
I finally formatted and installed ubuntu natty 11.04, but after 1h of work the system hangs again.

I really don't know how I can solve my porblem, hope someone could help me.

Thanks in advance,

Ale.

---

### Post by bailout on 2011-05-04
Firstly it may be a hardware issue, ie a problem with psu, overheating, memory or hard disk. Are you sure it was running ok with another os or before installing 11.04?

Secondly I used to have a 9800pro which was the same generation of gpu. I gave up on it at least a year ago and bought a cheap 2nd hand nvidia card because I couldn't get the 9800 to work in linux any more.

ATI dropped support for the older cards and the open source drivers were putting all there effort into newer cards as well. They changed something in the drivers to suit the newer cards and it didn't work on the old ones and it didn't look likely to ever get fixed.

However, my problems were very slow performance and high cpu use not crashing.

---

### Post by alethesnake on 2011-05-10
Hi bailout,

Sorry for the delay but I received no notification and I supposed that no one aswered yet.

I have used the same pc (same hardware configuration) for a long time with windows xp, then with mandriva and suse enterprise and I never had any problem.
My problems started with maverick, and they remains after I jumped on natty.

---

### Post by Krytarik on 2011-05-10
alethesnake, I'm not coming to the same conclusion as you, only by judging that the system freezes completely. At my mom's machine, an ATI Radeon 9600XT is installed, and it's running just fine with the Xorg-Edgers' "radeon" driver, which is included by Natty by default now, although she is running Lucid 10.04. Furthermore, if you didn't manually add Xorg-Edgers' PPA in Maverick, the driver wasn't even the same as now.

So, I believe the cause is a different one, check the logs "~/.xsession-errors.old" and "/var/log/Xorg.0.log.old" to possibly get hints to it, after your system crashed the next time.

Greetings.

---

### Post by alethesnake on 2011-05-10
Hi Krytarik,

Thanks for your suggestion.

Just a doubt, could the tv I use like a monitor be involved in any way in my problem (it's a samsung 32' full hd tv connected by a dvi-to-hdmi cable)?

In any case I will come back after a check of the log files you suggested me.

Regards,

Ale.

---

### Post by Krytarik on 2011-05-10
> **alethesnake said:**
> 
Just a doubt, could the tv I use like a monitor be involved in any way in my problem (it's a samsung 32' full hd tv connected by a dvi-to-hdmi cable)?
I don't think so.

---

### Post by cragwolf on 2011-05-10
What is the brand/model of your motherboard?

---

### Post by alethesnake on 2011-05-11
> **cragwolf said:**
> What is the brand/model of your motherboard?

Hi cragwolf,

The mobo is a Gigabyte GA-8IG1000MK (rev. 1.x):

[http://www.gigabyte.com/products/product-page.aspx?pid=1655#sp](http://www.gigabyte.com/products/product-page.aspx?pid=1655#sp)

---

### Post by alethesnake on 2011-05-17
Ok, I took a look to the logs indicated (both the old and the current version immediatly after a freeze), but nothing inside them is saying me 'hey, I'm hanging your pc!'.
I also tried to remove the graphic card and deeply clean it (there was a lot of powder around the fan, but the problem remains).

What I can say is that when I switch on the pc for the first time in the day it hangs after several minutes (10/15, it depends on the workload I think). I usually speed up the hang by playing a divx or watching youtube videos.
After the first hang, following times-to-hang are shorter and shorter.

Any idea? Is there a way to check if I have some kind of temperature issue?

---

### Post by Krytarik on 2011-05-17
I don't see any related error messages in the logs either.

Check if that issue also occurs if you are running the session option "Ubuntu Classic (No effects)" you can choose at the login screen.

And yes, definitely check the various temperatures of your hardware, since the decreasing time-to-crash is pointing into that direction:
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Indicators for the Unity panel:
[https://launchpad.net/indicator-sysmonitor](https://launchpad.net/indicator-sysmonitor)
[https://launchpad.net/indicator-sensors](https://launchpad.net/indicator-sensors)

---

### Post by alethesnake on 2011-05-19
Hi Krytarik, 

I started my ubuntu in classic mode (no effects) as you suggested and I got the same problem.
I worked for about 2 hours using just the terminal and package manager, with no issue. I finally tried to stress the system a bit by opening a youtube video (in chrome) together with a mplayer video, and I got the freeze I think in concomitance with the start of the screensaver (not sure about that, it's just a suspect because the screen went black and after a few seconds the voices from the videos stopped).
I then restarted (throught the reset button) the pc, I still logged in in classic mode/no effects and run mplayer again (just it), and the system freeze again after about 5/10 minutes.
After the login I disabled the screensaver, so no interaction from him this time.

During the first two hours I literally fought against lm-sensors modules with no success..
I succesfully installed them.
I succesfully configure them (sudo sensors-detect).
I hit yes to the question about adding the relative modules in /etc/modules but I found no way to load them.

After sensors-detect my /etc/modules file was modified with the addction of it87.

I then run:

```
sudo service module-init-tools start

```

as suggested in the last lines of sensors-detect output but I got the output:

> module-init-tools stop/waiting 

I then tried to run:

```
sudo modprobe it87
```

but I got:

> FATAL: Error inserting it87 (/lib/modules/2.6.31-6-generic/kernel/drivers/hwmon/it87.ko): Device or resource busy

I then manually add the following modules to /etc/modules:

i2c-viapro
i2c-isch
eeprom
it87

but modules-init-tools failed again.

I finally modprobe every single module, but I got the same error mentioned above on it87.

Surfing on the internet I found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418246)

I cleaned /etc/modules file, reboot, run sensors-detect again, yes, yes, yes, and finally run:

```
sudo update-grub 
```

in order to generate menu.lst file. I then:

> - open /boot/grub/menu.lst
- find the line starting with "# kopt="
- do not uncomment the line, but append "acpi_enforce_resources=lax"
- save and close
- run update-grub
- reboot

No good news.

I think that at this point I made a bit of confusion between grub and grub2.. I also tried to do as follow:

> - open /etc/default/grub
- insert GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
- save and close
- run update-grub
- reboot


but the result didn't change, no sensors for me yet.

At this point I'm a bit frustrated..

---

### Post by Krytarik on 2011-05-19
Did you ever try to run
```
sensors
```
after "sudo service module-init-tools start" or after one of the followed boot-ups!?

---

### Post by narayanan9190 on 2011-05-20
i experience the same problem dude !

---

### Post by alethesnake on 2011-05-23
> **Krytarik said:**
> Did you ever try to run
```
sensors
```
after "sudo service module-init-tools start" or after one of the followed boot-ups!?

Yes, I tried to run sensors in both these cases but I always get an error like 'no sensor activated, try to run sensors-detect to..' (I don't remember the exact text now.).

In any case this evening I'll try to carefully clean every part of the pc, to substitute the thermal grease in the processor and in the gpu and so on. Let's see the result.

> **narayanan9190 said:**
> i experience the same problem dude !
:-)
With the sensors or are you talking about freezes? Have you solved your problems?

---

