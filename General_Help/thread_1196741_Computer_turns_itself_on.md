---
title: "Computer turns itself on"
date: 2009-06-25
forum: General Help
---

### Post by zarqoon on 2009-06-25
I just recently updated from 8.04 to 9.04 and since then 3 times i discovered my computer switched on while i am reasonably sure it switched it off hours previously. I already checked the obvious bios settings but all the wake on settings are disabled.
I usually hibernate the system.
For the last occurrence i especially checked that the system was off before i got to bed. In the morning it was still off. But after i got home in the evening it was on again displaying grub.
Could it have anything to to with me having upgraded the system. It would seem to be a pretty big coincidence for it not to.

---

### Post by philcamlin on 2009-06-25
its impossible for the pc to turn itself on unless:

1. someone turns it on
2.power outage and you have it to wake on power restore
3. you have wake exabled on your pc 

do you have one of those power units that supply battery?

---

### Post by zarqoon on 2009-06-25
I thought that too. But
1. I live alone and i do not think anyone would break into my apartment turn my pc on but do nothing with it and leave. My mom has a key but i do not believe she would do something like that.
2. I already wrote that every wake on option is disabled
3. see 2.

my power supply is a 540w be quiet straight power. I am fairly sure it does not have a battery.

---

### Post by JKyleOKC on 2009-06-25
I had a similar situation with a WinXP machine that would turn itself back on instantly after I switched it off with the shutdown button, although all of the automatic-on features were turned off.

It turned out, after several weeks of troubleshooting, to be a setting in the BIOS that was doing it. Have you verified that your BIOS doesn't have an automatic-restore-after-power-failure setting that's still active? If it does, then this might be the cause. And since the BIOS settings are invisible unless you view them during the first stages of booting up, they are easy to overlook...

---

### Post by Therion on 2009-06-25
> **zarqoon said:**
> ... I live alone and i do not think anyone would break into my apartment turn my pc on but do nothing with it and leave.
Didn't you see my note?  I left a note...  Wow.  Akward.  Just needed to blast off a couple quick emails and, well, your PC was closer.

---

### Post by zarqoon on 2009-06-25
I've seen the wake after power loss setting in the bios but its set to disabled.

And you could not have sent any emails. The pc was waiting in grub for me to select what to boot. I've yet to see someone send emails using nothing but grub.

---

### Post by dcstar on 2009-06-26
> **philcamlin said:**
> its impossible for the pc to turn itself on unless:

1. someone turns it on
2.power outage and you have it to wake on power restore
3. you have wake exabled on your pc 


Wake on LAN is enabled and the right packet arrives.

---

### Post by zarqoon on 2009-06-27
Wake on lan is disabled.
It has not done it a whole day now.
Is it possible to create a boot entry in grub that powers the system down?
If I could set that as default my problem would be at least partially solved.

---

### Post by QIII on 2009-06-27
It misses you?

Careful jumping to conclusions about your recent upgrade.  Don't fall into the "Post hoc ergo propter hoc" fallacy.  Causality has to be considered.  It could be coincidental.

Sounds more hardware related to me.  Might be a failing power switch shorting ...

---

### Post by zarqoon on 2009-07-26
Over the last couple of weeks i made some observations.
If I hibernate the system it will switch on if I move the mouse or press a key. It only requires minimal mouse movement to do this. Bumping the table is usually enough. That could explain the Computer being on at odd Times.

If i do a Shut Down this does not happen.
If the System starts itself and i switch it off right away with the power button it does not happen anymore.
I checked multiple times Wake on Keyboard/Lan/whatever is disabled in Bios.

This has to be Software related somehow. 

I really would like to keep using Hibernate but having to be careful not to move the mouse and failing that powering the system on and then off again immediately is not an ideal solution. And its bad for the hard disks.
I just found an entry in the help for ending a session where it says a mouse movement is supposed to restart the computer from hibernation.
How do i shut that off?

---

### Post by Crunchy the Headcrab on 2009-07-26
Sometimes in Windows people have problems with their wireless mouse waking their system.  The solution in windows is to go into power settings and disable wake on usb (meaning that usb devices can't wake up the system).  Another solution is to unplug the usb device.  Infrared devices like remotes can also wake the system.  This is not an OS problem, but has more to do with the device sending unnecessary information.

---

### Post by zarqoon on 2009-07-26
I do not have any wireless devices etc.
I know it is my mouse thats booting the system up. 
I have windows installed but I did not boot that up in the last few months.
It has to be an ubuntu setting. The help on hibernate states
>  You can resume from hibernation by moving your mouse or pressing a key.
I want it not to do that. I can not find a setting to this effect anywhere.

---

### Post by dhughes on 2009-07-26
It was in Hibernate not off so that makes me wonder if you're having the rebooting issue several people have had, including myself, it only happens with 9.04

 I think all of us solved it by changing the power supply, I know it solved the mystery rebooting problem I was having with my system.

 If you don't have a problem with it rebooting randomly when you're using it then it's probably not the same problem.

[http://ubuntuforums.org/showthread.php?t=1178833](http://ubuntuforums.org/showthread.php?t=1178833)
[http://ubuntuforums.org/showthread.php?t=1112028](http://ubuntuforums.org/showthread.php?t=1112028)
[http://ubuntuforums.org/showthread.php?t=1090385](http://ubuntuforums.org/showthread.php?t=1090385)
[http://ubuntuforums.org/showthread.php?t=1193369](http://ubuntuforums.org/showthread.php?t=1193369)

> I know it is my mouse thats booting the system up. 

OK, didn't see that in time.

---

### Post by zarqoon on 2009-07-26
It is not randomly. It behaves exactly as is stated in the help file. But my mouse is kind of touchy and therefore i thought it was randomly because i did not know the mouse caused the power on. Now that I know and have been paying attention all powerups can be traced to accidental mouse movement.
The mouse did not wake the system from hibernate in 8.04 and i want to go back to that behavior

---

