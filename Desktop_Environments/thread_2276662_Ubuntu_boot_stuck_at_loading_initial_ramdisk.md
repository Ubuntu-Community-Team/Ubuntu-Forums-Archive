---
title: "Ubuntu boot stuck at loading initial ramdisk"
date: 2015-05-04
forum: Desktop Environments
---

### Post by biaggi on 2015-05-04
Hi, I'm running ubuntu 14.04 LTS in a dell inspiron 7348


I've just installed ubuntu 64 in a dual boot with windows 8, so I'm running ubuntu in UEFI mode.


When grub loads, I must select Advanced options->recovery mode to be able to load, otherwise, it get stuck in loading initial ramdisk screen.


Any hint on which log could I use to be able to investigate the problem? I'm completly lost

---

### Post by dino99 on 2015-05-04
syslog/dmesg are the two first logs to glance at (into /var/log/)

---

### Post by biaggi on 2015-05-04
Thank you @Dino99, this is the last log in syslog when it fails loading...

May  4 11:33:20 jmgomez-Inspiron-7348 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="801" x-info="http://www.rsyslog.com"] start
May  4 11:33:20 jmgomez-Inspiron-7348 rsyslogd: rsyslogd's groupid changed to 104
May  4 11:33:20 jmgomez-Inspiron-7348 rsyslogd: rsyslogd's userid changed to 101
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] Initializing cgroup subsys cpuset
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] Initializing cgroup subsys cpu
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] Initializing cgroup subsys cpuacct
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] Linux version 3.16.0-36-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #48~14.04.1-Ubuntu SMP Wed Apr 15 13:11:28 UTC 2015 (Ubuntu 3.16.0-36.48~14.04.1-generic 3.16.7-ckt9)
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-36-generic.efi.signed root=UUID=4c8f5387-a17d-41f4-8f4d-85549c09f50a ro quiet splash vt.handoff=7
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] KERNEL supported cpus:
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000]   Intel GenuineIntel
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000]   AMD AuthenticAMD
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000]   Centaur CentaurHauls
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] e820: BIOS-provided physical RAM map:
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000059000-0x0000000000087fff] usable
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000088000-0x000000000009ffff] reserved
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000086639fff] usable
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x000000008663a000-0x0000000086f39fff] reserved
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000086f3a000-0x000000009c4cefff] usable
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x000000009c4cf000-0x000000009c6cefff] type 20
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x000000009c6cf000-0x000000009cebefff] reserved
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x000000009cebf000-0x000000009cfbefff] ACPI NVS
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x000000009cfbf000-0x000000009cffefff] ACPI data
May  4 11:33:20 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x000000009cfff000-0x000000009cffffff] usable
May  4 11:33:20 jmgomez-Inspiron-7348 keMay  4 11:34:08 jmgomez-Inspiron-7348 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="1186" x-info="http://www.rsyslog.com"] start

Here I did a hard shutdown, cos it was hunged up
And this is the log when I start in recovery mode.

May  4 11:34:08 jmgomez-Inspiron-7348 rsyslogd: rsyslogd's groupid changed to 104
May  4 11:34:08 jmgomez-Inspiron-7348 rsyslogd: rsyslogd's userid changed to 101
May  4 11:34:08 jmgomez-Inspiron-7348 NetworkManager[1223]: <info> NetworkManager (version 0.9.8.8) is starting...
May  4 11:34:08 jmgomez-Inspiron-7348 NetworkManager[1223]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
May  4 11:34:08 jmgomez-Inspiron-7348 NetworkManager[1223]: <info> WEXT support is enabled
May  4 11:34:08 jmgomez-Inspiron-7348 cron[1193]: (CRON) INFO (pidfile fd = 3)
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] Initializing cgroup subsys cpuset
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] Initializing cgroup subsys cpu
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] Initializing cgroup subsys cpuacct
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] Linux version 3.16.0-36-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #48~14.04.1-Ubuntu SMP Wed Apr 15 13:11:28 UTC 2015 (Ubuntu 3.16.0-36.48~14.04.1-generic 3.16.7-ckt9)
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-36-generic.efi.signed root=UUID=4c8f5387-a17d-41f4-8f4d-85549c09f50a ro recovery nomodeset
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] KERNEL supported cpus:
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000]   Intel GenuineIntel
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000]   AMD AuthenticAMD
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000]   Centaur CentaurHauls
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] e820: BIOS-provided physical RAM map:
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000059000-0x0000000000087fff] usable
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000088000-0x000000000009ffff] reserved
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x0000000086639fff] usable
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x000000008663a000-0x0000000086f39fff] reserved
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000086f3a000-0x000000009c4cefff] usable
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x000000009c4cf000-0x000000009c6cefff] type 20
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x000000009c6cf000-0x000000009cebefff] reserved
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x000000009cebf000-0x000000009cfbefff] ACPI NVS
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x000000009cfbf000-0x000000009cffefff] ACPI data
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x000000009cfff000-0x000000009cffffff] usable
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000025effffff] usable
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] NX (Execute Disable) protection: active
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] efi: EFI v2.40 by Dell Inc.
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] efi:  SMBIOS=0x9c742000  ACPI 2.0=0x9cffe014
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
May  4 11:34:08 jmgomez-Inspiron-7348 kernel: [    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x000000000000e000) (0MB)


Any aditional hint?

---

### Post by alex375 on 2015-05-04
Exactly /var/log/dmesg.0

---

