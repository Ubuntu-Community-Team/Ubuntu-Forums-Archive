---
title: "Ubuntu hangs on restart"
date: 2008-06-26
forum: Desktop Environments
---

### Post by jkmuller on 2008-06-26
When I try to restart, everything but my desktop wallpaper disappears, but it hangs at that point seemingly indefinitely. Ctrl+alt+backspace sometimes lets me restart, sometimes I actually have to remove my laptop battery. Here's my syslog contents:

Jun 26 11:28:31 joseph-laptop syslogd 1.5.0#1ubuntu1: restart.
Jun 26 11:28:31 joseph-laptop anacron[5330]: Job `cron.daily' terminated
Jun 26 11:28:31 joseph-laptop anacron[5330]: Normal exit (1 job run)
Jun 26 11:28:37 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:28:39 joseph-laptop last message repeated 6 times
Jun 26 11:28:40 joseph-laptop scim-bridge: An invalid char is given at scim_bridge_string_to_uint (): -
Jun 26 11:28:40 joseph-laptop scim-bridge: Invalid message: Close the connection.
Jun 26 11:40:59 joseph-laptop -- MARK --
Jun 26 11:49:12 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:49:13 joseph-laptop last message repeated 2 times
Jun 26 11:49:14 joseph-laptop scim-bridge: An invalid char is given at scim_bridge_string_to_uint (): -
Jun 26 11:49:14 joseph-laptop scim-bridge: Invalid message: Close the connection.
Jun 26 11:50:06 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:50:07 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:50:10 joseph-laptop scim-bridge: An invalid char is given at scim_bridge_string_to_uint (): -
Jun 26 11:50:10 joseph-laptop scim-bridge: Invalid message: Close the connection.
Jun 26 11:50:12 joseph-laptop pulseaudio[5664]: shm.c: shm_open() failed: No such file or directory
Jun 26 11:50:12 joseph-laptop pulseaudio[5664]: pstream.c: Failed to import memory block.
Jun 26 11:50:15 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:50:50 joseph-laptop last message repeated 2 times
Jun 26 11:50:56 joseph-laptop scim-bridge: An invalid char is given at scim_bridge_string_to_uint (): -
Jun 26 11:50:56 joseph-laptop scim-bridge: Invalid message: Close the connection.
Jun 26 11:50:56 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:50:58 joseph-laptop last message repeated 2 times
Jun 26 11:50:58 joseph-laptop scim-bridge: An invalid char is given at scim_bridge_string_to_uint (): -
Jun 26 11:50:58 joseph-laptop scim-bridge: Invalid message: Close the connection.
Jun 26 11:50:59 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:50:59 joseph-laptop scim-bridge: An invalid char is given at scim_bridge_string_to_uint (): -
Jun 26 11:50:59 joseph-laptop scim-bridge: Invalid message: Close the connection.
Jun 26 11:51:02 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:51:03 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:52:52 joseph-laptop last message repeated 38 times
Jun 26 11:52:54 joseph-laptop scim-bridge: An invalid char is given at scim_bridge_string_to_uint (): -
Jun 26 11:52:54 joseph-laptop scim-bridge: Invalid message: Close the connection.
Jun 26 11:54:15 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:54:16 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:54:21 joseph-laptop scim-bridge: An invalid char is given at scim_bridge_string_to_uint (): -
Jun 26 11:54:21 joseph-laptop scim-bridge: Invalid message: Close the connection.
Jun 26 11:54:40 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:55:24 joseph-laptop last message repeated 14 times
Jun 26 11:55:25 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:55:28 joseph-laptop scim-bridge: An invalid char is given at scim_bridge_string_to_uint (): -
Jun 26 11:55:28 joseph-laptop scim-bridge: Invalid message: Close the connection.
Jun 26 11:58:47 joseph-laptop scim-bridge: No such IMContext
Jun 26 11:58:50 joseph-laptop scim-bridge: An invalid char is given at scim_bridge_string_to_uint (): -
Jun 26 11:58:50 joseph-laptop scim-bridge: Invalid message: Close the connection.
Jun 26 12:00:08 joseph-laptop scim-bridge: No such IMContext
Jun 26 12:00:08 joseph-laptop scim-bridge: No such IMContext
Jun 26 12:05:44 joseph-laptop scim-bridge: No such IMContext
Jun 26 12:06:49 joseph-laptop last message repeated 7 times
Jun 26 12:06:51 joseph-laptop scim-bridge: No such IMContext
Jun 26 12:06:52 joseph-laptop scim-bridge: An invalid char is given at scim_bridge_string_to_uint (): -
Jun 26 12:06:52 joseph-laptop scim-bridge: Invalid message: Close the connection.
Jun 26 12:08:44 joseph-laptop scim-bridge: No such IMContext
Jun 26 12:09:08 joseph-laptop last message repeated 9 times
Jun 26 12:10:46 joseph-laptop scim-bridge: Cleanup, done. Exitting...
Jun 26 12:17:02 joseph-laptop /USR/SBIN/CRON[9513]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 26 12:22:35 joseph-laptop gdm[5301]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jun 26 12:22:35 joseph-laptop init: tty4 main process (4458) killed by TERM signal
Jun 26 12:22:35 joseph-laptop init: tty5 main process (4459) killed by TERM signal
Jun 26 12:22:35 joseph-laptop init: tty2 main process (4463) killed by TERM signal
Jun 26 12:22:35 joseph-laptop init: tty3 main process (4464) killed by TERM signal
Jun 26 12:22:35 joseph-laptop init: tty6 main process (4466) killed by TERM signal
Jun 26 12:22:35 joseph-laptop init: tty1 main process (5497) killed by TERM signal
Jun 26 12:22:36 joseph-laptop avahi-daemon[4880]: Got SIGTERM, quitting.
Jun 26 12:22:36 joseph-laptop avahi-daemon[4880]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.0.4.
Jun 26 12:22:36 joseph-laptop gdm[955]: CRITICAL: gdm_connection_close: assertion `conn != NULL' failed 
Jun 26 12:22:36 joseph-laptop last message repeated 2 times
Jun 26 12:22:36 joseph-laptop gdm[955]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 26 12:22:36 joseph-laptop gdm[955]: WARNING: Request for invalid configuration key xdmcp/PingIntervalSeconds=15 
Jun 26 12:22:36 joseph-laptop gdm[955]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 26 12:22:36 joseph-laptop gdm[955]: WARNING: Request for invalid configuration key xdmcp/PingIntervalSeconds=15 
Jun 26 12:22:37 joseph-laptop kernel: [ 2655.913727] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jun 26 12:22:37 joseph-laptop gdm[955]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 26 12:22:37 joseph-laptop gdm[955]: WARNING: Request for invalid configuration key daemon/ServAuthDir=/var/lib/gdm 
Jun 26 12:22:37 joseph-laptop gdm[955]: WARNING: gdm_slave_send: Can't open fifo! 
Jun 26 12:22:37 joseph-laptop gdm[955]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 26 12:22:37 joseph-laptop gdm[955]: WARNING: Request for invalid configuration key daemon/ServAuthDir=/var/lib/gdm 
Jun 26 12:22:37 joseph-laptop gdm[955]: WARNING: gdm_auth_secure_display: Cannot safely open  
Jun 26 12:22:37 joseph-laptop gdm[955]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 26 12:22:37 joseph-laptop gdm[955]: WARNING: Request for invalid configuration key daemon/ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh 
Jun 26 12:22:37 joseph-laptop gdm[955]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Jun 26 12:22:37 joseph-laptop gdm[955]: WARNING: Request for invalid configuration key daemon/ConsoleNotify=true 
Jun 26 12:22:39 joseph-laptop exiting on signal 15
Jun 26 12:23:32 joseph-laptop syslogd 1.5.0#1ubuntu1: restart.
Jun 26 12:23:32 joseph-laptop kernel: Inspecting /boot/System.map-2.6.24-19-generic

---

### Post by VMC on 2008-06-26
"scim-bridge: No such IMContext"

What exactly is that. Some piece of hardware. Some kind of bridge. It looks to be the culprit.

---

### Post by jkmuller on 2008-06-26
Seems like a piece of software to me: [http://www.scim-im.org/projects/scim_bridge](http://www.scim-im.org/projects/scim_bridge)

I'm not sure what to make of that though. There are a lot of potential culprits in the log, but I think these two lines are important.

Jun 26 12:17:02 joseph-laptop /USR/SBIN/CRON[9513]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
Jun 26 12:22:35 joseph-laptop gdm[5301]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 

I think the time difference there is the time between when Ubuntu was hanging after trying to restart and when I hit ctrl+alt+backspace. I don't have enough understanding of linux to know what the problem is though. Any ideas?

---

### Post by vincent orange on 2009-05-24
If my memory serves me right scim bridge is a language input function where you can type in languages that use script that is different from English.

---

