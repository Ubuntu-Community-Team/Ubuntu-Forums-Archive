---
title: "Ripping CDs causes a segfault on AMD64"
date: 2006-05-26
forum: Desktop Environments
---

### Post by harro0209 on 2006-05-26
I use kernel 2.6.15-22-smd64-k8 (SMP) on a AMD64 X2 4200+ machine with an updated Dapper. When I try to rip an audio CD (mp3) I get

sound-juicer[6173]: segfault at 0000000000c58000 rip 00002aaab287c017 rsp 00000000410419a8 error 6 (dmesg)

The same happens if I use banshee to rip CDs. grip works fine.
In launchpad I found similar errors related to compiz but somehow I suspect that gstreamer might be linked with this weird behaviour.

Can anybody confirm this ?

Thx.

---

### Post by harro0209 on 2006-05-31
Did nobody experience this behaviour ?](*,)

---

