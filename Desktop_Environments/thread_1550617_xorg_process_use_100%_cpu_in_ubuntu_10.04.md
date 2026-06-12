---
title: "xorg process use 100% cpu in ubuntu 10.04"
date: 2010-08-11
forum: Desktop Environments
---

### Post by tejasd on 2010-08-11
Hi All,

Recently, my pc xorg process was use 100% CPU  of system


Need Help 
Tejas

---

### Post by TheFu on 2010-12-18
I don't want to hijack your thread, but I've been having a similar issue since moving to 10.04 in June. It happened again today just by typing 'ls' into an xterm window.  I had to ssh in from another machine to access the problem desktop.


I figured that showing a little debug-type information would be helpful to others ... and hopefully someone will know exactly what my issue is too.

Here's 'top' output (left the ext-ASCII in) - Xorg is stuck at 100% and cannot be killed:
[FONT=Courier New]top - 11:42:21 up 17:45,  3 users,  load average: 6.24, 6.03, 4.67
Tasks: 220 total,   6 running, 213 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.0%us, 25.0%sy,  0.0%ni, 75.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8187668k total,  6490560k used,  1697108k free,    13728k buffers
Swap: 11912156k total,        0k used, 11912156k free,  5503668k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                              
 1494 root      20   0     0    0    0 R  100  0.0  30:39.88 Xorg                                  

[/FONT] Here's the tail of dmesg - nVidia driver is crashing:

[FONT=Courier New][62514.327669] Call Trace:
[62514.327910]  [<ffffffffa04d199f>] ? _nv013927rm+0xc6/0xef [nvidia]
[62514.328131]  [<ffffffffa0367b1b>] ? _nv016209rm+0x1bf/0x5af [nvidia]
[62514.328348]  [<ffffffffa034a2d1>] ? _nv016212rm+0x1f0/0x484 [nvidia]
[62514.328581]  [<ffffffffa04a8115>] ? _nv004584rm+0x886/0x8fd [nvidia]
[62514.328814]  [<ffffffffa04a69d6>] ? _nv004586rm+0x39/0x46 [nvidia]
[62514.329047]  [<ffffffffa04a6d5c>] ? _nv004577rm+0xe5/0x4c7 [nvidia]
[62514.329280]  [<ffffffffa04a69d6>] ? _nv004586rm+0x39/0x46 [nvidia]
[62514.329514]  [<ffffffffa04a6afd>] ? _nv004581rm+0x11a/0x294 [nvidia]
[62514.329747]  [<ffffffffa04a69d6>] ? _nv004586rm+0x39/0x46 [nvidia]
[62514.329982]  [<ffffffffa0531fe3>] ? _nv004545rm+0xcb/0x10c [nvidia]
[62514.330218]  [<ffffffffa0533c5c>] ? rm_free_unused_clients+0x69/0xb7 [nvidia]
[62514.330414]  [<ffffffffa0620934>] ? nv_kern_ctl_close+0x74/0x100 [nvidia]
[62514.330609]  [<ffffffffa0621693>] ? nv_kern_close+0x393/0x3f0 [nvidia]
[62514.330617]  [<ffffffff8114556f>] ? __fput+0xdf/0x1f0
[62514.330620]  [<ffffffff811456a5>] ? fput+0x25/0x30
[62514.330624]  [<ffffffff811417ed>] ? filp_close+0x5d/0x90
[62514.330630]  [<ffffffff81067fbf>] ? put_files_struct+0x7f/0xf0
[62514.330633]  [<ffffffff81068084>] ? exit_files+0x54/0x70
[62514.330637]  [<ffffffff8106a49b>] ? do_exit+0x14b/0x380
[62514.330641]  [<ffffffff8106a725>] ? do_group_exit+0x55/0xd0
[62514.330647]  [<ffffffff8107af77>] ? get_signal_to_deliver+0x1d7/0x3d0
[62514.330652]  [<ffffffff810116e4>] ? __setup_rt_frame+0x404/0x450
[62514.330657]  [<ffffffff81011a25>] ? do_signal+0x75/0x1c0
[62514.330661]  [<ffffffff81057960>] ? finish_task_switch+0x50/0xe0
[62514.330667]  [<ffffffff81558318>] ? thread_return+0x48/0x420
[62514.330671]  [<ffffffff81011bcd>] ? do_notify_resume+0x5d/0x80
[62514.330675]  [<ffffffff81012c1c>] ? retint_signal+0x48/0x8c
[/FONT]
So it seems the nVidia driver is crashing.  Syslog shows nVidia driver crashing a few times previously ... today, yesterday, before it locked up.  Because of all the lock ups, I don't really use this system behind the head much. I remote in.

This box is an i5-750 x64 running 10.04.1 and patched weekly.  I reloaded the nVidia dirvers "185" yesterday in hope that would force a rebuild for my specific system. I saw that newer drivers were released, but want to wait a month.

[FONT=Courier New]$ lsmod|grep -i nvid
nvidia              10832442  28 

[/FONT]The driver module is definitely being loaded and used.

lshw shows this for the graphics card:
[FONT=Courier New]           *-display
                description: VGA compatible controller
                product: G73 [GeForce 7600 GS]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:fa000000-faffffff memory:d0000000-dfffffff(prefetchable) memory:f9000000-f9ffffff ioport:cc00(size=128) memory:fbee0000-fbefffff(prefetchable)
[/FONT]
I've been driving dual monitors with this card for years.  Just in 2010 has X/Windows become unstable. Here's the kernel info - I believe this is the latest kernel.

[FONT=Courier New]$ uname -a
Linux romulus 2.6.32-26-server #48-Ubuntu SMP Wed Nov 24 10:28:32 UTC 2010 x86_64 GNU/Linux
[/FONT]
So, any help determining what the issue is would be appreciated.  If I don't login directly on the head, the system is rock solid for running KVM  and a few VMs with multiple months of uptime.  With X/Windows running - even just the login screen, it will lock up after just a few days even if I don't login.  

Suggestions?

---

### Post by Polar Humenn on 2011-01-11
I've recently had the same problem after some recent upgrades 

My system works fine all day, then at some times I come back in the morning and my machine is all but dead. No screens, blank (probably because the card shut down the signal to  the monitors). No amount of key presses turns them back on. So, I remote in from another machine.

I can get limited response from my machine for some diagnostics

htop shows Number 2 processor (AMD64) at 100% and Xorg at 100% CPU, but processor #1 is running at 2-5%, which is probably why I'm getting some command response at all.

The last part of the Xorg log is:
[ 55648.072] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select+1280+0,DFP-1:nvidia-auto-select+0+0"
[ 55653.072] (WW) NVIDIA(0): WAIT (2, 1, 0x8000, 0x000000d0, 0x000013bc)
[ 55662.074] (WW) NVIDIA(0): WAIT (1, 1, 0x8000, 0x000000d0, 0x000013bc)
[ 55667.072] (WW) NVIDIA(0): WAIT (2, 1, 0x8000, 0x000000d0, 0x00001414)
[ 55672.075] (WW) NVIDIA(0): WAIT (1, 1, 0x8000, 0x000000d0, 0x00001414)
[ 55675.136] (WW) NVIDIA(0): WAIT (2, 11, 0x8000, 0x000000d0, 0x00001488)
[ 55686.074] (WW) NVIDIA(0): WAIT (1, 11, 0x8000, 0x000000d0, 0x00001488)
[ 55691.074] (WW) NVIDIA(0): WAIT (2, 11, 0x8000, 0x000000d0, 0x000014dc)
[ 55700.074] (WW) NVIDIA(0): WAIT (1, 11, 0x8000, 0x000000d0, 0x000014dc)

I do see a bunch of the following messages in the syslog:
Jan 11 10:07:19 adiron kernel: [86015.072527] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
Jan 11 10:07:19 adiron pulseaudio[5036]: module-rtp-send.c: Failed to push chunk into memblockq.

I looked back to the first occurrence of this message. Every thing seems normal before the first on of the above messages shows up. Another following message that emerges immediately and repeats is:

Jan 11 01:40:16 adiron kernel: [55592.072532] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
Jan 11 01:40:18 adiron pulseaudio[5036]: module-rtp-send.c: Failed to push chunk into memblockq.
Jan 11 01:40:22 adiron pulseaudio[5036]: last message repeated 9 times
Jan 11 01:40:22 adiron kernel: [55598.669205] NVRM: Xid (0002:00): 6, PE0000 1c38 00000000 0000b248 00000000 ffc3c319
Jan 11 01:40:22 adiron kernel: [55598.672665] NVRM: Xid (0002:00): 6, PE001e 0100 0000000b 00000000 a7a7a7a7 00000000
Jan 11 01:40:23 adiron kernel: [55599.072550] NVRM: Xid (0002:00): 8, Channel 00000020
Jan 11 01:40:25 adiron kernel: [55601.072525] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
Jan 11 01:40:27 adiron pulseaudio[5036]: module-rtp-send.c: Failed to push chunk into memblockq.
Jan 11 01:40:32 adiron pulseaudio[5036]: last message repeated 7 times

I get the NVRM which is probably the Nvidia Kernel driver. The pulseaudio message seems strange. I am running Skype, and I have patched the Xorg system with that recent Qt bug. But even so I don't think it applies to me, as I'm running dual monitors in Twinview. In any case, I have the same result before and after that patch yesterday.

My Graphics card is: lspci
02:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a1)

Thie following info is from nvidia-settings:

NVidia Driver Version is 260.19.05
X Server Vendor Version 1.9.0
NV_CONTROL Version: 1.24

Now, i I kill the X server, then the machine just stops responding and I have to hard boot.

Any insight?

Cheers,
-Polar

---

### Post by Polar Humenn on 2011-01-24
I'm upgrading to NVida 260.19.36. We'll see how it goes.

Cheers,
-Polar
[B][SIZE=1]
[/SIZE][/B]

---

### Post by Polar Humenn on 2011-01-29
So far, so good. No hangs since the upgrade of the Nvidia Driver.

---

### Post by Polar Humenn on 2011-02-07
Not quite. It seems not to be hanging as often, but it still hangs the same way. This apparently is only affecting the AMD 64 architecture, as my 32 bit Intel machine seems to be fine.

---

### Post by dphurst on 2011-02-09
I can confirm on a Dell Precision 470 dual Xeon system with Ubuntu 10.04 64bit that this behavior occurs.  Typically, when I arrive in the morning, Xorg is at 100% cpu usage, there is a driver wait message in Xorg.0.log, and I have to log in with ssh remotely to restart the machine.  Kill -9 doesn't work on Xorg, restarting gdm doesn't work.  I've only recovered by a "shutdown -r now".  This is really stupid since the machine was fine in November.  Sometime in the past two months an update has changed the system's behavior.

I seem to remember a glibc update and other libraries being updated in the past two months.

NVIDIA GLX Module  173.14.22
NVIDIA GPU Quadro FX 1300 (NV35GL)
2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux

I found a post where someone mentioned putting Options "UseEvents" False in the xorg.conf file but reading a bit on this indicates that it should be by default set to False.  If this is not the case then a hardware problem could cause the system to wait forever.  Here is an explanation of Use Events from the nvidia-xconfig manpage:

--use-events, --no-use-events
	      Enable  or  disable  "UseEvents" X configuration option. Setting
	      this option will enable the X driver to use the system events in
	      some cases when it is waiting for the hardware. With this option
	      X driver sets an	event  handler	and  waits  for  the  hardware
	      through the poll() system call. This option defaults to FALSE.



Thanks,
Dow

---

### Post by Polar Humenn on 2011-02-10
Thanks Dow,

Right now, I'm finding that if it is not hung in the morning the performance really starts to degrade, composting gets really slow, although not at 100% CPU it's pretty close around 80-90%. I imagine if I just waited a bit more, it would just hang soon.

I'm not a gamer and do mostly development work, so the fast video and stuff doesn't bother me if it's slow, but it degrades my machine, and switching between desktops being really slow annoys me. You're right, I noticed this problem after an update in November as well. 

At a loss at what to do, but pretty much blaming the Nvidia modules, I just installed and am running the 270.18 Beta for the GeoForce 7 series and we'll see how it goes. 

Cheers,
-Polar

---

### Post by w4r_l0ck on 2011-02-11
Hi all,
I'm having the same problem as well. Running Maverick on XPS M1530, Core2Duo, 8600M GT. (driver 260.19.06) Been crawling all over the internet for a solution but still couldn't find any.

Symptoms are:
Computer runs fine on boot. However Xorg processes start to eat up more and more CPU% gradually. After (around 12 hours), cpu monitor shows that Xorg is taking up 60-70%(on idle).

---

### Post by nherriot on 2011-03-13
Hi All,


I can also confirm the same behaviour.

I stupidly upgraded my Dell Lattidtude E4310 and my main work PC to Ubuntu 10.10 maverick. Got same behaviour in both.... 2-3 days max and I run out of CPU all on the Xorg process.

My main machine is using twin view - but the laptop is just a plain old laptop. So I guess we can rule out anything to do with using dual monitors.

If anyone knows a fix for this I'd be grateful ...

---

### Post by jrothney on 2011-03-31
Hi guys,

I'm experiencing this as well. I've tried different flavours of Ubuntu 10.04, Mythbuntu 10.04, Mythbuntu 10.10. All have the same issue:
- CPU usage climbs to 100%, making the video crap out and the system unresponsive, except when connecting from a different machine (it is still sluggish, but works)

I am trying to drive dual displays (CRT monitor over VGA and Toshiba LCD TV over HDMI) from my nvidia GT 430 card.

It craps out faster with both displays running, but will die eventually even with just the CRT.

I have only tried 64-bit installs and wondering if that may have some effect. Have any of you tried 32-bit installs?

James

---

### Post by irfan20uk on 2012-07-30
Hi guys,
So did anyone solve this problem or it still existing?
I am very much afraid while mentioning am the victim of the same symptom. If some one had figure out this bug then please do favour us also.

---

### Post by oldos2er on 2012-07-30
Hi irfan20uk, please start a new thread for your question. Old thread closed.

---

