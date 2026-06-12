---
title: "Forwarded X windows from HP-UX"
date: 2009-04-10
forum: General Help
---

### Post by Khaele on 2009-04-10
Hi,

I'm looking round using ubuntu as an Xserver for applications running on some HP-UX 11.31 servers.

I'm running this ubuntu in a vmware running on a Windows XP host.

As the ubuntu has to listen on some ports to act as a server and as it's network interface has been configured using NAT, I installed stunnel on WinXP and ubuntu. I forward ports 22 and 6000-6039.

I allowed remote TCP in the gnome conf : DisallowTCP=false

I do a xhost +

Then, at the HP-UX prompt (sh):

```
setenv DISPLAY vmware-host:0.0
```

```
xclock -d -update 1
```


The server contacts correctly the WinXP which forward data to the ubuntu through stunnel.

The window displays correctly.

Everything is working fine BUT I still have a problem:

Backspace, TAB and enter doesn't seems to work correctly...

Those work fine in my putty ssh, but once I start a GUI in this way, I can type in, use mouse, etc. but some keys doesn't work...

I don't know if I have to force some values at Unix side, or....

I'm looking in X11 forwarding too, but as I work mainly in sudoing to system accounts on my unix box, this breaks the X1 forwarding. I'm looking in rebuilding MIT cookies, etc... 

Thank you.

Have a nice weekend.

---

