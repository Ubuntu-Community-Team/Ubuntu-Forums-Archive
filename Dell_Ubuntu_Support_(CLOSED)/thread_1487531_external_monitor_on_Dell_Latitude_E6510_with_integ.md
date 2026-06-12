---
title: "external monitor on Dell Latitude E6510 with integrated graphics"
date: 2010-05-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tohen2010 on 2010-05-19
Hi,

I have a Dell Latitude E6510 with an integrated Intel Graphics Card with Ubuntu 10.04 installed. lspci show me the following:

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
        Subsystem: Dell Device 040b
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 36
        Region 0: Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
        Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Region 4: I/O ports at 70b0 [size=8]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
                Address: fee0500c  Data: 41d9
        Capabilities: [d0] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [a4] PCIe advanced features <?>
        Kernel driver in use: i915
        Kernel modules: i915
```The problem is: When I attach a second monitor and use xrandr -q or start "System | Settings | Display" the System completely freezes. There is nothing in the logs as the system stops doing everything.
When I start the Live-System from the intall-CD, everything works fine and I can use the external monitor. When I install the System and then start it without doing an update (which I think means it should be the same system)  the problem occurs as described.

Does anyone has problems like this with this system or another system with same cpu und graphics
I would be thankful for any kind of help.

---

### Post by dschulz on 2010-05-27
I received (finally!) a similar laptop yesterday, a Dell Latitude E6510 with Intel integrated graphics. I asked specifically for Intel Graphics as it has a free driver that supports kernel mode setting. 

But I'm quite dissapointed right now as I can't even boot the livecd, the screen simply turns black no matter the kernel parameters passed. The only thing left to try is to directly install with the alternate cd, but of course there's a high probability that X will simply not work once ubuntu is fully installed and windows 7 wiped. I just don't want to be there, whining at the bash console with my shiny new unusable 1800 dollars laptop.

How did you get Ubuntu installed?

---

### Post by SharkUSMC on 2010-05-28
Check here, worked for me: [http://georgia.ubuntuforums.org/showpost.php?p=9195971&postcount=14](http://georgia.ubuntuforums.org/showpost.php?p=9195971&postcount=14)

---

### Post by dschulz on 2010-05-28
> **SharkUSMC said:**
> Check here, worked for me: [http://georgia.ubuntuforums.org/showpost.php?p=9195971&postcount=14](http://georgia.ubuntuforums.org/showpost.php?p=9195971&postcount=14)

Thanks for your reply. I already tried that but unfortunately doesn't work for me. It boots rather normally in text mode (I always remove the "quiet splash") to the point X should come up, but it all ends with Caps and Numlock leds blinking madly.

---

### Post by dschulz on 2010-05-28
ok, finally it worked using the following kernel args

```
nomodeset xforcevesa
```

Typing this from the new kubuntu installation.

@tohen2010: excuse me for polluting the thread with this issue, not directly related to your problem.

---

### Post by sf_basilix on 2010-06-18
Was this issue ever resolved?  I am having the exact same problem. I have a Dell Latitude E6510 running Ubuntu 10.04. Everything seems to work fine, except when I plug in an external (second) monitor. Once I attach the monitor, I go into System -> Preferences -> Monitors and at that point the screen turns black and everything hangs. Can't move the mouse or even do any sequence of keys.  I've tried both 32 bit and 64 bit versions of Ubuntu - both do exactly the same.

I ran this with firmware A01, then the A01.1 (patch) and then A03. All exhibited the same behavior.

It's a shame, I was really hoping to have this ability to do an external display for my presentations.

Anyone else have any suggestions on what to try?

UPDATE: I believe the video adapter (according to Dell's site) is this one:   Intel QM57/QS57 NB Gfx - Intel GMA HD

---

### Post by bach on 2010-07-01
I am running Ubuntu 10.04 64 bits on a DELL E6510 with Intel integrated graphics card. I can only boot by using the kernel option "i915.modeset=0". The problem is that it boots in low graphics mode. The X log file says 

(EE) intel(0): No kernel modesetting driver dettected 

My bios is A03. Suggestions are welcome.

---

### Post by jogojapan on 2010-07-13
This is the same problem I encountered on Fedora 12 and Fedora 13. It's related to problems in the Intel graphics drivers that come with recent kernel versions.

The problem is solved in kernel 2.6.35, but that version is probably not available yet as a regular kernel update for Ubuntu (nor Fedora).

What I did to solve this on Fedora 12 is to download the kernel sources, fix the problem manually and rebuild the kernel. The code lines that need to be changed are described under the two links I included in the bug report to Fedora:

[https://bugzilla.redhat.com/show_bug.cgi?id=607864](https://bugzilla.redhat.com/show_bug.cgi?id=607864)

(see the entry of July 7th, 2010)

---

### Post by Stefanie on 2010-07-20
I'm running kernel 2.6.35-7 under lucid (I downloaded the individual debs for the kernel) and the issue is not solved for me...

---

### Post by jogojapan on 2010-07-20
Just to be sure: Do you plug in the monitor after booting and starting X, or is the monitor already plugged-in when you boot the computer? The latter does not work for me either.

---

### Post by Stefanie on 2010-07-26
When I plug in the monitor after X has started the system freezes. Bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607783](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607783)

---

### Post by Stefanie on 2010-08-05
Fix here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607783](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/607783)

---

### Post by semmypurewal on 2010-08-12
I managed to get two monitors working by installing the backported maverick kernel:

```

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update && sudo apt-get install linux-lts-backport-maverick

```This was after I installed lucid using by using the following kernel parameters to boot the live environment:

```

i915.modeset=0 xforcevesa

```That allowed me to do an install, and then I only needed the following kernel parameter to boot:

```

i915.modeset=0

```After that, I was able to install the backported maverick kernel as above which allowed me to boot with no special kernel parameters.  Finally, I reconfigured X to use the intel driver instead of the vesa driver.

I should also note that the second monitor is plugged in via a Dell docking station -- I haven't tried to plug it in directly.

---

### Post by EJH on 2010-08-16
Brilliant work, semmypurewal, I was having the excact same problem with a laptop here (which, ironically, was bought for maximum Linux compatibility).

---

### Post by sf_basilix on 2010-09-02
I never got this to work. In fact, I just recently received a new problem. With yesterday's patches (9/1/2010), it completely broke my video card. I don't know what happens, but when I boot up, there is no display at all. Not even a splash screen. I do hear it booting and I can hear the drum sound, so I know it's working in the background, but I can't even ALT+F3-12 to get a regular display. Nothing shows up. I had to hold the shift key down when booting to get into grub and then chose an older kernel, which booted fine.

If anyone has seen that happen with the latest patches, please let me know here:

[http://ubuntuforums.org/showthread.php?t=1566500](http://ubuntuforums.org/showthread.php?t=1566500)

As far as the problem regarding the OP, I had bought a d-port connector for the E6510 laptop to VGA and DVI. Both work but are a bit buggy. It doesn't lock up the system though (as does the vga port built into the back of the laptop).

---

### Post by semmypurewal on 2010-09-03
> **sf_basilix said:**
> I never got this to work.

Hi, SF_Basilix.  Sorry to hear that you're having problems.  When you say you never got 'this' to work, to what are you referring?

I've had my Dell E6510 with an Intel video card running the 32-bit Lucid for about a month now.  I'm running the Maverick kernel though (as described above).  I could not get the Intel driver working with the Lucid kernel.

Yesterday's updates did not affect my machine.

---

### Post by Stefanie on 2010-09-03
It's a known bug, there was a regression in 2.6.35 final which also made it into the latest lucid kernels.

[https://bugs.launchpad.net/bugs/561802](https://bugs.launchpad.net/bugs/561802)

[https://bugs.freedesktop.org/show_bug.cgi?id=29278](https://bugs.freedesktop.org/show_bug.cgi?id=29278)

---

### Post by semmypurewal on 2010-09-07
Thanks for the response.  Note that you've linked to bugs in the 64-bit lucid distro.  I haven't tried that one.

I'm running the 2.6.35 maverick kernel with the intel driver and I am having no problems in the 32-bit lucid.  (I did have the black-screen problems trying to boot from the live CD, though.  I described the solution above)

---

### Post by sf_basilix on 2010-09-07
> **semmypurewal said:**
> Hi, SF_Basilix.  Sorry to hear that you're having problems.  When you say you never got 'this' to work, to what are you referring?

I've had my Dell E6510 with an Intel video card running the 32-bit Lucid for about a month now.  I'm running the Maverick kernel though (as described above).  I could not get the Intel driver working with the Lucid kernel.

Yesterday's updates did not affect my machine.

Sorry, what I never got to work was the external VGA adapter. Anything I plug into there just halts my machine and it dies.

I'm not seeing an update in the synaptic package manager for the latest kernel .35 - does anyone know when the folks at Ubuntu will release this?  I'm still fairly new to using ubuntu so I'm a bit hesitant to install the kernel by hand.

Thanks!

---

### Post by semmypurewal on 2010-09-09
> **sf_basilix said:**
> Sorry, what I never got to work was the external VGA adapter. Anything I plug into there just halts my machine and it dies.

I'm not seeing an update in the synaptic package manager for the latest kernel .35 - does anyone know when the folks at Ubuntu will release this?  I'm still fairly new to using ubuntu so I'm a bit hesitant to install the kernel by hand.

Thanks!

I noticed that you posted in some other threads that you're running the 64-bit 10.04.  Have you thought of giving the 32-bit a try on your machine, at least until this problem is resolved?  I managed to get it working on the same machine (dell latitude E6510, i5, intel graphics) and -- despite the complex install/setup -- it has been running pretty well for me over the last month or so.

The only two things that have caused me problems are the wireless and the internal microphone.  I managed to get the wireless working, but I still haven't been able to get the internal mic working.

I've posted some rough instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1509957&page=2") if you want to give them a try:

[http://ubuntuforums.org/showthread.php?t=1509957&page=2](http://ubuntuforums.org/showthread.php?t=1509957&page=2)

---

