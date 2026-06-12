---
title: "pulseaudio causing freezes?"
date: 2009-01-30
forum: General Help
---

### Post by zmzach on 2009-01-30
Hi there. I just reinstalled ubuntu 8.10 on my IBM T60 thinkpad. Previous to the install I had no problems. But now my laptop will just randomly lock up, sometimes within the first few minutes of turning it on, sometimes an hour goes by, it's incredibly frustrating. I don't believe it to be any hardware issues as it worked fine before the reinstall.

Here's what my log says right before I have to hard reset:
> Jan 29 23:27:36 zachl-laptop pulseaudio[5586]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan 29 23:27:36 zachl-laptop pulseaudio[5588]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan 29 23:27:36 zachl-laptop pulseaudio[5588]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan 29 23:29:08 zachl-laptop kernel: [  125.985474] CE: hpet increasing min_delta_ns to 15000 nsec
Jan 29 23:29:09 zachl-laptop kernel: [  127.773468] CE: hpet increasing min_delta_ns to 22500 nsec
Jan 29 23:29:10 zachl-laptop kernel: [  128.089503] CE: hpet increasing min_delta_ns to 33750 nsec
Jan 29 23:29:12 zachl-laptop kernel: [  130.297363] CE: hpet increasing min_delta_ns to 50624 nsec
Jan 29 23:29:15 zachl-laptop kernel: [  133.113477] CE: hpet increasing min_delta_ns to 75936 nsec
Jan 29 23:29:18 zachl-laptop kernel: [  136.089499] CE: hpet increasing min_delta_ns to 113904 nsec
Jan 29 23:47:25 zachl-laptop -- MARK --

Looks like a pulseaudio issue. Not really sure what pulseaudio is, but I can play music and sounds without any problems (until it locks up randomly).

Does anybody have a solution to this? Thanks so much!

---

### Post by halovivek on 2009-01-30
Can you post the output?

lspci

---

### Post by zmzach on 2009-01-31
Here's what lspci says:
> zachl@zachl-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller


---

### Post by hammondb3 on 2009-01-31
Im having a similar issue not sure if its pulse audio but 
there are messages like this in my logfile about pulse audio
after screen saver comes on my system freezes

---

### Post by zmzach on 2009-01-31
> **hammondb3 said:**
> Im having a similar issue not sure if its pulse audio but 
there are messages like this in my logfile about pulse audio
after screen saver comes on my system freezes

Interesting. Ya I don't run a screensaver so I don't know, but now my computer's been on for about 5 hours and it hasn't frozen. However when I first turned it on 5 hours and 10 minutes ago it froze within a couple minutes. It seems like it'll freeze once pretty quickly, but when you restart it it'll run normally. I'm at my wits end. 

I'm always the guy with the problems for which nobody has any answers!

---

### Post by kostkon on 2009-01-31
I don't think it is caused by PulseAudio, but it may be. It is for sure a kernel problem that does not have a definite source as you can see in [this bug report on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/270798").

Unfortunately, I can't help you more...

---

### Post by Taxi on 2009-02-02
I'm having the same, or at least a very similar, problem.

It started with the extensive kernel and PulseAudio updates for Intrepid on January 28th.  At first I suspected the kernel updates were the problem, but I was able to duplicate the freezes when booted into the previous kernel, as well.

On my system, the freezes are definitely sound-related; it seems to be totally stable until I start playing audio.  It has definitely frozen when Totem was playing an mp4 video downloaded from YouTube, and with Audacious playing mp3 audio.

When it happens, the system completely locks up.  No reponses to Alt+Ctrl+F1, Alt+Ctrl+Backspace, or even (Alt+Control+PrintScreen)R+E+I+S+U+B.

If it helps, here is the info given by lspci regarding my audio chipset:
00:10.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

Can anyone offer any insights?

---

