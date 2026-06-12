---
title: "Problems while playing Dota 2 CS:GO and general"
date: 2016-09-27
forum: Gaming &amp; Leisure
---

### Post by ignajavi2 on 2016-09-27
Hi All,

I am having a lot of dump/cpu freezes.
I have copy-paste some lines from my sylog based on the day and hour that DUMPS occurs.

This is the last one:
Sep 27 20:46:46 Dell-System-XPS-L502X systemd[1]: Starting Cleanup of Temporary Directories...
Sep 27 20:46:46 Dell-System-XPS-L502X systemd-tmpfiles[3557]: [/usr/lib/tmpfiles.d/var.conf:14] Duplicate line for path "/var/log", ignoring.
Sep 27 20:46:46 Dell-System-XPS-L502X systemd[1]: Started Cleanup of Temporary Directories.
Sep 27 20:52:46 Dell-System-XPS-L502X systemd[1]: Starting Automatically refresh installed snaps...
Sep 27 20:52:46 Dell-System-XPS-L502X /usr/lib/snapd/snapd[908]: store.go:539: DEBUG: cannot set device session: no state entry for key
Sep 27 20:52:47 Dell-System-XPS-L502X /usr/lib/snapd/snapd[908]: daemon.go:170: DEBUG: uid=0;@ POST /v2/snaps 500.741855ms 202
Sep 27 20:52:47 Dell-System-XPS-L502X snap[3593]: #015#033[K
Sep 27 20:52:47 Dell-System-XPS-L502X snap[3593]: All snaps up to date.
Sep 27 20:52:47 Dell-System-XPS-L502X systemd[1]: Started Automatically refresh installed snaps.
Sep 27 20:52:47 Dell-System-XPS-L502X systemd[1]: snapd.refresh.timer: Adding 5h 10min 57.322195s random time.
Sep 27 20:52:47 Dell-System-XPS-L502X systemd[1]: snapd.refresh.timer: Adding 58min 44.521151s random time.
Sep 27 20:53:24 Dell-System-XPS-L502X kernel: [ 1300.172000] NVRM: GPU at PCI:0000:01:00: GPU-f5a0ba91-5d73-7b7a-d15a-d188e0b538d9
Sep 27 20:53:24 Dell-System-XPS-L502X kernel: [ 1300.172032] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: Shader Program Header 1 Error
Sep 27 20:53:24 Dell-System-XPS-L502X kernel: [ 1300.172043] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: Shader Program Header 3 Error
Sep 27 20:53:24 Dell-System-XPS-L502X kernel: [ 1300.172052] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: Shader Program Header 9 Error
Sep 27 20:53:24 Dell-System-XPS-L502X kernel: [ 1300.172060] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: Shader Program Header 11 Error
Sep 27 20:53:24 Dell-System-XPS-L502X kernel: [ 1300.172068] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: Shader Program Header 18 Error
Sep 27 20:53:24 Dell-System-XPS-L502X kernel: [ 1300.172078] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ESR 0x405840=0xa0040a0a
Sep 27 20:53:24 Dell-System-XPS-L502X kernel: [ 1300.172117] NVRM: Xid (PCI:0000:01:00): 13, Graphics Exception: ChID 0001, Class 00009197, Offset 00000100, Data 0fffcc00
Sep 27 20:53:24 Dell-System-XPS-L502X kernel: [ 1300.177272] NVRM: Xid (PCI:0000:01:00): 39, CCMDs 00000007 000090b5
Sep 27 20:53:26 Dell-System-XPS-L502X kernel: [ 1302.177312] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context
Sep 27 20:53:28 Dell-System-XPS-L502X kernel: [ 1304.177474] NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context




If you need more information or a recommendation, feel free. I will be really gratefull!

This is my first Post on the community!

---

### Post by oldrocker99 on 2016-09-27
Welcome to the forums!

When you post code, please enter it with **code** in brackets **[]** at the top and  /code at the end to make it easier to read.


Beyond that, what is your system? CPU, RAM, GPU?

Please post the output of```
lspci
```

This will make it a trifle easier for us to help you.

---

