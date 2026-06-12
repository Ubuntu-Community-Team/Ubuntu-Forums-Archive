---
title: "poor battery life on XPS M1530"
date: 2008-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by var on 2008-07-01
hi all,

in the last april I bought a XPS M1530 with this specs:

T9300 @ 2.5 GHz
4 GB of RAM
5400 RPM HDD
9 cells battery

the problem is that, under Hardy, my battery life is very poor. I've read around and, for a 9 cells battery, the duration is set around 4 hours. however, in my case when the battery is fully charged shows a duration of only 2 hours and 40 minutes. I've also checked it pushing the phisical button and seeing about leds: the battery is on a good state.

so, the question: why the battery has a so poor life? how can I increase it under Hardy?

thanks a lot. :)

---

### Post by sc00ter on 2008-07-01
A good place to start in your attempt improve the battery life is to install and run powertop:
```

sudo apt-get install powertop
```

and then run it (using sudo):

```
sudo powertop
```

Let it run for a while, basically it will analyze your system and give suggestions for reducing the number of wake-ups thus improving your battery life.

For further information, try here:
[http://en.wikipedia.org/wiki/PowerTOP](http://en.wikipedia.org/wiki/PowerTOP)

---

### Post by sdennie on 2008-07-01
Along with the suggestion to use powertop, also check [www.lesswatts.org](www.lesswatts.org) for more power saving tips.  Also, have you timed the actual battery life?  The gnome-power-manager isn't always correct so, to get an accurate number, you really have to unplug the machine and manually time how much battery life you are actually getting.

---

### Post by var on 2008-07-01
> **sc00ter said:**
> A good place to start in your attempt improve the battery life is to install and run powertop:
```

sudo apt-get install powertop
```

and then run it (using sudo):

```
sudo powertop
```

Let it run for a while, basically it will analyze your system and give suggestions for reducing the number of wake-ups thus improving your battery life.

For further information, try here:
[http://en.wikipedia.org/wiki/PowerTOP](http://en.wikipedia.org/wiki/PowerTOP)

thanks sc00ter, powetop says to do this:

```
sudo hal-disable-polling --device /dev/scd0
```

and system replies:

*Polling is already disabled on the given drive.*

and these other commands:

```
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
```

that I did as root. but are these last two commands' effects active after reboot?

@vor: yep, in my case gnome-power-manager is accurate.

thanks to all. :)

---

### Post by sdennie on 2008-07-01
> **var said:**
> but are these last two commands' effects active after reboot?


They aren't retained over a reboot, no.  You can either put all your changes into /etc/rc.local (though, pm-utils will helpfully clobber some of them for you) or you can use a script to toggle on/off power savings features depending on whether the machine is plugged in.  I use: [http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644)

---

### Post by var on 2008-07-02
nothing to do my friends, my battery life is the same (always 2 hours and 40 minutes). :(

what can I do?

thanks.

---

### Post by Cheburator on 2008-07-02
hm..ubuntu is not really a power saver. Can get 2h and 20 min on my compaq 6715b. On XP 3h is minimum.

---

### Post by damis648 on 2008-07-02
I, too, have low battery life. This is not something easily fixable because the kernel consumes lots of power. Try the following:
Right click your panel and click "Add to Panel". Find "CPU Frequency Scaling Monitor" and add it twice, one for each core. Now close that and right click one of them and click "Preferences". Select "CPU 1" as the monitored CPU. Close that. Then open a terminal and:
```
sudo dpkg-reconfigure gnome-applets
```
and press OK at the prompt. Say also yes, that it should run with root privileges.  After that, you may click one of the CPU scaling monitors on your panel and select a scheme on the bottom or frequency on the top. Of the schemes, conservative starts at 800mhz and goes up when you need it and stays up. OnDemand goes up when you need it, but returns to 800mhz when not needed. Performance keeps it full-speed ahead at 2.5ghz. Finally, Powersave keeps it at 800mhz. If you want more tips for powersaving and other things on the M1530, check this wiki: [https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530?highlight=(M1530](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530?highlight=(M1530))
Good Luck!

---

### Post by sdennie on 2008-07-02
> **Cheburator said:**
> hm..ubuntu is not really a power saver. Can get 2h and 20 min on my compaq 6715b. On XP 3h is minimum.

I don't think that's the case.  I admit my XPS m1330 has only ever run Ubuntu, but, the battery life is exceptional with the 9 cell battery (over 6 hours).

> **damis648 said:**
> I, too, have low battery life. This is not something easily fixable because the kernel consumes lots of power. Try the following:
Right click your panel and click "Add to Panel". Find "CPU Frequency Scaling Monitor" and add it twice, one for each core. Now close that and right click one of them and click "Preferences". Select "CPU 1" as the monitored CPU. Close that. Then open a terminal and:
```
sudo dpkg-reconfigure gnome-applets
```
and press OK at the prompt. Say also yes, that it should run with root privileges.  After that, you may click one of the CPU scaling monitors on your panel and select a scheme on the bottom or frequency on the top. Of the schemes, conservative starts at 800mhz and goes up when you need it and stays up. OnDemand goes up when you need it, but returns to 800mhz when not needed. Performance keeps it full-speed ahead at 2.5ghz. Finally, Powersave keeps it at 800mhz.


Setting the CPU governor to powersave generally will not increase battery life (and will probably shorten it).  It seems counter intuitive but, ondemand actually saves more power.  See: [http://mjg59.livejournal.com/88608.html](http://mjg59.livejournal.com/88608.html)

> 
 If you want more tips for powersaving and other things on the M1530, check this wiki: [https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530?highlight=(M1530](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530?highlight=(M1530))
Good Luck!

The power savings tips there are good but don't work exactly how one would expect over a suspend/resume if you suspend while on/off battery and resume in the opposite state.  Unfortunately, Hardy further complicates things with the addition of pm-utils and so the nvidia tip (which I was surprised to see link back to my original on the nvidia forums :) ) won't work quite right either.

I'll put together a thread with all the scripts I'm using on my XPS m1330 and explanations of what they are doing, along with general usage tips for saving power and post them in this forum.  There is no silver bullet to power savings, it's just a lot of little changes that add up.

Edit:
Said guide can be found here: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

---

### Post by motin on 2008-07-22
> **var said:**
> nothing to do my friends, my battery life is the same (always 2 hours and 40 minutes). :(

what can I do?

thanks.

Did you implement the tips and tricks suggested by vor at [http://ubuntuforums.org/showthread.php?t=729644](http://ubuntuforums.org/showthread.php?t=729644) (and possible at [http://ubuntuforums.org/showthread.php?t=847773)?](http://ubuntuforums.org/showthread.php?t=847773)?)

You should really see an increase in battery life, even though implementing these tips and tricks can be a bit daunting...

---

### Post by JSHN on 2008-07-22
It seams quite strange.
I also have the M1530 and my battery lasts 5hours on a full charge.
The nvidia is running at power-save-mode and also the CPU is running at 800MHz as lowest, then throttle higher if needed.
I also have some tweaks but I need to check my PC at home first.

I have the 2.1GHz CPU, 7200rpm hdd, nvidia 8600m gt 256 mb, 4gb ram, 1680x1050 lcd, 9cell battery.

---

### Post by rony474 on 2008-07-25
try to install [COLOR="Red"]Kpowersafe[/COLOR], and CPU to 800 MHZ ,brightess to 70%,i have a 1400 Dell Vostro , and more than 3:40 With a 9 Cell battery,... have a nice day ... :)

---

### Post by sdennie on 2008-07-25
> **rony474 said:**
> try to install [COLOR="Red"]Kpowersafe[/COLOR], and CPU to 800 MHZ ,brightess to 70%,i have a 1400 Dell Vostro , and more than 3:40 With a 9 Cell battery,... have a nice day ... :)

Pegging the CPU to 800Mhz is probably decreasing your battery life.  It seems non-intuitive but, letting the CPU go to max power when it needs it will save battery life.  For a good explanation of this, google for "intel race to idle" or see this site: [http://mjg59.livejournal.com/88608.html](http://mjg59.livejournal.com/88608.html)

I have an m1330 and not an m1530 but, I get nearly 7 hours of battery from a 9 cell using the guides that are linked several times in this thread and are in my signature.

Edit: Didn't mean to quote one post.

---

### Post by articpenguin on 2008-07-25
Dont forget Lithium Ion batterys lose there max charge capacity overtime

---

