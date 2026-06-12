---
title: "latitude touchpad losing sync"
date: 2006-02-21
forum: Desktop Environments
---

### Post by Payrok on 2006-02-21
Hi,

    I have a fairly fresh install of ubuntu on my laptop (specs at the end of post).  The problem I have been having started with a fresh install, what happens is, my touchpad stops working for a brief moment or two, and when it becomes active again, sometimes jumps to the other side of my screen.  Sometimes, however,  the cursor will move, but it seems that no click events are sent to the window manager. This was a minor annoyance at first but this is getting out of hand.  Thanks for the help in advance.

dmesg output and system specs:

Latitude CPx J650GT
256MB Ram
ATI M1 graphics w/ 8MB dedicated framebuffer
Synaptic Touchpad
Linksys pcmcia wireless card 802.11g

[4299574.566000] video bus notify
[4299639.463000] video bus notify
[4299662.347000] cpufreq: change failed with new_state 0 and result 0
[4299664.351000] cpufreq: change failed with new_state 1 and result 0
[4299671.499000] cpufreq: change failed with new_state 0 and result 0
[4299674.628000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost synchronization, throwing 4 bytes away.
[4299674.628000] cpufreq: change failed with new_state 1 and result 0
[4299674.634000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 1
[4299674.635000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 1
[4299674.643000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 - driver resynched.

---

### Post by chanski on 2006-08-06
I am seeing this exact problem with the same Dell CPx.  Does anyone have a resolution?

I see on another forum that somoeone suggests the touchpad is faulty, but the same latop had no problems when Mandriva was installed.

This makes ubuntu unusable for me:(

---

### Post by ccolella on 2007-04-30
I have the exact same problem with my Compaq laptop using a Synaptics touchpad and an ATI shared-memory graphics card. The mouse is jumpy, often disappears, then reappears on the other side of the screen, then isn't able to click on anything unless I repeatedly tap the left mouse key, then it seems to "wake up." As someone else has said, it's getting out of hand. The only thing is, it happen for me with every distribution of Linux I've ever tried. This doesn't happen in Windows, so I know it is a Linux problem. It's too bad, because it makes Linux totally unusable for me, and no one seems to have the same problem except you two gentlemen, so this makes me think it isn't my hardware. I certainly hope it isn't my hardware, because Ubuntu, Mandriva, Linux Mint, Sabanyon, etc. are completely unusable with this touchpad.

I hope someone out there has an answer.

---

### Post by jlavrador on 2007-06-14
Hello guys I have the same problem on my Toshiba Tecra S3, I am using Ubuntu with Kubuntu Desktop installed.

This is my dmesg:

[ 5363.280000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 5363.300000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 - driver resynched.
[ 5363.696000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 3
[ 5363.704000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 - driver resynched.
[ 5363.708000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 5363.708000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 5363.756000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 - driver resynched.

Best regards

---

### Post by Xeor on 2007-08-28
Same problem with Kubuntu Edgy and Acer Aspire 1362 Laptop;
My touchpad get freaky and jump all around every so and so. The rest of the time it's OK.

[  125.068000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  125.068000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  125.076000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  244.908000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  244.912000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  244.920000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  415.488000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  415.488000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  415.492000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  415.492000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  415.496000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  415.496000] psmouse.c: issuing reconnect request
[  417.620000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  417.620000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  417.628000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  417.712000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  417.716000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  417.724000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  484.632000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  484.636000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  484.644000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  514.588000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  514.588000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  514.592000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  514.592000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  514.596000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  514.596000] psmouse.c: issuing reconnect request
[  634.488000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  634.488000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  634.496000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  964.256000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  964.288000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 1234.100000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 1234.104000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1234.112000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.


But as it is to replace Windows on my brother's laptop, I would love it to be more than OK. The good thing is they having the same problem on Windows with this laptop.

---

### Post by n3tfury on 2007-10-19
> **Xeor said:**
> Same problem with Kubuntu Edgy and Acer Aspire 1362 Laptop;
My touchpad get freaky and jump all around every so and so. The rest of the time it's OK.

[  125.068000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  125.068000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  125.076000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  244.908000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  244.912000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  244.920000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  415.488000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  415.488000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  415.492000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  415.492000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  415.496000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  415.496000] psmouse.c: issuing reconnect request
[  417.620000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  417.620000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  417.628000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  417.712000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  417.716000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  417.724000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  484.632000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  484.636000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  484.644000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  514.588000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  514.588000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  514.592000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  514.592000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  514.596000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  514.596000] psmouse.c: issuing reconnect request
[  634.488000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  634.488000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[  634.496000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[  964.256000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[  964.288000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[ 1234.100000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
[ 1234.104000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[ 1234.112000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.


But as it is to replace Windows on my brother's laptop, I would love it to be more than OK. The good thing is they having the same problem on Windows with this laptop.

bump. same here on a Dell C600 and now on Gutsy.

---

### Post by mhenry676 on 2007-10-19
I too have had this problem on a Dell C810 (p3 1.13 GHz) 
I had it on Fiesty, and now Gutsy (using kubuntu). I have ran opensuse, and not had this problem, but do have a workaround, that kinda stinks for a laptop. Do note, psmouse was not a module running on opensuse. Also, this problem is worst with Gutsy than Fiesty..

First, here's what I tried and the results. I also had a usb mouse plugged in....

By default,
Power Manager CPU on AC Power set to Dynamic
psmouse driver loaded (touchpad does not work without)

Mouse skips constantly at times, dmesg (watch -n1 'dmesg | tail -n 55')

[  320.888000] Synaptics Touchpad, model: 1, fw: 5.7, id: 0x8146b1, caps: 0x804793/0x0
[  320.888000] serio: Synaptics pass-through port at isa0060/serio1/input0
[  320.932000] input: SynPS/2 Synaptics TouchPad as /class/input/input7
[  326.268000] IBM TrackPoint firmware: 0x0b, buttons: 2/3
[  326.496000] input: TPPS/2 IBM TrackPoint as /class/input/input8
[  375.292000] ondemand governor failed to load due to too long transition latency
[  376.784000] cpufreq: change failed with new_state 1 and result 0
[  378.280000] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
[  378.280000] cpufreq: change failed with new_state 1 and result 0
[  381.112000] cpufreq: change failed with new_state 1 and result 0
[  382.604000] cpufreq: change failed with new_state 1 and result 0
[  387.108000] cpufreq: change failed with new_state 1 and result 0
[  388.596000] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
[  388.596000] cpufreq: change failed with new_state 1 and result 0
[  389.772000] cpufreq: change failed with new_state 1 and result 0

This was with USB mouse and touchpad (just after loading psmouse manually and moving mouse around)


After setting CPU on AC Power to Performance, issue seems to go away.
unloading psmouse, with Dynamic?

same result, so only see this in dmesg

[  807.504000] cpufreq: change failed with new_state 1 and result 0
[  809.328000] cpufreq: change failed with new_state 1 and result 0
[  810.820000] cpufreq: change failed with new_state 1 and result 0
[  812.316000] cpufreq: change failed with new_state 1 and result 0
[  820.828000] cpufreq: change failed with new_state 1 and result 0
[  824.648000] cpufreq: change failed with new_state 1 and result 0
[  826.144000] cpufreq: change failed with new_state 1 and result 0
[  827.324000] cpufreq: change failed with new_state 1 and result 0
[  833.836000] cpufreq: change failed with new_state 1 and result 0

each time with a mouse skip

loaded kpowersave, defaulted to dynamic:

dmesg:
[  961.764000] ondemand governor failed to load due to too long transition latency
[  963.260000] cpufreq: change failed with new_state 1 and result 0

changed to Performance, again no issue


So, issue is with the cpufreq switching. Not practical when on battery, but ok on AC.

Will continue to investigate, cause opensuse 10.3 sucks, but kubuntu 7.10 rocks!

:guitar:

---

### Post by n3tfury on 2007-10-19
i found this a few hours ago and it worked for me.  take a look:

[http://www.shahidhussain.com/blog/?p=12](http://www.shahidhussain.com/blog/?p=12)

---

### Post by mhenry676 on 2007-10-23
okay....

I'm sorry, but that's a lot like cutting off an arm to take care of a paper cut.

It's will work; just need a little more digging, which I've got good results. Thanks to this post [http://ubuntuforums.org/archive/index.php/t-75598.html]("http://ubuntuforums.org/archive/index.php/t-75598.html")

I did this:
```

rmmod speetstep-smi
modprobe acpi-cpufreq

```

and switching works great! Mouse no skippy!

Now, I'm trying to figure out how to get it to be used by default. I've tried blacklisting speedstep-smi. I've tried modifing the /usr/share/powernowd/cpufreq-detect.sh to only have acpi-cpufreq as an option (replacing where I saw a speedstep driver) but still nothing. 

Can anyone help set it so I have the acpi-cpufreq driver only load?

---

### Post by n3tfury on 2007-10-25
*bump*

---

### Post by zzanzare on 2007-11-26
> **Xeor said:**
> Same problem with Kubuntu Edgy and Acer Aspire 1362 Laptop;
My touchpad get freaky and jump all around every so and so. The rest of the time it's OK.


I seem to have quite the same problem as Xeor. from time to time when i start my computer the mouse occasionally jumps and clicks (even right or middle clicks). when i restart, it is USUALLY ok. but i don't have any cpufreq errors in my log and also uninstalling powernowd doesn't help.

I have ALPS touchpad on Acer Aspire 5710 and ubuntu gutsy

---

### Post by zzanzare on 2007-12-11
hi all.. it seems i have found a sollution for my "mouse jump" problem. I don't think it has something common with your cpufreq errors, but at least it helped on my Acer Aspire 5710 with ALPS Glide point

after adding 
```
i8042.reset i8042.nomux
```
to my kernel options in /boot/grub/menu.lst i had no jump for 4 days already

hope it helps for you too, good luck

---

### Post by uuser57 on 2007-12-15
I have a Dell c600 in which the mouse seemingly randomly goes crazy; the pointer starts jumping all over the place and usually retreats to a corner.  Sometimes it stops after a while, but usually not.

I used evtest (in the lineakd package) to examine the events coming from both the touchpad and the trackpoint.  When I looked at the trackpoint events (evtest /dev/input/event4), the list kept scrolling noting a constant stream of relative position events.  The coordinates seemed to be correlated with the directions the pointer was moving.  My conclusion was that the trackpoint was the culprit.  I edited xorg.conf to change the "configured mouse" to only reference the touchpad (/dev/input/mouse1 instead of /dev/input/mice).  The pointer doesn't jump around anymore, but it's a bit sticky for the touchpad (i.e., moving a finger on the touchpad sometimes doesn't move the mouse the corresponding amount).  I'll try some of the other solutions noted in this thread and post back.

---

