---
title: "Ubuntu on Dell M2010"
date: 2007-07-04
forum: Dell  Ubuntu Support
---

### Post by dfernandez on 2007-07-04
I folks, i recently buy a Dell M2010 and I want to install it Ubuntu last release (7.04), but i think there is some incompatibility issues with the hardware...Video (XServer dont start) and bluethoot keyborad not respond...

Help neeed please...I need to migrate my old Windows Vista Ultimate to Ubuntu ;-)

Regards,
Damian

---

### Post by sj3fk3 on 2007-07-04
> **dfernandez said:**
> I folks, i recently buy a Dell M2010 and I want to install it Ubuntu last release (7.04), but i think there is some incompatibility issues with the hardware...Video (XServer dont start) and bluethoot keyborad not respond...

Help neeed please...I need to migrate my old Windows Vista Ultimate to Ubuntu ;-)

Regards,
Damian
Bluetooth: [http://ubuntuforums.org/showthread.php?t=227057](http://ubuntuforums.org/showthread.php?t=227057)
for x try sudo dpkg-reconfigure xserver-org

---

### Post by metalheart on 2007-07-04
Problem with X may be the same as described in [http://ubuntuforums.org/showthread.php?p=2516175](http://ubuntuforums.org/showthread.php?p=2516175)

---

### Post by originalsurfmex on 2007-12-12
ive installed ubuntu and kubuntu and gOS - a combined total of 8 times on my xps m2010...and haven't had any bluetooth problems yet. (i installed and reinstalled because i kept breaking alsa in my attempts to get sound coming out of the speakers, only headphones work)

...maybe a reinstall is in order if nothing else works.

---

### Post by zeddock on 2008-01-07
you did this on Gusty or Feisty, or what?

Which version did you install of Ubuntu onto your 2010?

zeddock

---

### Post by rebski on 2008-01-11
I have installed Ubuntu 7.10 as a dual Vista boot.

Overall the experience is very good. With support for the Hardware including:-
Bluetooth Keyboard and Touchpad
Screen Resolution 1680 x 1050
ATI Radeon 1800 Mobility drivers – But not those required for special graphics effects
Sound via headphone socket
USB speakers support
USB support
Intel WiFi
CD/DVD Drive 

Two issues
No Sound from system speakers
Extreme overheating from CPU and Graphics card.

The last is particularly annoying. One of the many joys of the M2010 is the silent running, fan noise is a rarity. However as soon as I boot into Ubuntu with no applications loaded apart from WiFi connection, the fans kick in at full bore. The heat from the top LH and RH panels is intense.

I have installed a cpu activity status applet (cpufreq?)  which shows the CPU usage alternating between 50% and 100%. Never less than 50% and never anything in between 50% and 100%. 

By contrast, on Vista CPU usage is between 4% and 10% in similar circumstances

This is a serious Ubuntu problem and one which had been unresolved for about 2 years. When I exit Ubuntu and reboot into Vista, almost immediately the cpu and graphics cool down, the fans stop and my system is silent again.

I have read that other Linux distros do not have this bug. My next task is to track one down. This is a shame as I really like Ubuntu but I would sooner stick with Vista than have a noisy overheating computer.

The good news is that Linux on the M2010 is a reality.

---

### Post by zeddock on 2008-01-12
Wow. Thanx for the info.

I love Ubuntu.  But I just can't see how this is "very good".  It sounds like Ubuntu is killing your expensive laptop!

Thank you for the information. Please!  Get back to us as you find solutions.  

I have to order a laptop in a few days and hope you have success before I have to go another route.

Thanx again!

zeddock

---

### Post by rebski on 2008-01-12
By tweaking a few settings in gconf-editor/gnome-power-manager/cpufreq
I have managed to eliminate the heat from the cpu.

I am on the trail now for corresponding tweaks for the graphics card.

Once I have finished I am happy to post the settings. 

In the meantime, I should be appreciative if anyone can help to point me in the right direction.

---

### Post by Linux/MAC-Fan on 2008-02-04
I have a Dell M2010 as well and i have tried the newest version of Ubuntu Gusty on it and i didnt seem to have overheating,bluetooth, or video problems. But has anyone else had extreme jumps in computer useage? and i really dont want to have any problems with my spendy laptop so any help would be greatly appreciated

---

### Post by faulkes on 2008-02-05
> **rebski said:**
> 
The last is particularly annoying. One of the many joys of the M2010 is the silent running, fan noise is a rarity. However as soon as I boot into Ubuntu with no applications loaded apart from WiFi connection, the fans kick in at full bore. The heat from the top LH and RH panels is intense.

I have installed a cpu activity status applet (cpufreq?)  which shows the CPU usage alternating between 50% and 100%. Never less than 50% and never anything in between 50% and 100%. 

By contrast, on Vista CPU usage is between 4% and 10% in similar circumstances


cpufreq is the frequency at which the cpu is operating, which can be displayed as a percentage (so if it says %50, it means your 2.8ghz cpu is currently running at 1.4ghz to save energy).  The value can be changed by right clicking the applet and selecting "Preferences" to display the actual MHZ.

cpufreq does equate to cpu utilization.

Faulkes

---

### Post by rebski on 2008-02-07
Thank you for the explanation, that makes sense and I had obviously misunderstood the function of cpufreq. As you point out, I had confused it with cpu utilisation and I am glad to be corrected.

It also explains why my cpu overheating issue was dealt with, presumably my cpu running at 1.0ghz will be under less stress and so run cooler that if it were running at 2.0ghz?

Irrespective, this overheating of my cpu and gpu does not occur under XP or Vista so I have to assume that it is early days yet in development of these Linux drivers. 

But then, from previous posts, this overheating may not be a consistent experience with other users.

---

### Post by faulkes on 2008-02-07
> **rebski said:**
> Thank you for the explanation, that makes sense and I had obviously misunderstood the function of cpufreq. As you point out, I had confused it with cpu utilisation and I am glad to be corrected.


No problem.

> 
It also explains why my cpu overheating issue was dealt with, presumably my cpu running at 1.0ghz will be under less stress and so run cooler that if it were running at 2.0ghz?


correct.

> 
Irrespective, this overheating of my cpu and gpu does not occur under XP or Vista so I have to assume that it is early days yet in development of these Linux drivers. 

But then, from previous posts, this overheating may not be a consistent experience with other users.

There are several things you may wish to investigate, I know that some dells
(my 600m for instance) have fan issues or rather fan control isn't always working properly.  I had to install gkrellm + i8k modules to get the second fan to turn on.  That would also help you determine if it's a cpu or other internal tempurature issue.

I would investigate further, it's likely that one of the cooling methods isn't working as intended, which is why you're seeing a greater heat signature than in windows (just a stab in the dark though).

Faulkes

---

### Post by rebski on 2008-02-08
Thanks for the further information and suggestions. I have read reports of fans sometimes not being switched on and so giving rise to overheating but this is not the issue in my case.

Within a minute or so of starting Ubuntu (or any other Linux distro) the fans kick in at full throttle and the panel over the graphics card gets extremely hot to the touch. That pitch of noise and heat remains constant for as long as the Linux Os is running.  Bear in mind that my use of Linux at the moment (for these very reasons) is simply observational and very brief and the only app that might get some use would be Firefox.

Then, when I exit Ubuntu and boot straightaway into Vista, the temperature cools down and the fans stop completely even before Vista has finished loading. No matter how long Vista is on, and no matter how many apps are running, the temperature remains cool and fan activity is non-existent.

There is no doubt in my mind that the issue lies with inefficient Linux drivers. This is borne out if I accept the default video card drivers, and corresponding low display resolution, then the system runs cool as normal. 

It is only when I install the Envy or ATI drivers required to enable the optimum screen resolution that the overheating problems occur. Maybe the next ATI catalyst release will solve this, I hope so. Because until it does there is no way that I can adopt Linux as a viable operating system on my M2010.

---

