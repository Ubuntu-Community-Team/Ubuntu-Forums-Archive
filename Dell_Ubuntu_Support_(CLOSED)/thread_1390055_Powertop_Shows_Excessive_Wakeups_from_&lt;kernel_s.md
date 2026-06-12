---
title: "Powertop Shows Excessive Wakeups from &lt;kernel scheduler&gt; and &lt;kernel IPI&gt;"
date: 2010-01-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Braytonio on 2010-01-25
FROM: Linux macunaimachine2 2.6.32-11-generic #15-Ubuntu SMP Tue Jan 19 18:16:27 UTC 2010 i686 GNU/Linux.

This is a Dell Latitude D620 with a GenuineIntel T2500 (Core 2) processor @2.0GHz.

I am experiencing huge numbers of wakeups per second, mainly attributable to:


[LIST=1]
[*][kernel scheduler] Load balancing tick
[*][Rescheduling interrupts] <kernel IPI>
[/LIST]

[IMG]http://boizebueditorial.files.wordpress.com/2010/01/fsckedupwakeups.png[/IMG]

A moment later, the thermal event interrupts went to >500 per second. 

I need help interpreting this reading and troubleshooting the cause. 

From my googling on the issue, I understand vaguely that the following result from dmesg might indicate a load-balancing malfunction.

```
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using HPET reference calibration
[    0.397997] checking TSC synchronization [CPU#0 -> CPU#1]:
[    0.400001] Measured 4342119672 cycles TSC warp between CPUs, turning off TSC clock.
[    0.400001] Marking TSC unstable due to check_tsc_sync_source failed
```The discussion of this issue is too technical for me to make much practical sense of, however. Can anyone clarify, in layman's terms?

I am running the kernel with boot parameter "pnpacpi=off" at the moment -- in a bid to fix a chronic problem with CPU frequency scaling -- but the problem recurs without that parameter, and with SpeedStep in (Dell's miminalist) BIOS (v. A10) disabled as well.

I am an Ubuntu user on this same hardware since Artsy Aardvark and have never experienced either of these two problems -- (1) excessive wakeups, possibly due to cpu scheduling, and (2) chronic frequency scaling failures -- before.

With Jaunty, I believe it was, driver modules were removed and the drivers compiled into the kernel, with a routine called loadcpufreq controlling which driver was loaded -- acpi-cpufreq by default. 

Using Live CDs of various other distros, I have neither of these problems: my CPU is identified properly, the proper driver module (speedstep-smi, I believe it is) is loaded, and power management works flawlessly. 

Thermal sensors work reliably, as I am not sure they are doing now. Performance and reliability are a degree of magnitude better. So why am I sticking with Ubuntu?

Anyone with similar problems? I find few references by googling the issue. I would appreciate any insights and would be happy to post debugging info. One result that troubles me is lscpu and cat /proc/cpu, which seem to indicate my CPU is not being identified properly. The output shows two logical processors @1.0GHz apiece. When frequency scaling is working properly, it shows two logical processors @2.0Ghz apiece:```


processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 14
model name    : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping    : 8
cpu MHz        : 2000.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm
bogomips    : 3994.65
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 14
model name    : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping    : 8
cpu MHz        : 2000.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm
bogomips    : 3993.41
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:
```The power management line is blank. Why?

Thanks in advance to hardcore Ubuntuans for your kind attention to this issue.

---

### Post by qwerty017 on 2010-01-25
I am seeing the same thing after the latest update. I am using Lucid if that changes anything but I doubt it does. he only reason I noticed anything amiss was that my CPU was pegged at 100% and running at 1.86ghz without ever stepping down. I found a workaround that at least works on my system if you want to give it a try. Wait about 2 minutes after startup without running anything. Just let the startup programs start and run. After the 2 minutes I click:
Menu
Shut Down...
Restart
A window then pops up stating an unknown program is not responding at which point I hit cancel and CPU and Load Balancing Tick drops to almost 0. I can't tell what the "Unknown Program" is but it looks like whatever it is, it might be causing the problem.

---

### Post by davidb_ on 2010-03-01
Braytonio, I am experincing the same issues as you have described. The number of wakeups does seem excessive.

One thing to note, the failure due to "TSC clock warp" that you mentioned is not the problem. The TSC is the Time Stamp Counter. Because your Core2 supports sleep states (C1, C2, C3), the TSC won't be synchronized between the cores. (Basically one core could be sleeping while the other is active, so TSC synchronization is pointless). At the very least, that's my understanding.

Did disabling plug and play acpi do anything for you with respect to wakeups?

---

### Post by finite9 on 2010-04-28
just a me too message.  Im getting the same behaviour on a Thinkpad Edge 13" with Lucid RC and daily updates.

Ive just got this laptop so I dont know if its Lucid or the hardware.  Never had an issue wqith this on my HP laptop though with any previous version of Ubuntu down to 6.06 (or whenever Powertop first made it into the repos).  Anyone posted a bug report?

Here is the [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/552020") on Launchpad

---

### Post by qwerty017 on 2010-04-28
I finally found the problem to be Blackbox that had been installed when I tried to use Lubuntu. After I uninstalled blackbox it's working perfectly fine.

---

### Post by mihai.ile on 2010-05-05
have the same problem, no blackbox installed so I don't know any workaround for this....

Oh it's on a Dell xps m1330 with intel t8300 cpu.

---

### Post by hlxshady on 2010-05-06
Hi all,

Same here, I just upgraded to 10.04 last weekend, and it is definitely showing its hunger for battery power ...

In WinXP, I can watch a movie using P2P streaming service for more than 2 hours nearly 3 hours on battery.

And in Ubuntu 9.10, documentation works including internet could last more than 3 hours as well.

But having upgraded to 10.04, my laptop can barely last for 2 hours, and I wasn't doing any resource demanding work, but browsing some website without flash(in fact, the system was almost in an idle status).

Through the sensors-applet, when system is idle, I can see both cores of my CPU have a temperature roughly 6 ~7 celsius higher than 9.10 (it is getting warmer recently ... I mean the weather).

About my laptop environment, I actually don't use any power saving software, either in Windows XP or Ubuntu.

Even a comparison within Ubuntu, I never used any power saving software in 9.10 too.
To make the battery run longer, I just switched off the bluetooth at boot (disable it in /etc/rc.local). And I seldom use the CD driver either.
That is all what I did to save power.

In 9.10, without using flgrx driver for my ATI video card, I couldn't turn on the 3D desktop effect. However, this third party driver caused a significant use of CPU when there is any graphical operations (such as multi-media and flash).
But my T400 could still run for 3 hours for documentation or programming work.

In 10.04, I was surprised that I don't even need to use flgrx and the desktop effect runs smoothly, without much use of CPU either!
Therefore I expected an even longer time that my T400 can run on battery. But the fact is, it is even shorter, even I was just using pidgin(should be a piece of cake for CPU).

Comparing between ubuntu and Windows is not my point here.
The reason I mentioned Windows was to prove that my battery is completely healthy.
I actually am trying to compare the battery performance of 9.10 and 10.04.



I just tried powertop in 10.04, and the output is as followed:

```

Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (10.7%)       Turbo Mode     0.1%
polling           1.0ms ( 0.0%)         2.27 Ghz     0.1%
C1 mwait          0.0ms ( 0.0%)         1.60 Ghz     0.0%
C2 mwait          0.3ms ( 3.6%)          800 Mhz    99.8%
C6 mwait          1.0ms (85.7%)

Wakeups-from-idle per second : 979.4    interval: 10.0s
Power usage (ACPI estimate): 25.6W (0.2 hours) (long term: 26.5W,/0.1h)

Top causes for wakeups:
  42.6% (454.7)   PS/2 keyboard/mouse/touchpad interrupt
  16.1% (172.0)   [kernel scheduler] Load balancing tick
  15.6% (166.3)   firefox-bin
  14.6% (155.4)   [extra timer interrupt]
   0.0% (  0.1)D  upowerd
   2.5% ( 26.2)   [iwlagn] <interrupt>
   2.1% ( 22.8)   [ata_piix] <interrupt>
   1.4% ( 15.2)   Xorg
   0.9% ( 10.0)   nautilus
   0.9% ( 10.0)   [kernel core] r600_audio_update_hdmi (r600_audio_update_hdmi)
   0.5% (  5.0)   [Rescheduling interrupts] <kernel IPI>
   0.5% (  5.0)   syndaemon
   0.4% (  4.7)   [acpi] <interrupt>


```

The wake up per second is horrific !!!

Well, I don't have any data for my laptop in 9.10 though ...


Any thoughts ?

---

### Post by finite9 on 2010-05-07
This is a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281)

And it is probably kernel related so until we get a newer kernel version that includes the fix we're going to have to live with it.

That is why you don't see the same issue on 9.10: different kernel.

---

### Post by isbiyanto on 2010-05-14
:( oh... no. my laptop battery life is about 1 hour 15 minutes

---

### Post by GeorgeOfTheBush on 2010-06-19
Any fixes yet to this problem??

---

### Post by mikewhatever on 2010-06-19
Look at the screenshot in post #1. The blue line says '14 wakeups per second'. That's not a problem for a 2GHz cpu, and is by no means excessive.

---

### Post by WindPower on 2010-06-19
@GeorgeOfTheBush: If you really want to, someone on the bug report posted a link to his PPA:
[https://launchpad.net/~brian-rogers/+archive/power](https://launchpad.net/~brian-rogers/+archive/power)
which includes the kernel with the fix applied. I haven't tried it though, as I don't need to go powerless for the coming months. But this bug does shave off about 25% of my battery life. Whatever mikewhatever says, it's still a huge power drain.

---

### Post by mikewhatever on 2010-06-19
> **WindPower said:**
> @GeorgeOfTheBush: If you really want to, someone on the bug report posted a link to his PPA:
[https://launchpad.net/~brian-rogers/+archive/power](https://launchpad.net/~brian-rogers/+archive/power)
which includes the kernel with the fix applied. I haven't tried it though, as I don't need to go powerless for the coming months. But this bug does shave off about 25% of my battery life. Whatever mikewhatever says, it's still a huge power drain.

I don't know if you can go much lower then 14 wakeups per second. In case that rate of wakeups is too high, consider suspending or turning the computer off.

---

### Post by saidmontiel on 2010-06-20
For those who get 2 hours... nice...
for that guy with one hour... decent...

I get 35 minutes.... ! my battery is old, but with xp i get and hour and a half, with 7 about 2 hours...

I think this is a major problem, and not only for laptop users.

I hope theres a fix SOON.

---

### Post by _the_mars_ on 2010-06-23
I had many (approx. 200) wakeups with the message "[Rescheduling interrupts] <kernel IPI>" with my 3 core AMD Phenom II running Lucid.
After closing all my screenlets it dropped to 20.

However while posting this comment I get 700 wakeups/sec from the "kernel IPI" using Chrome (badly optimized). But switching to the tab with Google (no animated icons anymore) it drops to 20 again.

Just to illustrated what (bad) apps can do...

---

### Post by NightwishFan on 2010-07-06
I have this (issue?) so I am going to add my 2 cents to the bug report, as well as some extra mainline kernel testing.

---

### Post by dante.jones on 2010-07-28
Greetings,

I've also noticed this problem with 10.04 on a Thinkpad T42

> $ cat /proc/cpuinfo gives:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.70GHz
stepping        : 6
cpu MHz         : 600.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2
bogomips        : 1199.20
clflush size    : 64
cache_alignment : 64
address sizes   : 32 bits physical, 32 bits virtual
power management:
```

Again, nothing against "power management:" - Why?

The kernel is a stock 2.6.32-24-generic.

Power top shows:

```
     PowerTOP version 1.12      (C) 2007 Intel Corporation


Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        ( 2.3%)         1.71 Ghz     0.8%
C0                0.0ms ( 0.0%)         1400 Mhz     0.6%
C1 halt           0.0ms ( 0.0%)         1200 Mhz     0.4%
C2               11.7ms (97.7%)         1000 Mhz     0.0%
C3                0.0ms ( 0.0%)          600 Mhz    98.2%

Wakeups-from-idle per second : 83.1     interval: 15.0s                 
no ACPI power usage estimate available

Top causes for wakeups:
  21.1% ( 16.1)   [kernel scheduler] Load balancing tick
  19.8% ( 15.1)   [ata_piix] <interrupt>
  13.6% ( 10.4)   [uhci_hcd:usb4, ipw2200] <interrupt>
   6.8% (  5.2)   [kernel core] hrtimer_start (tick_sched_timer)
   6.5% (  5.0)   syndaemon
   5.2% (  4.0)   [kernel core] usb_hcd_poll_rh_status (rh_timer_func)
```

I realise there's an open bug for this. Considering the excessive heat and battery power consumption this is causing - *a real issue for laptop users*, a prompt fix would be appropriate.

---

### Post by olivier-np30 on 2010-07-30
Hello,

I confirm : same issue on acer 5738Z laptop with kernel 2.6.32-24-generic-pae.

:(

---

### Post by ahmetalpbalkan on 2010-08-28
Confirmed. This problem also exists on Toshiba A300-15g laptop with 3.0 GB ram.

I have had a clean installation FROM: 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

---

### Post by Vadi on 2010-09-15
Supposedly a fix is available in this PPA: ppa:brian-rogers/power

It has two versions of a kernel, installing either should help alleviate the problem somewhat. Giving it a try... (there are 6 packages, so you have to install 3 for either)

---

### Post by dfszb on 2010-11-20
This seems to be fixed in the 2.6.36 kernel. It's available from the mainline repository, or you can build a kernel for yourself. Probably it will be included with the next ubuntu release. (11.04)

---

### Post by trolleybus on 2010-12-29
I have this issue with 2.6.35. [kernel scheduler] Load balancing tick wakeup is around 100 per second. Tried 2.6.36 mainline kernel and got this number around 10. But still seems this is not a big problem. When idling (Pidgin and Conky running in background) the Powertop shows power consumption arond 11,5 watts with 2.6.35 but 13,5 watts with 2.6.36. So I stick with 35.

---

### Post by BoxxIT on 2011-01-17
**Ubuntu never sleeps**  :shock:

I have the same problem with Ubuntu Server 10.10 (64). I'm using it for a home server running on Intel Atom 330 CPU. I have just installed the LAMP packages and updated all packages. No web page or anything running yet. 


My top wakeups are :

1 .  [kernel scheduler] Load balancing tick
2 . mysqld 
3. [kernel core] hrtimer_start (tick_sched_timer)
4. apache2
5. [kernel core] "different things"
6. kslowd00x  (x=0 or 1)
7. flush.... "something"

Kernel : 2.6.36-24-server

---

### Post by kotek on 2011-01-23
Same problem (300 wake-ups per second due to that reason) in Asus EEE PC 901.

The kernel 2.6.36 definitely solves the problem. No need to compile, the .deb packages can be obtained as shown here:
[http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/]("http://www.ramoonus.nl/2010/10/linux-kernel-2-6-36-installation-guide-ubuntu-linux/")

After that, between 10-20 wake-ups per second from kernel scheduler...

---

### Post by florinn on 2011-01-26
I solved the problem installing linux-image-2.6.37-020637rc2-generic_2.6.37-020637rc2.201011160905_i386.deb
Load balacing tick dropped from 40-50% to 2-3% in powertop
But I could not use this kernel because I need a kernel with PAE and also because virtualbox is not working with this kernel on Ubuntu Maverick

---

### Post by jdsmofo on 2011-09-28
I have read several threads on this topic because my sony vaio has been chewing up power like crazy.  And runs painfully slowly.  Powertop showed something like 100 wakeups from idle when there was nothing running but the terminal.   Since it was supposedly a kernel problem, I saw no choice but to upgrade from the LTS to nattty. 
I was reluctant, but did not know what else to do.  So, I am now in Natty and the wakeups are three to four times WORSE.  And I have lost other software functionality in the upgrade.  

Luckily this bug is seen as low importance, and has gone unfixed for a year.  Why? Many laptop users report it.  It kills the laptop when unplugged.  Makes it painful to use linux.  I have had good luck with lucid on my desktops, but if this were my first foray into linux, I would delete it and probably never try it again.

---

