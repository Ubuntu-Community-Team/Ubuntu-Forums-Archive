---
title: "Ubuntu 9.04 does not wake up from suspend (sleep) mode."
date: 2009-04-26
forum: General Help
---

### Post by wittmarf on 2009-04-26
Hello,

i had no problems with suspend-to-ram/wake-up with 8.10. It worked fine and I was happy. 

Now with the new 9.04, after going to suspend mode (power LED is blinking), when I push the power button to wake up the system, I only see a black screen with a blinking cursor. 

When I hit Alt-F2 I see a console login, but the screen does not react to keyboard input. All I can do is a reset.

My system is 9.04/64-bit on X58-board with Core i7 CPU and Nvidia gtx275 graphics card. As I said I had no problems with 8.10!

Any help appreciated!

---

### Post by renowiggum on 2009-04-26
Similar problem - I just installed 9.04 a couple days ago, and accidentally hit the sleep button.  Now the computer will not boot - the power LEDS light up, but I am unable to get into BIOS, and unable to get the computer to respond - the monitor remains in power-save mode, and there is no sound from the monitors.

---

### Post by Deamos on 2009-04-26
I am having the same issues with Jaunty.  Suspend drops to a single cursor blink.

Maybe it has something to do with Video Card.

I am using the Restricted Nvidia 180.00 Drivers

---

### Post by pldg on 2009-04-27
> **Deamos said:**
> I am having the same issues with Jaunty.  Suspend drops to a single cursor blink.

Maybe it has something to do with Video Card.

I am using the Restricted Nvidia 180.00 Drivers

I've had problems with waking up from suspend all the life of this machine, but last time I managed to find a piece of info to try and find out what was the cause. I've synthesized the procedure below:

[INDENT]remove /etc/init.d/[checkroot.sh | checkfs.sh]
echo 1 > /sys/power/pm_trace
echo mem > /sys/power/state -> suspend
[supposedly failed attempt -> hard reboot with power button]
-> date will be screwed, as well as filesystem checks
save dmesg somewhere
restore /etc/init.d/[checkroot.sh | checkfs.sh]

In the dmesg file saved before, look for:
[    1.500776]   Magic number: 4:256:725
[    1.500851] pci 0000:01:00.0: hash matches

compare trailing numbers with lspci output to know which device was
culprit (last to be attempted to suspend or resume)

In this case, the fault was due to...

01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
[/INDENT]

Yeah, last time it was the nvidia driver alright. In 8.10 I had frozen nvidia do 173 because of other problems, and a few days before 9.04 came out, the update manager offered me 180 again and I decided to give it a try. Previous problems seemed to be gone, but the machine wouldn't wake up anymore (blank screen with flashing cursor only, no disk activity).

Now I'm 2--3 days on 9.04 and already noticed the waking up problem (100% of the attempts). I'll either try newer versions (185) or get back to good old 173.

If you really want to be sure about the cause, do the procedure above. The procedure I found through googling didn't mention about removing the checkfs init script, which is essential. Ignore eventual msgs about filesystem problems; what is vital is to reboot and collect the dmesg info in a few minutes time (<5min) after the suspend event, or else the clock digits in the RTC will increase the counting and overwrite the needed info.

---

### Post by jensjk on 2009-04-28
I have the same problem on a HP Pavilion DV6000 laptop - worked fine with 8.04 and 8.10, but an update in acpi some time in january caused the problem - hoped it solved after installing 9.04, but the problem persists

---

### Post by lemonberry on 2009-05-12
Same problem here - 8.10 would sleep/wake fine.  Installed 9.04 a couple of weeks ago, and now will sleep OK, and when I hit the power button to wake up, I hear fans etc kick into action but nothing else happens.  I have to hold power button in for 5 secs to power off, then restart.

Any ideas/help appreciated.

---

### Post by reon on 2009-05-27
Same problem here. Blank screen after I wake it up. Fresh install Ubuntu 9.04 (amd x64). I have a toshiba laptop with an ATI HD3650 if that matters. Big fan of the sleep feature I need this XD

---

### Post by ibokozan on 2009-05-27
so how to solve this. i have the same error.

---

### Post by tractor on 2009-05-27
I'm having the same problem with 9.04 on an HP with a 4800 Athlon X2 processor and ATI graphics. I left it go to sleep while out on an appointment today. I came back and the computer was dead. No blinkiing power light or anything. It had completely powered off and was locked. Hitting the power button to boot it did nothing. The only way to get it to start again was to totally disconnect the power for about 30 seconds, and then do a complete new boot. My son is running 9.04 on his laptop. It was strange, but he had the identical thing happen to his today. He had to unplug it plus remove the battery to be able to restart it.

---

### Post by ragnarokz on 2009-05-30
I have a similar problem with my recently bought and installed generic laptop.

Close the lid, and if i leave it closed for to long, WHAM, won't reactivate, doesn't matter if I set the Power Savings to blank screen, hibernate or suspend, same result every time. 

If I open it fast, it doesn't. This is unfortunately a rather critical issue, as it lowers battery time quite a bit, having to set the monitor permanently on.

---

### Post by naifnezar on 2009-06-29
Hi,
I am currently having the same problem as all of you guys. I am using Compaq CQ40. If anybody did solve the issue, kindly reply. Really need the feedback.

---

### Post by dave_i on 2009-06-30
I too am having this problem - I've noticed that it only occurs when I have my wireless G USB adapter plugged in. Anyone else got any USB devices plugged in when this is happening? Can anyone tell me where I should look for a logfile to investigate this? I'm using an Aopen system with a 1.7Ghz Pentium M.

---

### Post by rbolio on 2009-07-03
Bump on this! ..... My cousin has the same problem.....

---

### Post by Chronon on 2009-07-03
Sorry.  I can't help.  Suspend works properly for me with or without USB devices connected.  I have found an oddity, though.  Wake up from Suspend is accomplished by pressing Fn button by itself -- not "Fn + F1".  If I press the expected combo then it wakes and goes back into suspend again.  

I have a Eee PC 1000 HEB if it matters at all.

---

### Post by MZBKA on 2009-07-09
Bump.  I have the same problem.

---

### Post by AClark on 2009-07-09
I suspect that not all the problems reported in this thread are caused by the same problem - but it sounds like some may be related to problems with various WiFi drivers and suspend.

This problem causes many weird and seemingly unrelated symptoms so don't assume it couldn't be WiFi because the problem seems to be with USB or Audio etc.

The SUSPEND_MODULES solution described in the 2 following posts is worth a try - it's easy to implement and won't cause more problems even if it doesn't work.

[http://ubuntuforums.org/showthread.php?t=1190881](http://ubuntuforums.org/showthread.php?t=1190881)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274780](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274780)

Good Luck

---

### Post by spinetree on 2009-07-13
Same problem with Dell Optiplex GX270. 

There is no wireless adapter, so this supports the theories that it's a usb or audio-related issue.

How do either of the above fixes work if nobody's able to boot into even a terminal? Are people booting from a liveCD?

---

### Post by seb.el on 2009-07-17
Same problem:
- Sleep mode from power-management as well as from keyboard sleep button.
- Fans are constantly running, as well in sleep.
- No reaction when pressing mouse, keyboard or power buttons.
- Displays are staying in Sleep-Mode.
- Reset needed.

System used: 
- Ubuntu 9.03
- Intel Motherboard with Core 2 Duo 2.8 Gzh
- MSI Graphic Card with nVidia GeForce 512MB DDR2, PCI Express
- D-Link USB WiFi G 
- inbuilt Audio

Troubleshooting from tips of this thread:
- Unplugged USB devices (it's only a USB WiFi), same issue.
- Restarted without USB, same issue.

- Uninstalled PCI Express Graphic Card.
- Rebooted with standard Graphics, same issue.


Well, I don't think it's the USB, nor the Graphic Card which are listed quite an amount of the above mentioned issues. Please correct me.
My workaround is: I set only the displays into sleep-mode. Well, it's a desktop, quite different for a notebook with battery usage.

Is it just beginner's having that issue?
Hope that my info helps.

---

### Post by seb.el on 2009-07-17
> **seb.el said:**
> 
System used: 
- Ubuntu 9.03

Sorry:
- Ununtu 9.04, released April 2009

---

### Post by vkaggal on 2009-07-17
I use Presario R3000 with fresh install(about 2 weeks old) of Ubuntu 9.04 and suspend and hibernate was not working for  me.

I just fixed it with help from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229806/comments/16](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229806/comments/16)

Hope this helps!

---

### Post by sossij on 2009-07-27
Hi all,

Just installed 9.04 at the weekend and all is well except I too have problems with suspend / hibernte (both used to work fine in SuSE 11).

I'm running 9.04 on a Packard Bell laptop, model Argo C.

I had no luck with the fix detailed here: [http://ubuntuforums.org/showthread.php?t=1211292](http://ubuntuforums.org/showthread.php?t=1211292)

Is there a canonical fix for this yet/anywhere?

Thanks.

---

### Post by AClark on 2009-07-27
Are you using WiFi ?

If so do you know which driver your WiFi adapter is using ?

```
lshw -C network
```

Have you tried the SUSPEND_MODULES solution described here ?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274780](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274780)

I remember seeing at least one post where the same problem was caused by an ethernet card driver but I don't remember where.

None of the various scripts that are floating around worked for me but creating the file with the SUSPEND_MODULES=(drivername) statement solved it for me on three different Jaunty installs all with different drivers.

---

### Post by ericwait on 2009-07-28
I am happy to say that the 9.10 Alpha release has fixed this problem on my HP dv6000! The only problem I see so far is that the taping doesn't work on my touch pad, but I am sure that will be worked out soon enough.

Good work Ubuntu Developers.  It seems like the boot up speed will make hibernation a thing of the passed!

---

### Post by lubimaer on 2009-09-08
In my case I solved the wake up from sleep/hibernate problem disabling compiz
Works both in GNOME and KDE 4
No special effects :( but correct resume from sleep

---

### Post by HolyShnikes on 2009-09-16
I am having a similar problem with my dv6000.  I put it to sleep last night and when I tried to boot it back up, all the lights came on, but no monitor display.

Any fix for this besides trying the alpha?

---

### Post by pablolie on 2009-09-17
doesn't look like there is a solution?

i just saw the same thing with my system, no wifi, but indeed an Nvidia card. 

i wonder why it's called "suspend" in the shut down menu off the panel, but "sleep" in power settings? consistent terminology in the user interface, anyone? :-)

anyhow, i will try to play around with BIOS settings to see if it's video card related, i think there's the S3 setting or something like that for video behavior after sleep.

---

### Post by wgillett on 2009-10-24
Thanks but didn't work for me. Neither did the fix described here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229806/comments/16](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229806/comments/16) .
which someone mentioned in another post. I'm using Ubuntu 9.04 on a Compaq 8710p laptop.
Hoping this issue can be bumped up, having a laptop that can't suspend/resume or hibernate/resume is a problem.

---

### Post by ignisuti on 2009-11-11
Bump... I'm using 9.10 and have the same issue.

---

### Post by Andy H. on 2009-11-11
I have the same issue w/ 9.10 on a HP Pavilion ze5400 laptop.

---

### Post by Andy H. on 2009-11-12
Bump

---

### Post by Sin@Sin-Sacrifice on 2009-11-20
Yeah... bump... this is an issue. 9.10 XFX 750a and ndiswrapper w/bcmwl5. A bunch of stuff in USBs including lirc receiver, saitek controller, speakers and a usb drive. I don't think those are the problems. And to be more specific I get the black screen with a blinking cursor.

---

### Post by kresh on 2009-12-07
Still no fix?  This is becoming a deal breaker.

edit:  That sounded bad, like somebody owed me something.  I meant a deal breaker for this particular machine.

---

### Post by seenthelite on 2009-12-15
> **HolyShnikes said:**
> I am having a similar problem with my dv6000.  I put it to sleep last night and when I tried to boot it back up, all the lights came on, but no monitor display.

Any fix for this besides trying the alpha?

Same problem on new Toshiba P500-01U004 with 9.04, tried 9.10 no wired or wireless network.

---

### Post by gm__ on 2009-12-27
Same here.

Maybe we should try other display drivers?

---

### Post by stangbat on 2010-01-11
vkaggal's fix in post #20 worked for me.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229806/comments/16](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229806/comments/16)

This is on a desktop machine, 9.10 with 2.6.31-17-generic, AGP GeForce 6600 GT, NVIDIA 185.18.36 drivers.

After resuming from suspend, the login prompt appears.  After logging in I'm at the desktop.

Edit:  Just resumed without having to login.  Either way, it now works.

---

### Post by soryu on 2010-01-31
same problem here not waking up from suspend or hibernate.
both work if i disable compiz.](*,)


is it necessary to blacklist intel agp?

---

### Post by Lepy on 2010-02-06
I am having a similar problem in Mythbuntu 9.10. Suspend (using pm-suspend) seems to work fine, as the computer and monitor completely power down with only the power remaining light blinking. 

However, upon resuming (using the power button...cat /proc/acpi/wakeup lists all devices as S-state 4), I get only a blinking cursor in the upper left of the screen which is remedied by a reset.

I have an AsRock K10N78 that connects to a lcd tv using the onboard nvidia 8200 (195.50) over a dvi to hdmi cable. 

To my xorg.conf, I have tried adding
 ```
Option         "NvAGP" "1"
```
as well as 
```
Section "Extensions"
Option "Composite" "Disable"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection
```

along with these added to /etc/modprobe.d/blacklist
```
blacklist intel_agp
blacklist agpgart
blacklist amd64_agp
```

and tried various modifications of /etc/defaults/acpi-support. 
No success at all!

---

### Post by jojodrum3 on 2010-02-06
I've been having this exact problem and the only thing that appears to have solved it is removing the third party video drivers in system>Administration>hardware drivers. I've got an Nvidia Gforce Go 6150 card in my laptop.

I have no idea what drivers are being used but I've been able to hibernate and suspend and successfully wake the computer back up 3 times each.

---

### Post by Ralph O on 2010-05-23
In case it's of any help to anyone, I fixed this in 10.04 by commenting a line out of "/etc/default/acpi-support"

```
...
# Should we attempt to warm-boot the video hardware on resume?
# POST_VIDEO=true
...
```

---

### Post by Ralph O on 2010-05-23
Okay, slightly premature with that last post. The above seems to make it wake up more often, but not every time.

---

### Post by X5-655 on 2010-08-24
This bug still exists in 10.04 with Compaq CQ61-313us..

---

