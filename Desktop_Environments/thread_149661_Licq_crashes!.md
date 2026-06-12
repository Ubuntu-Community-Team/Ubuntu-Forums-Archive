---
title: "Licq crashes!"
date: 2006-03-24
forum: Desktop Environments
---

### Post by Biffy on 2006-03-24
Hi! I have a problem. When i come home from work, Licq has disappeared from my desktop. No sign of it anywhere, and it was up and running when i went to bed. Seems like Licq crashes over night. This does not happen every night, but maybe twice a week.

So i started Licq from a terminal. It was working fine for a couple of days but when i came home from work today, it had crashed. Here's the output from the terminal:

```
larsson@ubuntu:~ $ licq
Licq Segmentation Violation Detected.
Backtrace:
licq(licq_handle_sigsegv+0x9e) [0x8111b7e]
[0xffffe420]
/usr/lib/libstdc++.so.6(_ZN9__gnu_cxx6__poolILb1EE16_M_reclaim_blockEPcj+0x52) [0xb7cee372]
licq(_ZN9__gnu_cxx10__mt_allocISt10_List_nodeIP8ICQEventENS_20__common_pool_policyINS_6__poolELb1EEEE10deallocateEPS4_j+0x72) [0x80adba2]
licq(_ZNSt4listIP8ICQEventSaIS1_EE5eraseESt14_List_iteratorIS1_E+0x40) [0x80addb0]
licq(_Z30ProcessRunningEvent_Server_tepPv+0x1a7) [0x80d1587]
/lib/tls/i686/cmov/libpthread.so.0 [0xb7dd1361]
/lib/tls/i686/cmov/libc.so.6(__clone+0x5e) [0xb7c1abde]
Attempting to generate core file.
Aborted
```

Any ideas on how to solve this?

---

### Post by juve on 2007-07-07
Same problem here (edgy)
My girlfriend just send me an athorization request and when i cam home and started LICQ it starts, says: "Oh Oh !" and crashes, here's the log:
```

# start licq with console package info output

$ licq -d 16
...
...
11:20:37: [PKT] Packet (SRVv0, 68 bytes) received:
                (192.168.#.#:51472 <- #.#.#.#:5190)
     0000: 2A 02 07 7C 00 3E 00 15  00 03 00 01 00 00 00 16   *..|.>..........
     0010: 00 01 00 30 2E 00 3F 4A  72 03 41 00 02 00 7C C9   ...0..?Jr.A...|É
     0020: 8B 06 D7 07 07 06 13 1B  06 00 18 00 FE FE FE FE   ..×.........þþþþ
     0030: 30 FE 61 6E 74 77 6F 72  74 20 69 73 74 20 3A 20   0þantwort ist : 
     0040: 4A 41 21 00                                        JA!.
Licq Segmentation Violation Detected.
Backtrace:
licq(licq_handle_sigsegv+0xc2) [0x80f21a2]
/lib/tls/i686/cmov/libc.so.6 [0xb7b00e98]
licq(_ZN10CICQDaemon17ProcessVariousFamER7CBuffert+0x2012) [0x80be7c2]
licq(_ZN10CICQDaemon18ProcessDataChannelER7CBuffer+0xca) [0x80c29ca]
licq(_ZN10CICQDaemon16ProcessSrvPacketER7CBuffer+0x159) [0x80c2bb9]
licq(_Z18MonitorSockets_tepPv+0x3bf) [0x80c3caf]
/lib/tls/i686/cmov/libpthread.so.0 [0xb7d7831b]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xb7ba657e]
Attempting to generate core file.
Aborted

```

The request was sent by a fancy sponge bob windows client, dunno which version atm.

Any solutions yet ?

---

### Post by juve on 2007-07-07
I'm probaly going to use SIM-IM now, since Licq is no longer maintained, afaics.

---

