---
title: "PS2 SMS and Samba Panic"
date: 2007-11-18
forum: Gaming &amp; Leisure
---

### Post by Lex Luthor on 2007-11-18
Hello

I have a PS2 plugged on the home network. I installed in the MC the SMS media player, so I can see on my TV the vídeos I make. It always worked perfectly, but yesterday (after 2 weeks without connecting), I tried to watch a vídeo but something strage happaned.

I turn on the PS2, it show my shares on the computer (it is shared by samba). When I select the share to enter, the samba gives me a sampa_panic and restart.

I changed nothing on the PS2 and on the computer either, unless samba was updated in this period of time. I am using gutsy.

Here is the error samba put on my log.ps2:
```

[2007/11/16 23:46:57, 1] smbd/service.c:make_connection_snum(1033)
  playstation2 (192.168.1.90) connect to service Series initially as user nobody (uid=65534, gid=65534) (pid 7367)
[2007/11/16 23:46:57, 0] lib/util.c:smb_panic(1632)
  PANIC (pid 7367): push_ascii - dest_len == -1
[2007/11/16 23:46:57, 0] lib/util.c:log_stack_trace(1736)
  BACKTRACE: 14 stack frames:
   #0 /usr/sbin/smbd(log_stack_trace+0x2d) [0x828b1bd]
   #1 /usr/sbin/smbd(smb_panic+0x5d) [0x828b2ed]
   #2 /usr/sbin/smbd(push_ascii+0xf7) [0x8273b47]
   #3 /usr/sbin/smbd(push_string_fn+0x4c) [0x8273b9c]
   #4 /usr/sbin/smbd(srvstr_push_fn+0x54) [0x80fffd4]
   #5 /usr/sbin/smbd [0x80e9e21]
   #6 /usr/sbin/smbd [0x80ebd95]
   #7 /usr/sbin/smbd(handle_trans2+0x237) [0x80ec5d7]
   #8 /usr/sbin/smbd(reply_trans2+0x6c4) [0x80f2d54]
   #9 /usr/sbin/smbd [0x810f6f0]
   #10 /usr/sbin/smbd(smbd_process+0x836) [0x8110ac6]
   #11 /usr/sbin/smbd(main+0xbdd) [0x836440d]
   #12 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b8f050]
   #13 /usr/sbin/smbd [0x8094061]
[2007/11/16 23:46:57, 0] lib/util.c:smb_panic(1637)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 7367]
[2007/11/16 23:46:57, 0] lib/util.c:smb_panic(1645)
  smb_panic(): action returned status 0
[2007/11/16 23:46:57, 0] lib/fault.c:dump_core(181)
  dumping core in /var/log/samba/cores/smbd

```

---

