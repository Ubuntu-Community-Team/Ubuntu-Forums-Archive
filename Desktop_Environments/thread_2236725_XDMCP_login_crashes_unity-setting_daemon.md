---
title: "XDMCP login crashes unity-setting daemon"
date: 2014-07-28
forum: Desktop Environments
---

### Post by paul_b3 on 2014-07-28
New install of Ubuntu 14.04 LTS

Enabled XDMCP.

XDMCP client sees login screen, at same time the following error appears in /var/syslog:

Jul 28 14:19:29 cctvbox kernel: [66161.429518] unity-settings-[8665]: segfault at 8 ip 00007f2702d98596 sp 00007fffcea98a10 error 4 in libpower.so[7f2702d88000+19000]

no other errors.

If XDMCP client attempts to login, more errors of the same appear in /var/syslog:


Jul 28 14:57:45 cctvbox kernel: [68455.841209] unity-settings-[9365]: segfault at 8 ip 00007f7218068596 sp 00007fff632ebf80 error 4 in libpower.so[7f7218058000+19000]
Jul 28 14:57:50 cctvbox kernel: [68460.219377] unity-settings-[9516]: segfault at 8 ip 00007fcf27df0596 sp 00007fff3ba75480 error 4 in libpower.so[7fcf27de0000+19000]
Jul 28 14:57:50 cctvbox kernel: [68460.448034] unity-settings-[9527]: segfault at 8 ip 00007f56d6118596 sp 00007fff71b1fec0 error 4 in libpower.so[7f56d6108000+19000]
Jul 28 14:57:50 cctvbox kernel: [68460.679508] unity-settings-[9536]: segfault at 8 ip 00007f683edf0596 sp 00007fffaf12f840 error 4 in libpower.so[7f683ede0000+19000]
Jul 28 14:57:50 cctvbox kernel: [68461.157322] unity-settings-[9549]: segfault at 8 ip 00007fc363df0596 sp 00007fff8a069a50 error 4 in libpower.so[7fc363de0000+19000]
Jul 28 14:57:51 cctvbox kernel: [68461.396598] unity-settings-[9558]: segfault at 8 ip 00007fa79e678596 sp 00007fff2f6d65e0 error 4 in libpower.so[7fa79e668000+19000]
Jul 28 14:57:51 cctvbox kernel: [68461.623025] unity-settings-[9567]: segfault at 8 ip 00007f9d7c230596 sp 00007fff99bf16c0 error 4 in libpower.so[7f9d7c220000+19000]
Jul 28 14:57:52 cctvbox kernel: [68462.955805] unity-settings-[9576]: segfault at 8 ip 00007f7a34320596 sp 00007fff5be4dca0 error 4 in libpower.so[7f7a34310000+19000]
Jul 28 14:57:53 cctvbox kernel: [68463.183298] unity-settings-[9583]: segfault at 8 ip 00007f533d6b0596 sp 00007fffa0d3e560 error 4 in libpower.so[7f533d6a0000+19000]
Jul 28 14:57:53 cctvbox kernel: [68463.405970] unity-settings-[9591]: segfault at 8 ip 00007f52784f0596 sp 00007fff132237a0 error 4 in libpower.so[7f52784e0000+19000]
Jul 28 14:57:53 cctvbox kernel: [68463.643975] unity-settings-[9598]: segfault at 8 ip 00007f7c80180596 sp 00007fffd112e2e0 error 4 in libpower.so[7f7c80170000+19000]

Appears to be trying to respawn, unsuccessfully.

Login never succeeds. Login XDMCP client sees an error box "System program problem detected", Cancel or Report Problem. Selecting either never renders anything further on the client.

Login directly on console is fine and brings up desktop with no problems, only when logging in through XDMCP does this error happen.

No different errors in the kernal log.

---

### Post by TheFu on 2014-07-29
I don't know the answer, but Unity requires 3D accelerated graphics drivers. It doesn't work well on anything less and definitely nothing over a network, like XDMCP.  So, I don't expect Unity will ever work well, if at all, over the network.

For network-based logins, DEs with less "cheese" are required.  XFCE4, LXDE are the normal solutions and work well.

---

