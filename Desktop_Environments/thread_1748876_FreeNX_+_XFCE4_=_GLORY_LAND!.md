---
title: "FreeNX + XFCE4 = GLORY LAND!"
date: 2011-05-04
forum: Desktop Environments
---

### Post by Sir_Brizz on 2011-05-04
I don't know if this will help anyone, but I have been toiling over this on Google for a few weeks now and I finally found a hint of a solution that finally turned out with a real solution. I could never seem to get any of the desktop managers in the nx client settings to pull up the XFCE environment in a usable way, yet with Gnome and KDE it worked magnificently.

The method I used to get it working is rather simple...

1) sudo vim /usr/NX/etc/node.cfg

2) On line 151, you will find a line like:
```

# Specify path and name of the command starting 'CDE'.
#
#CommandStartCDE = "cdwm"

```
I don't know what cdwm is, but I am sure I would never need to use it, so I changed this line to:
```

# Specify path and name of the command starting 'CDE'.
#
CommandStartCDE = "/usr/bin/startxfce4"

```

3) sudo /usr/NX/bin/nxserver --restart

4) Et voila, connect to the server with your nxclient set to CDE and there is your XFCE4 desktop in all its glory!

Sidenote: I installed the .deb from the NoMachine website so my file paths will probably be different. I will try using stock packages later (from the FreeNX Team PPA), however the steps should be somewhat similar even for those.

Sidenote 2: If this is posted in the wrong place, feel free to move to the right place. Thanks!

---

### Post by sniffton on 2011-12-05
Hey,

Just made the switch to xubuntu from ubuntu and had just setup nx on my media 'puter.

Thanks for this!

Nathaniel

---

### Post by kybel_gitu on 2012-11-01
FreeNX Team did realy good job with their implementation. I switched to xfce since there is none sane DE for linux at the moment. Not that XFCE is somehow functional - it lack almost everything user may need from DE - one example for them all - no file/folder sharing functionality - i am speachless.... However it is small,light and i can manage it somehow and i don't need use it much. 
That said be aware that if you want use freenx with XFCE it will bring like half of gnome with it so it does not looks to me like good choice at this moment. The case apply for Ubuntu Server 12.04 + XFCE 4.10.
If some of you guys find some way not to have bunch of gnome on machine just to enable remote desktop, please let me know. 
Thanx


p.s. there is still xrdp which is much more light solution to remote desktop but to be honest it is somewhat hilarious attempt for rdp. It does not handle even clipboard betven local and remote machine window.... i don't know what to say..... why every functionality implementation must be so cripled in linux?

---

### Post by Luis Miguel on 2012-12-02
> **Sir_Brizz said:**
> 
The method I used to get it working is rather simple...


Thank you for your method, it helped me a lot.

---

### Post by wildmanne39 on 2012-12-02
Old thread closed.

---

