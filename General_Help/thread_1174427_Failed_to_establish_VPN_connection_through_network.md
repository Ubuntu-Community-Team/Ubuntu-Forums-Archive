---
title: "Failed to establish VPN connection through network manager"
date: 2009-05-30
forum: General Help
---

### Post by rfu on 2009-05-30
I tried to use network manager to connect VPN and failed with the following log messages. I am using Ubuntu 9.04.
May 30 22:23:49 rfu-desktop NetworkManager: <info>  Login Banner: 
May 30 22:23:49 rfu-desktop NetworkManager: <info>  ----------------------------------------- 
May 30 22:23:49 rfu-desktop NetworkManager: <info>  (null) 
May 30 22:23:49 rfu-desktop NetworkManager: <info>  ----------------------------------------- 
May 30 22:23:50 rfu-desktop NetworkManager: nm_system_device_set_ip4_route: assertion `iface_idx >= 0' failed
May 30 22:23:50 rfu-desktop last message repeated 48 times
May 30 22:23:50 rfu-desktop NetworkManager: <info>  (tun0): writing resolv.conf to /sbin/resolvconf 
May 30 22:23:50 rfu-desktop NetworkManager: <info>  VPN connection 'VPN Toronto' (IP Config Get) complete. 
May 30 22:23:50 rfu-desktop NetworkManager: <WARN>  nm_system_replace_default_ip4_route_vpn(): (tun0): failed to set IPv4 default route: -19 
May 30 22:23:50 rfu-desktop NetworkManager: <info>  (tun0): writing resolv.conf to /sbin/resolvconf 
May 30 22:23:50 rfu-desktop NetworkManager: <info>  Policy set 'VPN Toronto' (tun0) as default for routing and DNS. 
May 30 22:23:50 rfu-desktop NetworkManager: <info>  VPN plugin state changed: 4 
May 30 22:23:50 rfu-desktop NetworkManager: <info>  VPN plugin failed: 1 
May 30 22:23:50 rfu-desktop NetworkManager: <info>  VPN plugin state changed: 6 
May 30 22:23:50 rfu-desktop NetworkManager: <info>  VPN plugin state change reason: 0 
May 30 22:23:50 rfu-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
May 30 22:23:50 rfu-desktop NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
May 30 22:23:50 rfu-desktop NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
May 30 22:23:50 rfu-desktop NetworkManager: <info>  (tun0): writing resolv.conf to /sbin/resolvconf 
May 30 22:23:51 rfu-desktop avahi-daemon[2559]: Withdrawing address record for 192.168.1.102 on eth0.
May 30 22:23:51 rfu-desktop avahi-daemon[2559]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.102.
May 30 22:23:51 rfu-desktop avahi-daemon[2559]: Interface eth0.IPv4 no longer relevant for mDNS.
May 30 22:23:51 rfu-desktop avahi-daemon[2559]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.102.
May 30 22:23:51 rfu-desktop avahi-daemon[2559]: New relevant interface eth0.IPv4 for mDNS.
May 30 22:23:51 rfu-desktop avahi-daemon[2559]: Registering new address record for 192.168.1.102 on eth0.IPv4.
May 30 22:23:52 rfu-desktop NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf 
May 30 22:23:52 rfu-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
May 30 22:23:52 rfu-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
May 30 22:23:52 rfu-desktop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
May 30 22:24:04 rfu-desktop NetworkManager: <debug> [1243736644.002114] ensure_killed(): waiting for vpn service pid 4565 to exit 
May 30 22:24:04 rfu-desktop NetworkManager: <debug> [1243736644.002338] ensure_killed(): vpn service pid 4565 cleaned up 
May 30 22:30:01 rfu-desktop /USR/SBIN/CRON[4658]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 30 22:40:01 rfu-desktop /USR/SBIN/CRON[4880]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

Is there anyone hit this problem before? If any suggestion or solution, please help me out. Thanks.

---

