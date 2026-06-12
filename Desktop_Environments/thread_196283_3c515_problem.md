---
title: "3c515 problem"
date: 2006-06-14
forum: Desktop Environments
---

### Post by helpdeskdan on 2006-06-14
I am unable to get my 3c515 working.  It works in windows (dual boot).  It worked in 5.10.  (As I remember, a simple modprobe 3c515 worked fine)  Does not work in Dapper.  :confused:  Bringing the card up manually with network-admin seems to bring up the card, but it does not work.  I did note that in windows there were different settings: IRQ 11, DMA 06, I/0 02C0-02DF.  Any ideas would be appreciated; this is the only 10/100 card I have in my spare parts bin & funds are short!

[FONT="Courier New"][SIZE="1"]dan@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:372 (372.0 b)  TX bytes:372 (372.0 b)

dan@ubuntu:~$ 
dan@ubuntu:~$ dmesg | grep 3c515
[  118.834221] 3c515.c:v0.99t-ac 28-Oct-2002 [email]becker@scyld.com[/email] and others
[  118.837101] 3c515 Resource configuration register 0x00a5, DCR 1483.
[  118.837160] eth%d: 3Com 3c515 at 0x2a0, 00:10:4b:34:24:68, DMA 3, IRQ 5
dan@ubuntu:~$ lsmod | grep 3c515
3c515                  19748  0
dan@ubuntu:~$ sudo 3c515-diag -p 0x2a0
3c515-diag.c:v1.03 3/14/2005 Donald Becker
   [http://scyld.com/diag/index.html](http://scyld.com/diag/index.html)
Looking for card at 2a0.

A ISA Fast EtherLink III board was detected at I/O 0x2a0.
Window 0: 0000 0000 0000 0000 0000 0095 0000 0000.
Window 1: 84c2 642a 0000 2000 8000 00ff 7ffc 2000.
Window 2: 1000 344b 6824 0000 0000 0000 0000 4000.
Window 3: 001b 0102 0000 0000 f040 7fff 7fff 6000.
Window 4: 0000 06d0 2000 0000 0002 8a10 0000 8000.
Window 5: 1ffc 1ffc 0000 1ffc 0000 0000 0000 a000.
Window 6: 0000 0000 0000 0000 0000 0000 0000 c000.
Window 7: 0000 0000 0000 0000 8000 00ff 0000 e000.
Operation registers: 642a 642a 0000 e000 8000 00ff 7ffc e000.
Boomerang registers: ffff ffff ffff ffff ffff ffff ffff ffff
  (at 0x6a0)       : ffff ffff ffff ffff ffff ffff ffff ffff.
Corkscrew registers: 1483 00a5 0000 0000 0001 0197 0010 ffff.
EEPROM contents:
 0010 4b34 2468 0089 c446 0036 4c4d 6d50 1485 5150 0010 4b34 2468 3f10 0000 0000 11c7 0000 001b 0161 0000 0003 0000 0010 6d50 5150 2468 4b34 0ab2 1010 1782 3300 6f43 206d 6146 7473 4520 6874 7265 694c 6b6e 4920 4153 5015 506d 0251 a822 2a9e 06e8 0047 0280 03e0 2020 4079 0000 0000 0000 0000 0000 0000 0000 0000 0000 0000  64K word-wide RAM 1:1 Rx:Tx split, autoselect/10baseT interface.
   Done card at 0x2a0.
dan@ubuntu:~$
(After bringing the interface up with network-admin)
dan@ubuntu:~$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:10:4B:34:24:68
          inet addr:10.42.42.14  Bcast:10.42.42.255  Mask:255.255.255.0
          inet6 addr: fe80::210:4bff:fe34:2468/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:12
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:720 (720.0 b)
          Interrupt:5 Base address:0x2a0 DMA chan:3

dan@ubuntu:~$ ping 10.42.42.1
PING 10.42.42.1 (10.42.42.1) 56(84) bytes of data.
From 10.42.42.14 icmp_seq=2 Destination Host Unreachable
From 10.42.42.14 icmp_seq=3 Destination Host Unreachable
dan@ubuntu:~$ lsmod | grep 3c515
3c515                  19748  0
[/SIZE][/FONT]

---

