---
title: "Is there any way to configure thresholds for the different fan speeds?"
date: 2008-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by motin on 2008-06-27
My XPS M1330 seem to trigger the maximum fan speed (level "2") whenever the CPU is around/above 46 and the GPU is around/above 58 degrees. 

This seems very aggressive and power-consuming, since CPU temps of around 50-60 is fully acceptable and the GPU could well run prolonged periods between 65-75. I strongly believe that the medium fan speed (level "1") would do perfectly fine at these levels, and that the fan need not to be on at all at temperatures around 45 (CPU) and 58 (GPU). (Please do correct me if my guesses are faulty!)

The i8k kernel modules together with i8kmon opens up for a way of controlling this. When configured and started it does it's job well. HOWEVER, since the ordinary fan control method in the XPS M1330 always seems to be running, the fan speed is set back to maximum every 1-10 seconds, and won't turn back again until i8kmon re-sets it to the desired level. 

This means that by turning down the timeout value for i8kmon to 1 second, it is possible to have the desired fan speeds active around 80-90% of the time (by constantly down-adjusting the fan speed every setting). However, since the fan speeds up every 1-10 seconds, the resulting noise scene is much more irritating than a fan that constantly runs at full speeds...

So - does anyone know more about how the fan speeds are adjusted (BIOS?), if there is any possibility to adjust the temperature thresholds for this mechanism (making ik8mon obsolete), or inactivating it while i8kmon is running? As a last resort - does anyone know how to program i8kmon to be able to have timeouts less than 1 second (allowing it to constantly fight down the automagic mechanism)?

Thankful for any advice! This fan noise is the only thing bothering me when working with the wonderful XPS M1330!

Cheers

(I have asked a question on launchpad against the i8kutils package about this: [https://answers.launchpad.net/ubuntu/+source/i8kutils/+question/37595](https://answers.launchpad.net/ubuntu/+source/i8kutils/+question/37595))

As a side note, I just wrote a guide on how to setup i8k: [http://ubuntuforums.org/showthread.php?p=5275415#post5275415](http://ubuntuforums.org/showthread.php?p=5275415#post5275415)
Hopefully it will be helpful as soon as the above issue is sorted out.

Other relevant threads:
[XPS M1330] GPU Temperature constantly high || Fan is almost constantly running at full speed and is never turned off in Ubuntu
[https://bugs.launchpad.net/dell/+bug/243637](https://bugs.launchpad.net/dell/+bug/243637)

CPU fan issues with Gusty (Dell xps M1330)
[http://ubuntuforums.org/showthread.php?p=5275651](http://ubuntuforums.org/showthread.php?p=5275651)

M1330 Fan Noise
[http://ubuntuforums.org/showthread.php?p=5276067](http://ubuntuforums.org/showthread.php?p=5276067)

---

### Post by bubbalouie on 2008-06-29
I8kmon can have timeouts of less than one second, open the file /usr/bin/i8kmon in an editor, it's little more than a script, off hand the timeout variable is set in milliseconds, it should be getting scaled by 1000 from the original seconds value in there somewhere. Unfortunately I don't remember which line it is that needs changing as I've only got a modded version, I've attached my version (I hope it's the modified one) if you'd like to have a look. I no longer use the i8k tools so I can not test this right now, it did previously work as expected when updating every 250ms, I expect this is still the case.

I'm sorry I don't have a more elegant solution besides hacking the original tool (CPU utilisation may increase a few percent because of this change).  I decided dellFanD (attached my hacked version) is a better candidate for hacking as C does not need to be interpreted, though I also abandoned that path of attack. If a lower speed is forced than the BIOS wants an 'argument' begins, once you close your fan controlling application (either i8kmon or dellfand) the BIOS just forces the fan to stay at high speed regardless of temperature until the laptop is turned off and on again (I no longer have any of the fan control tools running for this reason).

I found that focusing on reducing power consumption has a beneficial effect on temperatures and fan activity, perhaps some other intrepid posters can share their results, however, I primarily focused on reducing wake-ups (intel powertop & lesswatts.org, was over 500 wakeups a second now less than 60 when idle), using the MC power saving scheduler (echo 1 > /sys/devices/system/cpu/sched_mc_power_savings) and reducing the CPU voltages (linux-PHC [http://ubuntuforums.org/showthread.php?t=786402&page=6](http://ubuntuforums.org/showthread.php?t=786402&page=6) ). 

The above approach, although not perfect will: 
[LIST]
[*]Improve battery life (lower power consumption)
[*]Improve system life (generally lower temperatures and less extreme/frequent thermal cycling)
[*]Improve usability (ever used a hot laptop?)
[*]Improve temperature (less power = less heat)
[*]Improve noise (less heat = less fan)
[/LIST]

Other than the above, passive laptop cooling stands may also help, I use a cookie cooling rack due to it's excellent air flow (like a baker uses, this is only practical with a separate mouse and keyboard due to the elevation, but angled devices are available from places like [http://www.dealextreme.com](http://www.dealextreme.com) for a fair price).

Cheers

Ryan

---

### Post by motin on 2008-07-22
Thanks man!

The relevant line (126) in /usr/bin/i8kmon looks like:
```
    set status(timer) [after [expr $config(timeout)*1000] {status_timer}]
```

... which should be changed to:
```
    set status(timer) [after [expr $config(timeout)*200] {status_timer}]
```

Or similar low timeout. 

I have the following /etc/i8kmon:
```
# Run as daemon, override with --daemon option
set config(daemon)      1
# so that killall i8kmon kan be executed to kill i8kmon upon too high temperatures

# Automatic fan control, override with --auto option
set config(auto)        1

# Report status on stdout, override with --verbose option
set config(verbose)     1

# Status check timeout (seconds), override with --timeout option
set config(timeout)     1

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
#set config(0)  {{-1 0}  -1  52  -1  65}
#set config(1)  {{-1 1}  41  66  55  75}
#set config(2)  {{-1 1}  55  80  65  85}
#set config(3)  {{-1 2}  70 128  75 128}

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
set config(0)   {{-1 0}  -1  46  -1  46}
set config(1)   {{-1 1}  46  63  46  63}
set config(3)   {{-1 2}  63  128  63  128}

# end of file

```

And "gnome-terminal -c i8kmon" bound to the Ctrl + Alt + Shift + Q shortcut (Q for Quiet...). 

A am totally with you on the track that the only real solution involves getting down power consumtion, and for that we are together rounding up the best XPS M1330 power saving tips and scripts at [http://ubuntuforums.org/showthread.php?p=5381382](http://ubuntuforums.org/showthread.php?p=5381382)

However, this usage of i8kmon is a great intermediate work-around for me. At least now I can tell the laptop to be quiet for the periods that I can accept a warm palmrest but not disturbing fan noise... 

Thanks again!

---

### Post by oli_peps on 2008-08-07
Thanks to both of you for this very interesting topic. I have configured i8kmon for my M1330 following your guidelines, and I'm now able to keep the fan mostly under control. I have also added the i8kmon gui to my panel using the gnome applet swallower (as proposed by motin in another post), so that I can easily suspend the daemon in case the laptop becomes too hot. 

The only remaining problem is that, even with the reduced timeout value, the fan kicks in almost every ~5 sec for a very short while. Is it also the case for you? Did you find a workaround?

---

### Post by motin on 2008-08-12
> **motin said:**
> Thanks man!

The relevant line (126) in /usr/bin/i8kmon looks like:
```
    set status(timer) [after [expr $config(timeout)*1000] {status_timer}]
```

... which should be changed to:
```
    set status(timer) [after [expr $config(timeout)*200] {status_timer}]
```

Or similar low timeout. 

I have the following /etc/i8kmon:
```
# Run as daemon, override with --daemon option
set config(daemon)      1
# so that killall i8kmon kan be executed to kill i8kmon upon too high temperatures

# Automatic fan control, override with --auto option
set config(auto)        1

# Report status on stdout, override with --verbose option
set config(verbose)     1

# Status check timeout (seconds), override with --timeout option
set config(timeout)     1

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
#set config(0)  {{-1 0}  -1  52  -1  65}
#set config(1)  {{-1 1}  41  66  55  75}
#set config(2)  {{-1 1}  55  80  65  85}
#set config(3)  {{-1 2}  70 128  75 128}

# Temperature thresholds: {fan_speeds low_ac high_ac low_batt high_batt}
set config(0)   {{-1 0}  -1  46  -1  46}
set config(1)   {{-1 1}  46  63  46  63}
set config(3)   {{-1 2}  63  128  63  128}

# end of file

```

And "gnome-terminal -c i8kmon" bound to the Ctrl + Alt + Shift + Q shortcut (Q for Quiet...). 

A am totally with you on the track that the only real solution involves getting down power consumtion, and for that we are together rounding up the best XPS M1330 power saving tips and scripts at [http://ubuntuforums.org/showthread.php?p=5381382](http://ubuntuforums.org/showthread.php?p=5381382)

However, this usage of i8kmon is a great intermediate work-around for me. At least now I can tell the laptop to be quiet for the periods that I can accept a warm palmrest but not disturbing fan noise... 

Thanks again!

> **oli_peps said:**
> Thanks to both of you for this very interesting topic. I have configured i8kmon for my M1330 following your guidelines, and I'm now able to keep the fan mostly under control. I have also added the i8kmon gui to my panel using the gnome applet swallower (as proposed by motin in another post), so that I can easily suspend the daemon in case the laptop becomes too hot. 

The only remaining problem is that, even with the reduced timeout value, the fan kicks in almost every ~5 sec for a very short while. Is it also the case for you? Did you find a workaround?

The only workaround we've found makes the fan kick in more seldomly and then for a shorter period of time. It is found in the reply just above yours - decrease 1000 -> 200 i i8kmon. 

Then of course the real solution is to find a way to have your lappy stay cool. Check the links mentioned previously in this thread, and also this the main XPS thread: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

---

### Post by motin on 2008-08-12
> **oli_peps said:**
> Thanks to both of you for this very interesting topic. I have configured i8kmon for my M1330 following your guidelines, and I'm now able to keep the fan mostly under control. I have also added the i8kmon gui to my panel using the gnome applet swallower (as proposed by motin in another post), so that I can easily suspend the daemon in case the laptop becomes too hot. 

The only remaining problem is that, even with the reduced timeout value, the fan kicks in almost every ~5 sec for a very short while. Is it also the case for you? Did you find a workaround?

The only workaround we've found makes the fan kick in more seldomly and then for a shorter period of time. It is found in the reply just above yours - decrease 1000 -> 200 i i8kmon. 

Then of course the real solution is to find a way to have your lappy stay cool. Check the links mentioned previously in this thread, and also this the main XPS thread: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

---

### Post by Yeti can't ski on 2008-11-07
I updated the BIOS of my Dell XPS M1330 (which became noisy after upgrade to Ibex) to versio "A12" and the fan noise problem was solved just like magice. It is much more silent now than before, when I used Hardy Haron, and the computer is not overheating. 

If anyone is interested in this:

[http://ubuntuforums.org/showthread.php?t=948556&page=3](http://ubuntuforums.org/showthread.php?t=948556&page=3)

and for Dell's Linux Bios updating page:

[http://linux.dell.com/repo/firmware/bios-hdrs/](http://linux.dell.com/repo/firmware/bios-hdrs/)

Good luck!

---

