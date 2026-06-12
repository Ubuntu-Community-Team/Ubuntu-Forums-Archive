---
title: "Failing to remote login via XDMCP"
date: 2008-09-04
forum: Desktop Environments
---

### Post by Scunge on 2008-09-04
I added to [**[color=blue]an existing thread[/color]**](http://ubuntuforums.org/showthread.php?t=826893) about not being able to use remote login via XDMCP, but have just realised that it's in the [[color=blue]Server Platforms[/color]](http://ubuntuforums.org/forumdisplay.php?f=339) forum!

So I've moved my posts to here in the hope that is the more the correct place and people better suited to helping will see it!

==========
*Posted 1 week ago*

Here's exactly the history of what I have done re remote logins:

Remote machine running Ubuntu Dapper Drake 6.06.2:

In "System > Administration > Login Window", on the "Remote" tab, I chose the style to be "Same as local". I restarted the machine.

Local machine running Ubuntu Dapper Drake 6.06.2:

From either the login screen, or from an existing login choosing "Quit > Switch User", I can go to the "Options" in the bottom-left of the screen and pick "Remote login via XDMCP". After a bit of flickering the list of machines on the network with available logins comes up, showing the remote machine above. Selecting that, after a bit more flickering, I get the wait cursor then the login screen of the remote machine.

By the way, "remote" and "local" relate purely to where I'm sitting; both machines are on an internal network without any firewalls between them that I have installed (the modem/router is the firewall to the internet). Both are assigned IP addresses using DHCP, but which never expire so they always have the same IP addresses. I don't know if that matters but "static IPs" were mentioned in the post [in that [other thread](http://ubuntuforums.org/showthread.php?t=826893)].

Anyway, last week, I set up a dual boot on the remote machine and installed Ubuntu Hardy Heron 8.04.1 from the alternative CD (as opposed to doing an upgrade to Dapper).

Now, doing the same as above, it gets as far as the selection of the remote machine, but after that there is a brief appearance of the wait cursor before it jumps back to the screensaver-login view of the local machine.

So, as mentioned [in that [other thread](http://ubuntuforums.org/showthread.php?t=826893)] and elsewhere, I logged into the remote machine and, under "System > Administration > Login Window", on the "Security" tab, I unticked "Security > Deny TCP connections to Xserver", and restarted the remote machine. No change.

Finally. I added the following line to the end of /etc/dhcp3/dhclient.conf:

```
prepend domain-name-servers 208.67.222.222 208.67.220.220
```

as advised [in that [other thread](http://ubuntuforums.org/showthread.php?t=826893)] and restarted the remote machine. Again, no change.

Have I missed anything from what is suggested [in that [other thread](http://ubuntuforums.org/showthread.php?t=826893)]? Is there anything else to try or options that I have omitted to set?

Thanks.

==========
*Posted today*

Ok. I have reinstalled a fresh Hardy in that dual-boot system with Dapper that I mention above.

In the Hardy installation, I went to **System > Administration > Login Window**, and in the **Remote** tab, set **Style** to *Same as local*. I also unticked the **Deny TCP connections to XServer** option, as suggested before. The computer was restarted.

It is worth noting that in the Dapper installation, that latter flag is still set, and there is some text on the window saying that XDMCP is not affected by that flag.

That machine I'm trying to log into is on 192.168.1.66, and is called *menhunter*. The machine I'm trying to log into it from is on 192.168.1.65, and is called *ferengi*, which is using Dapper.

I set the flags on both *menhunter*'s installations, and on *ferengi*'s installation, which puts lots of debug output to the system log, then tried to reach the login screen on each *menhunter* installation respectively, from *ferengi*. To Hardy, it failed as described above; to Dapper, it worked.

The system log from *ferengi* when connecting to Hardy on *menhunter* is, as far as I can see, the same (barring process IDs) as  that when connecting to Dapper, but the latter part of the Hardy try is here:
```
Sep  4 09:05:31 ferengi gdm[4347]: gdm_socket_handler: Accepting new connection fd 7
Sep  4 09:05:31 ferengi gdm[4347]: Handling user message: 'VERSION'
Sep  4 09:05:31 ferengi gdm[4347]: Handling user message: 'CONSOLE_SERVERS'
Sep  4 09:05:31 ferengi gdm[4347]: Handling user message: 'CLOSE'
Sep  4 09:05:32 ferengi gdm[23858]: slave_waitpid: done_waiting
Sep  4 09:05:32 ferengi gdm[23858]: Sending CHOOSERPID == 0 for slave 23858
Sep  4 09:05:32 ferengi gdm[4347]: Handling message: 'CHOOSERPID 23858 0'
Sep  4 09:05:32 ferengi gdm[4347]: Got CHOOSERPID == 0
Sep  4 09:05:32 ferengi gdm[23858]: Sending locally chosen host menhunter
Sep  4 09:05:32 ferengi gdm[23858]: Sending CHOSEN_LOCAL == <secret> for slave 23858
Sep  4 09:05:32 ferengi gdm[4347]: Handling message: 'CHOSEN_LOCAL 23858 menhunter'
Sep  4 09:05:32 ferengi gdm[4347]: Got CHOSEN_LOCAL == menhunter
Sep  4 09:05:32 ferengi gdm[23858]: gdm_slave_quick_exit: Will kill everything from the display
Sep  4 09:05:32 ferengi gdm[23858]: gdm_server_stop: Server for :21 going down!
Sep  4 09:05:32 ferengi gdm[23858]: gdm_server_stop: Killing server pid 23869
Sep  4 09:05:32 ferengi gdm[23858]: gdm_server_stop: Server pid 23869 dead
Sep  4 09:05:32 ferengi gdm[23858]: gdm_slave_quick_exit: Killed everything from the display
Sep  4 09:05:32 ferengi gdm[4347]: mainloop_sig_callback: Got signal 17
Sep  4 09:05:32 ferengi gdm[4347]: gdm_cleanup_children: child 23858 returned 2
Sep  4 09:05:32 ferengi gdm[4347]: gdm_child_action: In remanage
Sep  4 09:05:32 ferengi gdm[4347]: gdm_display_manage: Managing :21
Sep  4 09:05:32 ferengi gdm[4347]: loop check: last_start 1220515522, last_loop 1220515522, now: 1220515532, retry_count: 1
Sep  4 09:05:32 ferengi gdm[23897]: gdm_slave_start: Starting slave process for :21
Sep  4 09:05:32 ferengi gdm[23897]: gdm_slave_start: Loop Thingie
Sep  4 09:05:32 ferengi gdm[4347]: gdm_display_manage: Forked slave: 23897
Sep  4 09:05:32 ferengi gdm[23897]: gdm_slave_run: Sleeping 1 seconds before server start
Sep  4 09:05:33 ferengi gdm[23897]: Sending VT_NUM == -1 for slave 23897
Sep  4 09:05:33 ferengi gdm[4347]: Handling message: 'VT_NUM 23897 -1'
Sep  4 09:05:33 ferengi gdm[4347]: Got VT_NUM == -1
Sep  4 09:05:33 ferengi gdm[23897]: Sending DISP_NUM == 20 for slave 23897
Sep  4 09:05:33 ferengi gdm[4347]: Handling message: 'DISP_NUM 23897 20'
Sep  4 09:05:33 ferengi gdm[4347]: Got DISP_NUM == 20
Sep  4 09:05:33 ferengi gdm[23897]: gdm_server_start: :20
Sep  4 09:05:33 ferengi gdm[23897]: gdm_auth_secure_display: Setting up access for :20
Sep  4 09:05:33 ferengi gdm[23897]: gdm_auth_secure_display: Setting up access
Sep  4 09:05:33 ferengi gdm[23897]: gdm_auth_secure_display: Setting up access for :20 - 1 entries
Sep  4 09:05:33 ferengi gdm[23897]: Sending COOKIE == <secret> for slave 23897
Sep  4 09:05:33 ferengi gdm[4347]: Handling message: 'COOKIE 23897 2...'
Sep  4 09:05:33 ferengi gdm[4347]: Got COOKIE == <secret>
Sep  4 09:05:33 ferengi gdm[23897]: Sending AUTHFILE == <secret> for slave 23897
Sep  4 09:05:33 ferengi gdm[4347]: Handling message: 'AUTHFILE 23897 /var/lib/gdm/:20.Xauth'
Sep  4 09:05:33 ferengi gdm[4347]: Got AUTHFILE == /var/lib/gdm/:20.Xauth
Sep  4 09:05:33 ferengi gdm[23903]: gdm_server_spawn: '/usr/bin/X :20 -br -audit 0 -auth /var/lib/gdm/:20.Xauth -terminate -query menhunter vt8'
Sep  4 09:05:33 ferengi gdm[23897]: gdm_server_spawn: Forked server on pid 23903
Sep  4 09:05:33 ferengi gdm[23897]: do_server_wait: Before mainloop waiting for server
Sep  4 09:05:33 ferengi gdm[23897]: gdm_server_start: After mainloop waiting for server
Sep  4 09:05:33 ferengi gdm[23897]: gdm_server_start: Completed :20!
Sep  4 09:05:33 ferengi gdm[23897]: Sending FLEXI_OK == 0 for slave 23897
Sep  4 09:05:33 ferengi gdm[4347]: Handling message: 'FLEXI_OK 23897 0'
Sep  4 09:05:33 ferengi gdm[4347]: Got FLEXI_OK
Sep  4 09:05:33 ferengi gdm[23897]: Sending VT_NUM == 8 for slave 23897
Sep  4 09:05:33 ferengi gdm[4347]: Handling message: 'VT_NUM 23897 8'
Sep  4 09:05:33 ferengi gdm[4347]: Got VT_NUM == 8
Sep  4 09:05:33 ferengi gdm[23897]: Sending XPID == 23903 for slave 23897
Sep  4 09:05:33 ferengi gdm[4347]: Handling message: 'XPID 23897 23903'
Sep  4 09:05:33 ferengi gdm[4347]: Got XPID == 23903
Sep  4 09:05:33 ferengi gdm[23897]: gdm_slave_run: Opening display :20
Sep  4 09:05:35 ferengi gdm[4347]: Handling message: 'START_NEXT_LOCAL'
Sep  4 09:05:36 ferengi gdm[4347]: gdm_socket_handler: Accepting new connection fd 7
Sep  4 09:05:36 ferengi gdm[4347]: Handling user message: 'VERSION'
Sep  4 09:05:36 ferengi gdm[4347]: Handling user message: 'CONSOLE_SERVERS'
Sep  4 09:05:36 ferengi gdm[4347]: Handling user message: 'CLOSE'
Sep  4 09:05:37 ferengi gdm[4347]: Handling message: 'XPID 23897 0'
Sep  4 09:05:37 ferengi gdm[4347]: Got XPID == 0
Sep  4 09:05:37 ferengi gdm[23897]: gdm_slave_quick_exit: Will kill everything from the display
Sep  4 09:05:37 ferengi gdm[23897]: gdm_slave_quick_exit: Killed everything from the display
Sep  4 09:05:37 ferengi gdm[4347]: mainloop_sig_callback: Got signal 17
Sep  4 09:05:37 ferengi gdm[4347]: gdm_cleanup_children: child 23897 returned 2
Sep  4 09:05:37 ferengi gdm[4347]: gdm_child_action: In remanage
Sep  4 09:05:37 ferengi gdm[4347]: gdm_display_unmanage: Stopping :20 (slave pid: 0)
Sep  4 09:05:37 ferengi gdm[4347]: gdm_display_dispose: Disposing :20
Sep  4 09:05:37 ferengi gdm[4347]: gdm_display_unmanage: Display stopped

```

The logs on *menhunter* are quite different from each other, perhaps due to a revamp of the debug messages than anything else, so here's them both in full.

The failing Hardy version:
```
Sep  4 09:05:29 menhunter gdm[5237]: DEBUG: decode_packet: GIOCondition 1 
Sep  4 09:05:29 menhunter gdm[5237]: DEBUG: XDMCP: Received opcode BROADCAST_QUERY from client ::ffff:192.168.1.65 : 32795 
Sep  4 09:05:29 menhunter gdm[5237]: DEBUG: gdm_xdmcp_host_allow: client->hostname is 192.168.1.65  
Sep  4 09:05:29 menhunter gdm[5237]: DEBUG: XDMCP: Sending WILLING to ::ffff:192.168.1.65 
Sep  4 09:05:31 menhunter gdm[5237]: DEBUG: decode_packet: GIOCondition 1 
Sep  4 09:05:31 menhunter gdm[5237]: DEBUG: XDMCP: Received opcode BROADCAST_QUERY from client ::ffff:192.168.1.65 : 32795 
Sep  4 09:05:31 menhunter gdm[5237]: DEBUG: gdm_xdmcp_host_allow: client->hostname is 192.168.1.65  
Sep  4 09:05:31 menhunter gdm[5237]: DEBUG: XDMCP: Sending WILLING to ::ffff:192.168.1.65 
Sep  4 09:05:33 menhunter gdm[5237]: DEBUG: decode_packet: GIOCondition 1 
Sep  4 09:05:33 menhunter gdm[5237]: DEBUG: XDMCP: Received opcode QUERY from client ::ffff:192.168.1.65 : 32795 
Sep  4 09:05:33 menhunter gdm[5237]: DEBUG: gdm_xdmcp_host_allow: client->hostname is 192.168.1.65  
Sep  4 09:05:33 menhunter gdm[5237]: DEBUG: XDMCP: Sending WILLING to ::ffff:192.168.1.65 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: decode_packet: GIOCondition 1 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: XDMCP: Received opcode REQUEST from client ::ffff:192.168.1.65 : 32795 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_xdmcp_handle_request: Got REQUEST from ::ffff:192.168.1.65 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_xdmcp_host_allow: client->hostname is 192.168.1.65  
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_xdmcp_handle_request: xdmcp_pending=0, MaxPending=4, xdmcp_sessions=0, MaxSessions=16, ManufacturerID= 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_xdmcp_display_dispose_check (192.168.1.65:20) 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Attempting to parse key string: security/AllowRemoteAutoLogin=false 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_auth_secure_display: Setting up access for 192.168.1.65:20 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/gdm 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_auth_secure_display: Setting up access 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Attempting to parse key string: debug/Enable=false 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_auth_secure_display: Setting up access for 192.168.1.65:20 - 1 entries 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_xdmcp_display_alloc: display=192.168.1.65:20, session id=1131282331, xdmcp_pending=1 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: XDMCP: Sending ACCEPT to ::ffff:192.168.1.65 with SessionID=1131282331 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: decode_packet: GIOCondition 1 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: XDMCP: Received opcode MANAGE from client ::ffff:192.168.1.65 : 32795 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_xdmcp_handle_manage: Got MANAGE from ::ffff:192.168.1.65 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_xdmcp_host_allow: client->hostname is 192.168.1.65  
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Attempting to parse key string: debug/Enable=false 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_xdmcp-handle_manage: Got display=20, SessionID=1131282331 Class=MIT-unspecified from MIT-unspecified1.65 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_xdmcp_handle_manage: Looked up 192.168.1.65:20 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_choose_indirect_lookup: Host ::ffff:192.168.1.65 not found 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_forward_query_lookup: Host ::ffff:192.168.1.65 not found 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_display_manage: Managing 192.168.1.65:20 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: loop check: last_start 0, last_loop 0, now: 1220515537, retry_count: 0 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Resetting counts for loop of death detection 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Forking slave process 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: Attempting to parse key string: xdmcp/PingIntervalSeconds=15 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: gdm_slave_start: Starting slave process for 192.168.1.65:20 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: gdm_slave_start: Loop Thingie 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: Attempting to parse key string: xdmcp/PingIntervalSeconds=15 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: Attempting to parse key string: daemon/AutomaticLogin= 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: Attempting to parse key string: daemon/TimedLogin= 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: Attempting to parse key string: daemon/AutomaticLoginEnable=false 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: Attempting to parse key string: daemon/TimedLoginEnable=false 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: gdm_slave_run: Opening display 192.168.1.65:20 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_display_manage: Forked slave: 5992 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: gdm_slave_greeter: Running greeter on 192.168.1.65:20 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: Attempting to parse key string: daemon/DisplayInitDir=/etc/gdm/Init 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: Forking extra process: /etc/gdm/Init/Default 
Sep  4 09:05:37 menhunter gdm[5995]: DEBUG: Attempting to parse key string: xdmcp/Enable=false 
Sep  4 09:05:37 menhunter gdm[5995]: DEBUG: Attempting to parse key string: daemon/User=gdm 
Sep  4 09:05:37 menhunter gdm[5995]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/gdm 
Sep  4 09:05:37 menhunter gdm[5995]: DEBUG: Attempting to parse key string: daemon/RootPath=/sbin:/usr/sbin:/bin:/usr/bin 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: Attempting to parse key string: daemon/RemoteGreeter=/usr/lib/gdm/gdmlogin 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: Forking greeter process: /usr/lib/gdm/gdmgreeter 
Sep  4 09:05:37 menhunter gdm[6000]: DEBUG: Attempting to parse key string: daemon/User=gdm 
Sep  4 09:05:37 menhunter gdm[6000]: DEBUG: Attempting to parse key string: daemon/DefaultPath=/bin:/usr/bin 
Sep  4 09:05:37 menhunter gdm[6000]: DEBUG: Attempting to parse key string: debug/Gestures=false 
Sep  4 09:05:37 menhunter gdm[6000]: DEBUG: Attempting to parse key string: daemon/GtkModulesList= 
Sep  4 09:05:37 menhunter gdm[6000]: DEBUG: Attempting to parse key string: daemon/AddGtkModules=false 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: gdm_slave_greeter: Greeter on pid 6000 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: Sending GREETPID == 6000 for slave 5992 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Attempting to parse key string: debug/Enable=false 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Handling message: 'GREETPID 5992 6000' 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Got GREETPID == 6000 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_socket_handler: Accepting new connection fd 10 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Handling user message: 'VERSION' 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Handling user message: 'GET_CONFIG daemon/AddGtkModules 192.168.1.65:20' 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Handling GET_CONFIG: daemon/AddGtkModules for display 192.168.1.65:20 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Looking up per display value for daemon/AddGtkModules 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Attempting to parse key string: daemon/AddGtkModules 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Looking up key: daemon/AddGtkModules 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Attempting to parse key string: daemon/AddGtkModules 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: Handling user message: 'CLOSE' 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: term_quit: Final cleanup 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: gdm_slave_quick_exit: Will kill everything from the display 
Sep  4 09:05:37 menhunter gdm[5992]: DEBUG: gdm_slave_quick_exit: Killed everything from the display 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: mainloop_sig_callback: Got signal 17 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_cleanup_children: child 5992 returned 65 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_child_action: In remanage 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_display_unmanage: Stopping 192.168.1.65:20 (slave pid: 0) 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_display_dispose: Disposing 192.168.1.65:20 
Sep  4 09:05:37 menhunter gdm[5237]: DEBUG: gdm_display_unmanage: Display stopped

```

And the working Dapper version:
```
Sep  4 09:42:28 menhunter gdm[4391]: gdm_xdmcp_decode: Received opcode BROADCAST_QUERY from client 192.168.1.65
Sep  4 09:42:28 menhunter gdm[4391]: gdm_xdmcp_handle_query: Opcode 1 from 192.168.1.65
Sep  4 09:42:28 menhunter gdm[4391]: gdm_xdmcp_host_allow: client->hostname is ferengi 
Sep  4 09:42:28 menhunter gdm[4391]: gdm_xdmcp_send_willing: Sending WILLING to 192.168.1.65
Sep  4 09:42:30 menhunter gdm[4391]: gdm_xdmcp_decode: Received opcode BROADCAST_QUERY from client 192.168.1.65
Sep  4 09:42:30 menhunter gdm[4391]: gdm_xdmcp_handle_query: Opcode 1 from 192.168.1.65
Sep  4 09:42:30 menhunter gdm[4391]: gdm_xdmcp_host_allow: client->hostname is ferengi 
Sep  4 09:42:30 menhunter gdm[4391]: gdm_xdmcp_send_willing: Sending WILLING to 192.168.1.65
Sep  4 09:42:32 menhunter gdm[4391]: gdm_xdmcp_decode: Received opcode QUERY from client 192.168.1.65
Sep  4 09:42:32 menhunter gdm[4391]: gdm_xdmcp_handle_query: Opcode 2 from 192.168.1.65
Sep  4 09:42:32 menhunter gdm[4391]: gdm_xdmcp_host_allow: client->hostname is ferengi 
Sep  4 09:42:32 menhunter gdm[4391]: gdm_xdmcp_send_willing: Sending WILLING to 192.168.1.65
Sep  4 09:42:36 menhunter gdm[4391]: gdm_xdmcp_decode: Received opcode REQUEST from client 192.168.1.65
Sep  4 09:42:36 menhunter gdm[4391]: gdm_xdmcp_handle_request: Got REQUEST from 192.168.1.65
Sep  4 09:42:36 menhunter gdm[4391]: gdm_xdmcp_host_allow: client->hostname is ferengi 
Sep  4 09:42:36 menhunter gdm[4391]: gdm_xdmcp_handle_request: xdmcp_pending=0, MaxPending=4, xdmcp_sessions=0, MaxSessions=16, ManufacturerID=
Sep  4 09:42:36 menhunter gdm[4391]: gdm_xdmcp_display_dispose_check (ferengi:20)
Sep  4 09:42:36 menhunter gdm[4391]: gdm_auth_secure_display: Setting up access for ferengi:20
Sep  4 09:42:36 menhunter gdm[4391]: gdm_auth_secure_display: Setting up access
Sep  4 09:42:36 menhunter gdm[4391]: gdm_auth_secure_display: Setting up access for ferengi:20 - 1 entries
Sep  4 09:42:36 menhunter gdm[4391]: gdm_xdmcp_display_alloc: display=ferengi:20, session id=1538752616, xdmcp_pending=1 
Sep  4 09:42:36 menhunter gdm[4391]: gdm_xdmcp_send_accept: Sending ACCEPT to 192.168.1.65 with SessionID=1538752616
Sep  4 09:42:36 menhunter gdm[4391]: gdm_xdmcp_decode: Received opcode MANAGE from client 192.168.1.65
Sep  4 09:42:36 menhunter gdm[4391]: gdm_xdmcp_handle_manage: Got MANAGE from 192.168.1.65
Sep  4 09:42:36 menhunter gdm[4391]: gdm_xdmcp_host_allow: client->hostname is ferengi 
Sep  4 09:42:36 menhunter gdm[4391]: gdm_xdmcp_handle_manage: Got Display=20, SessionID=1538752616 Class=MIT-unspecified from 192.168.1.65
Sep  4 09:42:36 menhunter gdm[4391]: gdm_xdmcp_handle_manage: Looked up ferengi:20
Sep  4 09:42:36 menhunter gdm[4391]: gdm_choose_indirect_lookup: Host 192.168.1.65 not found
Sep  4 09:42:36 menhunter gdm[4391]: gdm_forward_query_lookup: Host 192.168.1.65 not found
Sep  4 09:42:36 menhunter gdm[4391]: gdm_display_manage: Managing ferengi:20
Sep  4 09:42:36 menhunter gdm[4391]: loop check: last_start 0, last_loop 0, now: 1220517756, retry_count: 0
Sep  4 09:42:36 menhunter gdm[4391]: Resetting counts for loop of death detection
Sep  4 09:42:36 menhunter gdm[5853]: gdm_slave_start: Starting slave process for ferengi:20
Sep  4 09:42:36 menhunter gdm[5853]: gdm_slave_start: Loop Thingie
Sep  4 09:42:36 menhunter gdm[4391]: gdm_display_manage: Forked slave: 5853
Sep  4 09:42:36 menhunter gdm[5853]: gdm_slave_run: Opening display ferengi:20
Sep  4 09:42:36 menhunter gdm[5853]: gdm_slave_greeter: Running greeter on ferengi:20
Sep  4 09:42:36 menhunter gdm[5853]: gdm_slave_greeter: Greeter on pid 5859
Sep  4 09:42:36 menhunter gdm[5853]: Sending GREETPID == 5859 for slave 5853
Sep  4 09:42:36 menhunter gdm[4391]: Handling message: 'GREETPID 5853 5859'
Sep  4 09:42:36 menhunter gdm[4391]: Got GREETPID == 5859
Sep  4 09:42:36 menhunter gdm[4391]: gdm_socket_handler: Accepting new connection fd 8
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'VERSION'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG debug/Enable ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/GraphicalTheme ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/GraphicalTheme ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK Human'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/GraphicalThemes ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/GraphicalThemes ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK circles'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/GraphicalThemeDir ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/GraphicalThemeDir ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /usr/share/gdm/themes/'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG gui/GtkRC ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG gui/GtkRC ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /usr/share/themes/Default/gtk-2.0/gtkrc'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG gui/GtkTheme ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG gui/GtkTheme ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK Human'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/Include ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/Include ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK '
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/Exclude ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/Exclude ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK bin,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,gdm,postgres,pvm,rpm'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/SessionDesktopDir ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/SessionDesktopDir ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /etc/X11/sessions/:/etc/dm/Sessions/:/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/LocaleFile ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/LocaleFile ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /etc/gdm/locale.conf'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/HaltCommand ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/HaltCommand ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /sbin/shutdown -h now "Halted from gdm menu."'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/RebootCommand ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/RebootCommand ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /sbin/shutdown -r now "Rebooted from gdm menu."'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/SuspendCommand ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/SuspendCommand ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /usr/sbin/pmi action sleep'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/Configurator ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/Configurator ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /usr/sbin/gdmsetup --disable-sound --disable-crash-dialog'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/InfoMsgFile ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/InfoMsgFile ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK '
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/InfoMsgFont ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/InfoMsgFont ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK '
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/TimedLogin ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/TimedLogin ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK '
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/GraphicalThemedColor ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/GraphicalThemedColor ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK #2b0600'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/BackgroundColor ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/BackgroundColor ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK #2b0600'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/DefaultFace ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/DefaultFace ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /usr/share/pixmaps/nobody.png'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/DefaultSession ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/DefaultSession ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK default.desktop'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/SoundProgram ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/SoundProgram ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /usr/lib/gdmplay'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/SoundOnLoginFile ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/SoundOnLoginFile ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /usr/share/sounds/question.wav'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/Use24Clock ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/Use24Clock ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK auto'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/Welcome ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/Welcome ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK Welcome'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/RemoteWelcome ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/RemoteWelcome ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK Welcome to %n'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/XineramaScreen ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/XineramaScreen ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK 0'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/TimedLoginDelay ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/TimedLoginDelay ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK 30'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/FlexiReapDelayMinutes ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/FlexiReapDelayMinutes ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK 5'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG gui/MaxIconHeight ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG gui/MaxIconHeight ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK 128'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG gui/MaxIconWidth ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG gui/MaxIconWidth ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK 128'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/MinimalUID ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/MinimalUID ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK 1000'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/UseCirclesInEntry ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/UseCirclesInEntry ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK true'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/UseInvisibleInEntry ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/UseInvisibleInEntry ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK false'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/ShowXtermFailsafeSession ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/ShowXtermFailsafeSession ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK true'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/ShowGnomeFailsafeSession ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/ShowGnomeFailsafeSession ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK true'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/IncludeAll ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/IncludeAll ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK true'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/SystemMenu ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/SystemMenu ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK true'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/ConfigAvailable ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/ConfigAvailable ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK false'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/ChooserButton ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/ChooserButton ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK true'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/TimedLoginEnable ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/TimedLoginEnable ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK false'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/GraphicalThemeRand ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/GraphicalThemeRand ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK false'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/ShowLastSession ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/ShowLastSession ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK true'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG security/AllowRoot ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG security/AllowRoot ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK false'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG security/AllowRemoteRoot ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG security/AllowRemoteRoot ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK false'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/SoundOnLogin ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/SoundOnLogin ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK true'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/DefaultWelcome ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/DefaultWelcome ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK true'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/DefaultRemoteWelcome ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/DefaultRemoteWelcome ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK true'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/PidFile ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/PidFile ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /var/run/gdm.pid'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG greeter/PreFetchProgram ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG greeter/PreFetchProgram ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK '
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'CLOSE'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'CLOSE'
Sep  4 09:42:36 menhunter gdm[4391]: gdm_socket_handler: Accepting new connection fd 8
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'VERSION'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'VERSION'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'GDM 2.14.10'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'GET_CONFIG daemon/HibernateCommand ferengi:20'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'GET_CONFIG daemon/HibernateCommand ferengi:20'
Sep  4 09:42:36 menhunter gdmgreeter[5859]:   Got response: 'OK /usr/sbin/pmi action hibernate'
Sep  4 09:42:36 menhunter gdmgreeter[5859]: Sending command: 'CLOSE'
Sep  4 09:42:36 menhunter gdm[4391]: Handling user message: 'CLOSE'
Sep  4 09:42:36 menhunter gdm[5853]: gdm_slave_wait_for_login: In loop
Sep  4 09:42:44 menhunter gdm[5853]: term_quit: Final cleanup
Sep  4 09:42:44 menhunter gdm[5853]: gdm_slave_quick_exit: Will kill everything from the display
Sep  4 09:42:44 menhunter gdm[5853]: Running gdm_verify_cleanup and pamh != NULL
Sep  4 09:42:44 menhunter gdm[5853]: gdm_slave_quick_exit: Killed everything from the display
Sep  4 09:42:44 menhunter gdm[4391]: mainloop_sig_callback: Got signal 17
Sep  4 09:42:44 menhunter gdm[4391]: gdm_cleanup_children: child 5853 returned 2
Sep  4 09:42:44 menhunter gdm[4391]: gdm_child_action: In remanage
Sep  4 09:42:44 menhunter gdm[4391]: gdm_display_unmanage: Stopping ferengi:20 (slave pid: 0)
Sep  4 09:42:44 menhunter gdm[4391]: gdm_display_dispose: Disposing ferengi:20
Sep  4 09:42:44 menhunter gdm[4391]: gdm_display_unmanage: Display stopped
Sep  4 09:42:46 menhunter gdm[4391]: gdm_socket_handler: Accepting new connection fd 8
Sep  4 09:42:46 menhunter gdm[4391]: Handling user message: 'VERSION'
Sep  4 09:42:46 menhunter gdm[4391]: Handling user message: 'CONSOLE_SERVERS'
Sep  4 09:42:46 menhunter gdm[4391]: Handling user message: 'CLOSE'
Sep  4 09:42:51 menhunter gdm[4391]: gdm_socket_handler: Accepting new connection fd 8
Sep  4 09:42:51 menhunter gdm[4391]: Handling user message: 'VERSION'
Sep  4 09:42:51 menhunter gdm[4391]: Handling user message: 'CONSOLE_SERVERS'
Sep  4 09:42:51 menhunter gdm[4391]: Handling user message: 'CLOSE'

```

Can anyone see why the Hardy one is failing, and, more important, what to change in the Hardy installation to make it work?

---

