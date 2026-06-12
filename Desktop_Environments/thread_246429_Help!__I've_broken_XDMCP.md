---
title: "Help!  I've broken XDMCP"
date: 2006-08-29
forum: Desktop Environments
---

### Post by markius on 2006-08-29
Hi

I've been using Xming on my Windows laptop to connect to Ubuntu via XDMCP. This was all working well until I lost my network connection in the middle of a session. 

Now, whenever I try to connect using Xming I just get the blank X server canvas.

I can see that when I try to connect there is a hostname.Xauth file created in /var/lib/gdm/ so it seems as though the connection is at least partially working. I've also been able to start xeyes from inside a PuTTY/Xming SSH session.

I've tried restarting both machines but this hasn't fixed it.

I'm very new to linux and Ubuntu and don't know where to start looking to troubleshoot this problem.

Any advice would be greatly apreciated.

Thanks in advance

Mark

---

### Post by markius on 2006-08-30
Hi.  Can anyone give me any pointers on this?

I don't want to have to reinstall from scratch just for this one issue.

Thanks

---

### Post by markius on 2006-09-01
Can anyone offer any help with this problem?  It's driving me nuts and I feel all alone! ](*,) 

Below are two excerpts from /var/log/daemon.log
The first is a sucessful connection (from a different machine)
The second is a failed connect (from my laptop)
I've tried both Cygwin/X and Xming on the laptop.  No firewall is configured on the laptop.  My instinct tells me it's not the laptop that's at fault.

EDIT: I've discovered that if I change the IP address of the problem laptop then I can connect.  Ubuntu/gdm is definately blocking this particular IP address.  The question is why?

Mark

**LOG 1 - Sucessful XDMCP connection from machine A**
```

Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_decode: Received opcode BROADCAST_QUERY from client 192.168.0.12
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_handle_query: Opcode 1 from 192.168.0.12
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_host_allow: client->hostname is lisa.librium.local 
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_send_willing: Sending WILLING to 192.168.0.12
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_decode: Received opcode REQUEST from client 192.168.0.12
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_handle_request: Got REQUEST from 192.168.0.12
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_host_allow: client->hostname is lisa.librium.local 
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_handle_request: xdmcp_pending=0, MaxPending=4, xdmcp_sessions=0, MaxSessions=16, ManufacturerID=
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_display_dispose_check (lisa.librium.local:0)
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_auth_secure_display: Setting up access for lisa.librium.local:0
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_auth_secure_display: Setting up access
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_auth_secure_display: Setting up access for lisa.librium.local:0 - 1 entries
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_display_alloc: display=lisa.librium.local:0, session id=2104627135, xdmcp_pending=1 
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_send_accept: Sending ACCEPT to 192.168.0.12 with SessionID=2104627135
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_decode: Received opcode MANAGE from client 192.168.0.12
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_handle_manage: Got MANAGE from 192.168.0.12
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_host_allow: client->hostname is lisa.librium.local 
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_handle_manage: Got Display=0, SessionID=2104627135 Class=MIT-unspecified from 192.168.0.12
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_xdmcp_handle_manage: Looked up lisa.librium.local:0
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_choose_indirect_lookup: Host 192.168.0.12 not found
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_forward_query_lookup: Host 192.168.0.12 not found
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_display_manage: Managing lisa.librium.local:0
Sep  1 21:45:29 homer-ubuntu gdm[4368]: loop check: last_start 0, last_loop 0, now: 1157143529, retry_count: 0
Sep  1 21:45:29 homer-ubuntu gdm[4368]: Resetting counts for loop of death detection
Sep  1 21:45:29 homer-ubuntu gdm[5716]: gdm_slave_start: Starting slave process for lisa.librium.local:0
Sep  1 21:45:29 homer-ubuntu gdm[5716]: gdm_slave_start: Loop Thingie
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_display_manage: Forked slave: 5716
Sep  1 21:45:29 homer-ubuntu gdm[5716]: gdm_slave_run: Opening display lisa.librium.local:0
Sep  1 21:45:29 homer-ubuntu gdm[5716]: gdm_slave_greeter: Running greeter on lisa.librium.local:0
Sep  1 21:45:29 homer-ubuntu gdm[5716]: gdm_slave_greeter: Greeter on pid 5722
Sep  1 21:45:29 homer-ubuntu gdm[5716]: Sending GREETPID == 5722 for slave 5716
Sep  1 21:45:29 homer-ubuntu gdm[4368]: Handling message: 'GREETPID 5716 5722'
Sep  1 21:45:29 homer-ubuntu gdm[4368]: Got GREETPID == 5722
Sep  1 21:45:29 homer-ubuntu gdm[4368]: gdm_socket_handler: Accepting new connection fd 9

```

**LOG 2 - Failed XDMCP connection from Machine B**
```

Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_decode: Received opcode QUERY from client 192.168.0.22
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_handle_query: Opcode 2 from 192.168.0.22
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_host_allow: client->hostname is bart.munged.co.uk 
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_send_willing: Sending WILLING to 192.168.0.22
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_decode: Received opcode REQUEST from client 192.168.0.22
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_handle_request: Got REQUEST from 192.168.0.22
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_host_allow: client->hostname is bart.munged.co.uk 
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_handle_request: xdmcp_pending=0, MaxPending=4, xdmcp_sessions=0, MaxSessions=16, ManufacturerID=
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_display_dispose_check (bart.munged.co.uk:0)
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_auth_secure_display: Setting up access for bart.munged.co.uk:0
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_auth_secure_display: Setting up access
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_auth_secure_display: Setting up access for bart.munged.co.uk:0 - 1 entries
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_display_alloc: display=bart.munged.co.uk:0, session id=2104627136, xdmcp_pending=1 
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_send_accept: Sending ACCEPT to 192.168.0.22 with SessionID=2104627136
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_decode: Received opcode MANAGE from client 192.168.0.22
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_handle_manage: Got MANAGE from 192.168.0.22
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_host_allow: client->hostname is bart.munged.co.uk 
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_handle_manage: Got Display=0, SessionID=2104627136 Class=MIT-unspecified from 192.168.0.22
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_xdmcp_handle_manage: Looked up bart.munged.co.uk:0
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_choose_indirect_lookup: Host 192.168.0.22 not found
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_forward_query_lookup: Host 192.168.0.22 not found
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_display_manage: Managing bart.munged.co.uk:0
Sep  1 21:52:16 homer-ubuntu gdm[4368]: loop check: last_start 0, last_loop 0, now: 1157143936, retry_count: 0
Sep  1 21:52:16 homer-ubuntu gdm[4368]: Resetting counts for loop of death detection
Sep  1 21:52:16 homer-ubuntu gdm[5993]: gdm_slave_start: Starting slave process for bart.munged.co.uk:0
Sep  1 21:52:16 homer-ubuntu gdm[5993]: gdm_slave_start: Loop Thingie
Sep  1 21:52:16 homer-ubuntu gdm[4368]: gdm_display_manage: Forked slave: 5993
Sep  1 21:52:16 homer-ubuntu gdm[5993]: gdm_slave_run: Opening display bart.munged.co.uk:0
Sep  1 21:52:16 homer-ubuntu gdm[5993]: gdm_slave_run: Sleeping 1 on a retry
Sep  1 21:52:17 homer-ubuntu gdm[5993]: gdm_slave_run: Sleeping 3 on a retry
Sep  1 21:52:20 homer-ubuntu gdm[5993]: gdm_slave_run: Sleeping 5 on a retry
Sep  1 21:52:25 homer-ubuntu gdm[5993]: gdm_slave_run: Sleeping 7 on a retry
Sep  1 21:52:32 homer-ubuntu gdm[5993]: gdm_slave_run: Sleeping 9 on a retry
Sep  1 21:52:41 homer-ubuntu gdm[5993]: gdm_slave_run: Sleeping 11 on a retry
Sep  1 21:52:52 homer-ubuntu gdm[5993]: gdm_slave_run: Sleeping 13 on a retry
Sep  1 21:53:05 homer-ubuntu gdm[5993]: gdm_slave_run: Sleeping 15 on a retry
Sep  1 21:53:20 homer-ubuntu gdm[5993]: gdm_slave_run: Sleeping 17 on a retry
Sep  1 21:53:37 homer-ubuntu gdm[5993]: gdm_slave_run: Sleeping 19 on a retry
Sep  1 21:53:56 homer-ubuntu gdm[5993]: gdm_slave_quick_exit: Will kill everything from the display
Sep  1 21:53:56 homer-ubuntu gdm[5993]: gdm_slave_quick_exit: Killed everything from the display
Sep  1 21:53:56 homer-ubuntu gdm[4368]: mainloop_sig_callback: Got signal 17
Sep  1 21:53:56 homer-ubuntu gdm[4368]: gdm_cleanup_children: child 5993 returned 4
Sep  1 21:53:56 homer-ubuntu gdm[4368]: gdm_child_action: Aborting display bart.munged.co.uk:0
Sep  1 21:53:56 homer-ubuntu gdm[4368]: gdm_display_unmanage: Stopping bart.munged.co.uk:0 (slave pid: 0)
Sep  1 21:53:56 homer-ubuntu gdm[4368]: gdm_display_dispose: Disposing bart.munged.co.uk:0
Sep  1 21:53:56 homer-ubuntu gdm[4368]: gdm_display_unmanage: Display stopped

```

---

### Post by n3ko on 2008-02-10
It's a dns problem. i had the same...
writing the ip-s to the hosts.conf may help.


I changed the nsswitch.conf hosts line
from:
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
to:
hosts:          files dns mdns4
and this solved whitout editing hosts.conf

---

