---
title: "PLEASE, could really use some help on this one!"
date: 2009-04-01
forum: General Help
---

### Post by tmun52 on 2009-04-01
I've tried everything I could think of, but I cannot get the fglrx drivers to work on my computer. I've followed countless guides on the internet and tweaked my xorg.conf, but every time I restart the computer after installing the fglrx drivers from the ati website or from the restricted drivers manager, the computer hangs up after 30 seconds. This causes me to do a hard reboot and makes me go into recovery mode in order to uninstall the drivers. I've been trying for months with no avail, and the forum hasn't been very helpful either. I hope you guys can finally help me with my dilemma. 

Computer Specs:

Ubuntu Intrepid Ibex 8.10
Dell Pentium 4600
Intel Pentium 4 2.8 GHz processor
Sapphire ATI Radeon HD 3650 512MB AGP


Please tell me if you need any more info.

---

### Post by tmun52 on 2009-04-01
How come no one wants to help me?

---

### Post by Mze on 2009-04-01
From the Phoronix forums, I found [this]("http://www.phoronix.com/forums/showthread.php?p=68962"). Is this something you've tried already?

Or try 9.04 live CD to see if there's a fix.

---

### Post by Godly on 2009-04-01
Does it show any conflicts, ask to enable or disable anything? Under appearance>visual efects do you have this enabled? Have you O.C.'d your computer? Let me know.

---

### Post by tmun52 on 2009-04-02
> **Mze said:**
> From the Phoronix forums, I found [this]("http://www.phoronix.com/forums/showthread.php?p=68962"). Is this something you've tried already?

Or try 9.04 live CD to see if there's a fix.

Thanks so much for your help, I'm trying that solution right now


> **Godly said:**
> Does it show any conflicts, ask to enable or disable anything? Under appearance>visual efects do you have this enabled? Have you O.C.'d your computer? Let me know.

Thanks, but it doesn't ask me anything when I try to enable visual effects. It tries to install the drivers when I try to enable the effects, but then it says Desktop Effects could not be enabled.

Also, I haven't even tried to OC my computer.

---

### Post by tmun52 on 2009-04-02
Ok, so I tried the suggestions that Mze gave me, but the X server still froze when I rebooted. Here's my system log of the reboot:

```
Apr  2 20:10:44 taher-desktop gdm[5061]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Apr  2 20:10:44 taher-desktop NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Apr  2 20:10:44 taher-desktop NetworkManager: <info>  (wlan0): deactivating device (reason: 38). 
Apr  2 20:10:44 taher-desktop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 9324 
Apr  2 20:10:44 taher-desktop kernel: [13943.970855] rndis_wlan 5-5:1.0: rndis media disconnect
Apr  2 20:10:45 taher-desktop NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Apr  2 20:10:45 taher-desktop avahi-daemon[4623]: Withdrawing address record for 192.168.1.2 on wlan0.
Apr  2 20:10:45 taher-desktop avahi-daemon[4623]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.2.
Apr  2 20:10:45 taher-desktop avahi-daemon[4623]: Interface wlan0.IPv4 no longer relevant for mDNS.
Apr  2 20:10:45 taher-desktop console-kit-daemon[4808]: WARNING: Unable to activate console: No such device or address 
Apr  2 20:10:45 taher-desktop console-kit-daemon[4808]: GLib-GObject-WARNING: instance of invalid non-instantiatable type `(null)' 
Apr  2 20:10:45 taher-desktop console-kit-daemon[4808]: GLib-GObject-CRITICAL: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 
Apr  2 20:10:45 taher-desktop console-kit-daemon[4808]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed 
Apr  2 20:10:46 taher-desktop acpid: client connected from 18185[0:0] 
Apr  2 20:10:46 taher-desktop kernel: [13946.022939] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Apr  2 20:10:46 taher-desktop kernel: [13946.085872] [fglrx] Maximum main memory to use for locked dma buffers: 677 MBytes.
Apr  2 20:10:46 taher-desktop kernel: [13946.086812] [fglrx]   vendor: 1002 device: 9596 count: 1
Apr  2 20:10:46 taher-desktop kernel: [13946.088469] [fglrx] ioport: bar 1, base 0xde00, size: 0x100
Apr  2 20:10:46 taher-desktop kernel: [13946.090012] [fglrx] Driver built-in PAT support is enabled successfully
Apr  2 20:10:46 taher-desktop kernel: [13946.090078] [fglrx] module loaded - fglrx 8.59.2 [Mar 13 2009] with 1 minors
Apr  2 20:10:46 taher-desktop kernel: [13946.117172] [fglrx] AGP detected, AgpState   = 0x1f004a1b (hardware caps of chipset)
Apr  2 20:10:46 taher-desktop kernel: [13946.117185] [fglrx] [agp] enabling AGP with mode=0x1f004b1a
Apr  2 20:10:46 taher-desktop kernel: [13946.117197] agpgart-intel 0000:00:00.0: AGP 3.0 bridge
Apr  2 20:10:46 taher-desktop kernel: [13946.117234] agpgart-intel 0000:00:00.0: putting AGP V3 device into 8x mode
Apr  2 20:10:46 taher-desktop kernel: [13946.117304] fglrx_pci 0000:01:00.0: putting AGP V3 device into 8x mode
Apr  2 20:10:46 taher-desktop kernel: [13946.117333] [fglrx] AGP enabled,  AgpCommand = 0x1f004312 (selected caps)
Apr  2 20:10:50 taher-desktop kernel: [13949.537739] [fglrx] Setup AGP aperture
Apr  2 20:10:50 taher-desktop kernel: [13949.610252] [fglrx] Could not enable MSI; System prevented initialization
Apr  2 20:10:50 taher-desktop kernel: [13949.638692] [fglrx] Firegl kernel thread PID: 18196
Apr  2 20:10:50 taher-desktop kernel: [13949.653561] [fglrx] Gart cacheable size:373 M.
Apr  2 20:10:50 taher-desktop kernel: [13949.653584] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Apr  2 20:10:50 taher-desktop kernel: [13949.653590] [fglrx] Reserved FB block: Unshared offset:ff3a000, size:c6000 
Apr  2 20:10:50 taher-desktop kernel: [13949.653596] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
Apr  2 20:10:53 taher-desktop gdmgreeter[18207]: Gtk-WARNING: Unable to locate theme engine in module_path: "ubuntulooks", 
Apr  2 20:10:58 taher-desktop pulseaudio[18350]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr  2 20:10:58 taher-desktop pulseaudio[18352]: pid.c: Stale PID file, overwriting.
Apr  2 20:10:58 taher-desktop pulseaudio[18352]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr  2 20:10:58 taher-desktop pulseaudio[18352]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr  2 20:11:13 taher-desktop x-session-manager[18227]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Apr  2 20:11:13 taher-desktop pulseaudio[18352]: module-x11-xsmp.c: X11 session manager not running.
Apr  2 20:11:13 taher-desktop pulseaudio[18352]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
```

---

### Post by Mze on 2009-04-03
from what you posted, looks like you have fglrx 8.59.2:
> 090078] [fglrx] module loaded - fglrx 8.59.2 [Mar 13 2009] with 1 minors

fglrx 9.3 seems to work according this bug filing on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/314600")

---

### Post by jespdj on 2009-04-03
Please use a more descriptive topic title.

Something like "ATI Radeon HD 3650, help getting graphics driver to work" would have been much better than "PLEASE, could really use some help on this one!".

---

### Post by tmun52 on 2009-04-03
> **Mze said:**
> from what you posted, looks like you have fglrx 8.59.2:


fglrx 9.3 seems to work according this bug filing on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/314600")

That's weird, because I installed the proprietary drivers from the ATI website. If I did that, then how come the old drivers are loaded?

---

### Post by tmun52 on 2009-04-04
bump

---

