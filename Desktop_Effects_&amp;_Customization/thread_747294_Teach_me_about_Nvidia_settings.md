---
title: "Teach me about Nvidia settings"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by employeeno5 on 2008-04-06
Hi there. I just got a new computer with a core 2 duo 2.4Ghz, 4GB ram and an NVIDIA GeForce 8400 GS.

I know very little about video cards. My previous computer had an ATI mobility radeon that was not nearly as nice as this card from what I understand but my compiz effects all ran beautifully 98% of the time.

Right now on faster computer with twice the RAM and a nicer video card, they run like garbage. Basic window animations are slow and choppy and jarring.

I'm assuming (perhaps incorrectly) that if I change my NVIDIA settings and/or my compiz settings correctly, I could solve allot of this. 

I have nividia-settings installed. I've been playing around with the settings but really I'm kind of just trial and error stabbing in the dark as I don't actually understand what these options may do and if compiz will respond to them. For all my tinkering, so far I've seen no increased performance for my effects.

I'm hoping that perhaps someone with the same or a similar card has found a happy place with these settings, or could help me understand what I should be looking for in them or what some things even really mean like:
What exactly is syncing to VBlank?
Will increasing anti-alaising help the choppiness or make it worse?
etc.

Perhaps I misunderstand the problem and the NVIDIA settings aren't going to help me?

Any input or further info about video card settings in general would be great.
Thanks!

---

### Post by FuturePilot on 2008-04-06
There's a slight bug in the Nvidia driver (if you want to call it that, it's more like a feature :-?) called powermizer. What this does is step your GPU in a similar way the the CPU is scaled. When under low loads the GPU will scale down to consume less power. The problem is it seems to govern the GPU very strictly which will result in slow choppy animations until the GPU scales up. Unfortunately there's no way to control powermizer. But the good news is they seemed to have improved the performance in the latest driver which is in Hardy.  I have the same card and the performance is much better in Hardy.

There is another tweak in CompizConfig that will improve performance slightly. Open CompizConfig and go to the General section and go to the Display Settings tab. Increase the Refresh Rate to 60 (it probably says 50 which is incorrect because it cannot detect the correct refresh rate with the Nvidia driver). Then uncheck the Detect Refresh Rate box.
Also check the box that says SyncToVblank. This will eliminate any tearing you see when moving windows around.

As for some of the other options in nvidia-settings. SnycToVblank will take more of the load off your CPU when running things that use OpenGL like Compiz, games, etc. I would recommend enabling SyncToVblank. There's two places for it in the nvidia-settings. There's one under Xserver Xvideo Settings and one under OpenGL Settings It will also improve video playback and eliminate tearing in Videos.

If you log out and login your setting won't automatically get set. So you need to make them load when you login. To do this go System&#8594;Preferences&#8594;Sessions and Add a new entry. Call it whatever you want. For the command type this in
```
nvidia-settings --load-config-only
```
you can also add a comment if you want. That will make the nvidia-settings load when you login.

---

### Post by employeeno5 on 2008-04-06
Thanks, for the response, that was very informative for me.

> If you log out and login your setting won't automatically get set. So you need to make them load when you login. To do this go System&#8594;Preferences&#8594;Sessions and Add a new entry. Call it whatever you want. For the command type this in
Code:

nvidia-settings --load-config-only



Haha, no wonder I wasn't seeing a difference. I had been logging out and reloggin in every time thinking that I might need to restart the x server to see the changes.  
I'm also using the Hardy beta with great success for the most part. 
I've got my refresh rate solid. I'll make a startup script for the settings and play around a bit more. I'll let you know if I have any success. 

Many thanks again for all the info about the gpu scaling and the Vblank.

---

### Post by FuturePilot on 2008-04-06
You're welcome! :)
If you have any more questions feel free to ask. :)

---

### Post by sdennie on 2008-04-07
You can't directly control PowerMizer but, you can actually force the card to run at full speed at all times.  I actually use two scripts that keeps bumping the card to maximum power while it's on AC but lets it drop down to lower power while on battery.  Something like this should do the trick:

99-nvidia.sh:

```

#!/bin/bash
# A companion script to nvidia-power.sh that removes/adds the lock that
# tells the script whether or not it should force the card into it's highest
# frequency every 25 seconds.  Think of it as sort of a poor mans powermizer
# manager.
#
# Also, see the two comments marked OPTION if you wish to save more power
# using OnDemandVBlankInterrupts and compiz.
#
# On Ubuntu install this script with the following commands:
#
# sudo install 99-nvidia.sh /etc/acpi/start.d
# sudo install 99-nvidia.sh /etc/acpi/resume.d
# sudo install 99-nvidia.sh /etc/acpi/ac.d
# sudo install 99-nvidia.sh /etc/acpi/battery.d
#

if on_ac_power; then
  touch /tmp/nv-power-on
else
  rm -f /tmp/nv-power-on
fi

for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"

        if on_ac_power; then
          # OPTION: Uncomment next line  to turn on compiz vsync when the 
          # laptop is plugged in
          su $user -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 1"
          su $user -c "nvidia-settings -q all > /dev/null"
        else
          # OPTION: Uncomment next line if you use compiz and have 
          # OnDemandVBlankInterrupts set to true in xorg.conf.  This will 
          # remove the ~60 wakeups a second that compiz causes the nvidia 
          # driver to do.
          su $user -c "gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank 0"
        fi
	fi
done

```

Then you can run a second script at login time that looks like this:

nvidia-power.sh:

```

#!/bin/bash

while true; do
    if [ -f /tmp/nv-power-on ]; then
        nice /usr/bin/nvidia-settings -q all > /dev/null
    fi
    sleep 25;
done

```

---

### Post by employeeno5 on 2008-04-09
Hey, that script works great. Thanks!

However, I do have one quirk. It continues to run even when I'm on battery on power. This isn't the first power dependent script I've had that issue with either. 

I definitely suffer badly from the much talked about problem of certain hard drives cycling themselves to death. I attempted to do the ugly fix [http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26) which involves writing a script that manually sets how often your hd head parks and unparks. That script too is supposed to vary depending on whether or not your on ac or battery power. However, it does not respond differently between the two states on my computer.

I know it's fairly off topic here, but given that both your script and the "ugly fix" for the hd problem behave similarly on my computer, in that they don't respond to the change between battery and ac and they install to the same directories, I'm wondering if you  anyone has any insight.

If not, not worries, that script works fantastically otherwise. I'm thrilled to use it.

---

### Post by sdennie on 2008-04-09
So, you're saying that /tmp/nv-power-on still exists even when you switch to battery power?  If so, it sounds like /usr/bin/on_ac_power can't figure out if AC is plugged in.  If you could post the output of the following commands both on and off AC power, there may be a workaround for you (barring a BIOS or kernel update which also may fix the problem):

```

cat /proc/acpi/ac_adapter/*/*

```

and

```

cat /proc/acpi/battery/*/*

```

---

