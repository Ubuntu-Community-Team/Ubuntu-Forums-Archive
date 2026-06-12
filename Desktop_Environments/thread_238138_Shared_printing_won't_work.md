---
title: "Shared printing won't work"
date: 2006-08-17
forum: Desktop Environments
---

### Post by sdebo on 2006-08-17
I shared a PSC1110 printer on an XP machine from my Ubuntu Dapper box. It is visible to Ubuntu and print jobs do clear from the Linux print queue. However they get stuck in the XP print spooler. The printer leds just flash and no print job comes out. What's the possible problem?

---

### Post by sdebo on 2006-09-03
I kept trying hoping I would manage to solve this.  I fixed many other issues and learnt a lot in the process but I cannot crack this one.

Here is the samba log readout.  Anyone can help?

```
[2006/09/02 21:09:31, 0] smbd/nttrans.c:call_nt_transact_ioctl(2344)
  call_nt_transact_ioctl(0x9009c): Currently not implemented.
[2006/09/02 23:23:32, 0] lib/util_sock.c:read_data(529)
  read_data: read failure for 4 bytes to client 192.168.2.101. Error = Connection reset by peer
[2006/09/02 23:23:32, 1] smbd/service.c:close_cnum(890)
  jagernaut (192.168.2.101) closed connection to service shared
[2006/09/02 23:24:24, 0] lib/util_sock.c:write_data(557)
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2006/09/02 23:24:24, 0] lib/util_sock.c:send_smb(765)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
[2006/09/02 23:55:58, 1] smbd/service.c:make_connection_snum(693)
  jagernaut (192.168.2.101) connect to service shared initially as user stanley (uid=1000, gid=1000) (pid 21652)
[2006/09/02 23:56:00, 1] smbd/service.c:make_connection_snum(693)
  jagernaut (192.168.2.101) connect to service shared initially as user nobody (uid=65534, gid=65534) (pid 21652)
[2006/09/02 23:56:09, 1] smbd/service.c:close_cnum(890)
  jagernaut (192.168.2.101) closed connection to service shared
[2006/09/03 01:00:21, 0] lib/util_sock.c:write_data(557)
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2006/09/03 01:00:21, 0] lib/util_sock.c:send_smb(765)
  Error writing 4 bytes to client. -1. (Connection reset by peer)
```

---

