---
title: "Blank background after login since update"
date: 2014-11-07
forum: Desktop Environments
---

### Post by kevin124 on 2014-11-07
Hi,

I've recently (a few months ago) installed xUbuntu 14.04 and managed to get my nVidia graphic card to work properly and install a few tools.
Everything was working perfectly fine until installing some updates yesterday or the day before (I'm unsure).

I have no idea what I installed, it was done through the update center.

Since then, when I start my laptop under xUbuntu, I get the login screen but once logged in, I'm stuck a an empty screen with only the background.

The second screen is not plugged in the computer.

I've tried SUPER+T, ALT+F2, etc... without success, nothing happens.

Here is a video of what happens.
[http://youtu.be/rOF_KDukfww](http://youtu.be/rOF_KDukfww)

What should I do to get my xUbuntu working again?

---

### Post by Bucky Ball on 2014-11-07
Welcome. ctl+alt+F1 should get you to a cli from where your computer hangs on the vid. Unsure what other keys you're pressing there.

Login there then type 'startxfce4'. That should at least get you to a desktop so you can re-install the drivers. If you upgraded the kernel in that update it probably wiped them if you installed them manually. 

If that doesn't get you to a desktop, let us know what error you get. (Also, if it does get you to a desktop, immediately open a terminal and 'dmesg'. Post the last part of that between code tags thanks - see the last link in my signature for how.)

---

### Post by kevin124 on 2014-11-07
Hi Bucky,

First of all, thank you for your help and your quick answer.

I managed to start xfce.
Running startxfce4 from the CLI wasn't working , I had to first stop the lightdm daemon and then run the command again.

Regarding the nvidia drivers, I installed them using the standard tool from xubuntu (I can't remember the name, but basically it detected I had a nvidia card and I just had to select to install the proprietary drivers).

Here is the complete dmesg (from just a few lines above the first "nvidia" occurence in the output):
```

[   12.146901] type=1400 audit(1415419881.009:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=364 comm="apparmor_parser"
[   12.146909] type=1400 audit(1415419881.009:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=364 comm="apparmor_parser"
[   12.146915] type=1400 audit(1415419881.009:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=364 comm="apparmor_parser"
[   12.147357] type=1400 audit(1415419881.009:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=364 comm="apparmor_parser"
[   12.147363] type=1400 audit(1415419881.009:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=364 comm="apparmor_parser"
[   12.147592] type=1400 audit(1415419881.009:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=364 comm="apparmor_parser"
[   12.150130] nvidia: module license 'NVIDIA' taints kernel.
[   12.150134] Disabling lock debugging due to kernel taint
[   12.164674] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   12.172755] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   12.183824] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   12.183840] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.38  Wed Jan  8 19:32:30 PST 2014
[   12.297918] snd_hda_intel 0000:00:1b.0: irq 50 for MSI/MSI-X
[   12.335509] hda_codec: ALC663: SKU not ready 0x598301f0
[   12.335802] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   12.335804]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.335805]    hp_outs=2 (0x15/0x21/0x0/0x0/0x0)
[   12.335807]    mono: mono_out=0x0
[   12.335808]    dig-out=0x1e/0x0
[   12.335809]    inputs:
[   12.335811]      Internal Mic=0x19
[   12.335813]      Mic=0x18
[   12.335814] realtek: No valid SSID, checking pincfg 0x598301f0 for NID 0x1d
[   12.335815] realtek: Enable default setup for auto mode as fallback
[   12.349311] autoconfig: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
[   12.349314]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.349316]    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.349317]    mono: mono_out=0x0
[   12.349318]    inputs:
[   12.369129] input: HDA Intel HDMI/DP,pcm=3 Phantom as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[   12.369253] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[   12.369389] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   12.369491] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   12.402052] Linux video capture interface: v2.00
[   12.427320] uvcvideo: Found UVC 1.00 device USB2.0 1.3M UVC WebCam (04f2:b033)
[   12.427995] input: USB2.0 1.3M UVC WebCam as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input19
[   12.428514] usbcore: registered new interface driver uvcvideo
[   12.428516] USB Video Class driver (1.1.1)
[   12.678566] init: failsafe main process (479) killed by TERM signal
[   12.694431] cfg80211: World regulatory domain updated:
[   12.694436] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.694438] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.694440] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.694442] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.694443] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.694445] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.735798] type=1400 audit(1415419881.597:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=576 comm="apparmor_parser"
[   12.735807] type=1400 audit(1415419881.597:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=576 comm="apparmor_parser"
[   12.738566] type=1400 audit(1415419881.601:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=576 comm="apparmor_parser"
[   12.912489] iwlwifi 0000:03:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[   12.931365] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   12.931370] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   12.931372] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   12.931375] iwlwifi 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   12.931701] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   12.932112] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[   12.969715] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.988167] init: cups main process (578) killed by HUP signal
[   12.988183] init: cups main process ended, respawning
[   13.213178] Bluetooth: Core ver 2.17
[   13.213201] NET: Registered protocol family 31
[   13.213202] Bluetooth: HCI device and connection manager initialized
[   13.213409] Bluetooth: HCI socket layer initialized
[   13.213412] Bluetooth: L2CAP socket layer initialized
[   13.213417] Bluetooth: SCO socket layer initialized
[   13.218106] Bluetooth: RFCOMM TTY layer initialized
[   13.218117] Bluetooth: RFCOMM socket layer initialized
[   13.218123] Bluetooth: RFCOMM ver 1.11
[   13.236376] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.236381] Bluetooth: BNEP filters: protocol multicast
[   13.236391] Bluetooth: BNEP socket layer initialized
[   13.248691] type=1400 audit(1415419882.113:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=716 comm="apparmor_parser"
[   13.972934] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.985378] r8169 0000:08:00.0 eth0: link down
[   13.985390] r8169 0000:08:00.0 eth0: link down
[   13.985412] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.985686] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.334068] init: plymouth-upstart-bridge main process ended, respawning
[   15.644617] r8169 0000:08:00.0 eth0: link up
[   15.644628] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   15.670556] init: plymouth-splash main process (1017) terminated with status 1
[   17.559316] nvidia 0000:01:00.0: irq 51 for MSI/MSI-X
[   42.847880] audit_printk_skb: 105 callbacks suppressed
[   42.847884] type=1400 audit(1415419911.707:47): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1602 comm="apparmor_parser"
[   42.847891] type=1400 audit(1415419911.707:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1602 comm="apparmor_parser"
[   42.848370] type=1400 audit(1415419911.711:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1602 comm="apparmor_parser"
[  142.179669] nvidia 0000:01:00.0: irq 51 for MSI/MSI-X
[  790.693615] perf samples too long (2508 > 2500), lowering kernel.perf_event_max_sample_rate to 50000

```

---

### Post by Bucky Ball on 2014-11-08
If you do an update then check Additional Drivers (which I think is the auto-driver installer you were talking about) do you see anything there for your NVidia?

---

### Post by kevin124 on 2014-11-08
So, I couldn't find anything in the menu to update or get rid of the nvidia driver. I did a "apt-get remove nvidia*".

After a reboot, it's better.
After authenticating to my session, the background is an ugly checkerboard-ish shape until xfce starts (I didn't have that with the nvidia drivers).
When xfce is started, I have the proper background, icons on the desktop, right click menu, functionnal SUPER+** shortcuts. In fact, almost everything except for the top "Start menu" (sorry, I don't know the xfce terminology for this bar).

---

### Post by Bucky Ball on 2014-11-08
Try:

```
xfce4-panel
```

... in a terminal.

---

### Post by kevin124 on 2014-11-15
I'm back :-)

So, I tried running the command you gave me, but the system tells me that xfce4-panel is already running.
> me@PC:~$ xfce4-panel 
xfce4-panel: There is already a running instance

me@PC:~$

EDIT:
Just tried the following : [http://askubuntu.com/questions/359559/help-my-panel-in-xubuntu-disappeared](http://askubuntu.com/questions/359559/help-my-panel-in-xubuntu-disappeared)

Absolutely no change.

---

### Post by kevin124 on 2014-11-25
I finally reinstalled xubuntu, problem "solved".
It's a windows-style solution and I don't like it, but it's the only one working.

---

