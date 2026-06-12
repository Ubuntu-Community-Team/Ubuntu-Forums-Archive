---
title: "XFS - unmounts by itself"
date: 2009-02-03
forum: General Help
---

### Post by bonfire89 on 2009-02-03
While running rTorrent under ubuntu server 8.10 (perhaps even when not running rTorrent (I think that is actually the case)) a 1.5TB drive with an xfs filesystem on it will unmount itself.

I will be connected to the server via ssh and rTorrent will close out with an error. (suggesting that I have run out of space)

At the server itself a message will be on the screen

```
[11363.440034] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[11363.440070] ata2.01: cmd ea/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[11363.440072]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout
[11363.440108] ata2.01: status: { DRDY }
[11373.832178] end_request: I/O error, dev sdc, sector 1465137435
[11373.832285] I/O error in filesystem ("sdc1") meta-data dev sdc1 block 0x575438dc        ("xlog_iodone") error 5 buf count 7680
[11373.832335] Filesystem "sdc1": Log I/O Error Detected.  Shutting down filesystem: sdc1
[11373.832358] Please unmount the filesystem, and rectify the problem(s) 
```

Help on this will be appreciated, thanks in advance.




ps if there is a way that I can access that quoted text without having to type it out manually I would love to know :)

---

### Post by bonfire89 on 2009-02-04
ah, never mind, past experience says I wont get a response. I was wanting to diversify my distro skills so, I just installed a new OS

---

