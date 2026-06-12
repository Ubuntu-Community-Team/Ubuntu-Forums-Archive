---
title: "X crash after nvidia auto-update"
date: 2009-01-07
forum: General Help
---

### Post by trpnblies7 on 2009-01-07
This morning I installed auto-updates for Intrepid, which included the new nvidia 177.82 drivers. Everything was fine after the update, but then out of nowhere X crashed on me. I shut my computer down manually and rebooted without a problem. I checked my syslog and noticed the following:

> Jan  7 08:12:35 brian-desktop console-kit-daemon[5033]: WARNING: Unable to activate console: No such device or address
Jan  7 08:12:35 brian-desktop gdm[5218]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jan  7 08:12:36 brian-desktop acpid: client connected from 16415[0:0]
Jan  7 08:12:36 brian-desktop kernel: [51529.978759] NVRM: API mismatch: the client has the version 177.82, but
Jan  7 08:12:36 brian-desktop kernel: [51529.978761] NVRM: this kernel module has the version 177.80.  Please
Jan  7 08:12:36 brian-desktop kernel: [51529.978761] NVRM: make sure that this kernel module and all NVIDIA driver
Jan  7 08:12:36 brian-desktop kernel: [51529.978762] NVRM: components have the same version.
Jan  7 08:12:39 brian-desktop acpid: client connected from 16428[0:0]
Jan  7 08:12:39 brian-desktop kernel: [51533.027018] NVRM: API mismatch: the client has the version 177.82, but
Jan  7 08:12:39 brian-desktop kernel: [51533.027019] NVRM: this kernel module has the version 177.80.  Please
Jan  7 08:12:39 brian-desktop kernel: [51533.027020] NVRM: make sure that this kernel module and all NVIDIA driver
Jan  7 08:12:39 brian-desktop kernel: [51533.027021] NVRM: components have the same version.
Jan  7 08:12:42 brian-desktop acpid: client connected from 16439[0:0]
Jan  7 08:12:42 brian-desktop kernel: [51536.074175] NVRM: API mismatch: the client has the version 177.82, but
Jan  7 08:12:42 brian-desktop kernel: [51536.074176] NVRM: this kernel module has the version 177.80.  Please
Jan  7 08:12:42 brian-desktop kernel: [51536.074177] NVRM: make sure that this kernel module and all NVIDIA driver
Jan  7 08:12:42 brian-desktop kernel: [51536.074178] NVRM: components have the same version.
Jan  7 08:12:42 brian-desktop gdm[5215]: CRITICAL: gdm_config_value_get_bool: assertion `value->type == GDM_CONFIG_VALUE_BOOL' failed
Jan  7 08:12:44 brian-desktop acpid: client connected from 16487[0:0]
Jan  7 08:12:44 brian-desktop kernel: [51537.820675] mtrr: base(0xf5000000) is not aligned on a size(0xe00000) boundary
Jan  7 08:12:53 brian-desktop init: tty4 main process (4378) killed by TERM signal
Jan  7 08:12:53 brian-desktop init: tty5 main process (4379) killed by TERM signal
Jan  7 08:12:53 brian-desktop init: tty2 main process (4385) killed by TERM signal
Jan  7 08:12:53 brian-desktop init: tty3 main process (4386) killed by TERM signal
Jan  7 08:12:53 brian-desktop init: tty6 main process (4387) killed by TERM signal
Jan  7 08:12:53 brian-desktop init: tty1 main process (5426) killed by TERM signal
Jan  7 08:13:02 brian-desktop acpid: client has disconnected
Jan  7 08:13:02 brian-desktop last message repeated 5 times
Jan  7 08:13:02 brian-desktop init: rc6 main process (16505) killed by TERM signal
Jan  7 08:13:05 brian-desktop kernel: [51558.851464] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jan  7 08:13:05 brian-desktop avahi-daemon[4784]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  7 08:13:05 brian-desktop avahi-daemon[4784]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.3.
Jan  7 08:13:05 brian-desktop avahi-daemon[4784]: Withdrawing address record for fe80::21e:8cff:fed6:3795 on wlan0.
Jan  7 08:13:05 brian-desktop avahi-daemon[4784]: Withdrawing address record for 192.168.2.3 on wlan0.
Jan  7 08:13:05 brian-desktop dhclient: receive_packet failed on wlan0: Network is down
Jan  7 08:13:06 brian-desktop avahi-daemon[4784]: Got SIGTERM, quitting.
Jan  7 08:13:07 brian-desktop exiting on signal 15

Does anyone know what this means or how I can fix it so it won't happen again? I don't know what any of that means other than it seems something with the drivers and kernel isn't agreeing.

---

### Post by trpnblies7 on 2009-01-07
Anyone?

---

### Post by trpnblies7 on 2009-01-07
Anyone know how to fix this?

---

### Post by CRIMPS on 2009-01-13
I am having a similar problem.  I noticed, once I installed the updates, that 3d effects were disabled.  So, I checked the Nvidia drivers.  I found that both the original Nvidia driver version 173 and the newest driver (version 177) were installed.  However, both were disabled.  So, I enabled the recommended version 177.  When I rebooted, X Server crashed.  I tried enabling the original version 173 as well.  I have had absolutely no luck in getting either one of the drivers enabled.  Each time I restart X I have to log into Ubuntu in "Low Graphics Mode".

While I find that working at 800x600 is better for my eyes, I would prefer to be a little more productive.  Even more frustrating is that I can't even go back to the original resolution that I worked on for about 3 days.

I again tried to "activate" the new Nvidia 177 driver.  However, the driver is never enabled.  I seem to be getting nowhere :(

---

### Post by trpnblies7 on 2009-01-13
Other than that one initial crash, I actually haven't had any other problems. I'd still like to know what caused it, though.

---

