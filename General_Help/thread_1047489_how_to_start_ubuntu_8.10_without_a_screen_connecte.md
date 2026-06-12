---
title: "how to start ubuntu 8.10 without a screen connected?"
date: 2009-01-22
forum: General Help
---

### Post by nicolaamatucci on 2009-01-22
Hi everyone. I bought a new server and I've installed ubuntu 8.10 on it, but i haven't an lcd for this computer, so ubuntu don't start, but goes in safe mode and freeze. How I can avoid this problem. Thanks.

---

### Post by Titan8990 on 2009-01-22
There isn't a safe mode in Ubuntu. There is a recovery mode but it has to be manually selected.

Please try to explain a bit more.

---

### Post by dcstar on 2009-01-22
> **nicolaamatucci said:**
> Hi everyone. I bought a new server and I've installed ubuntu 8.10 on it, but i haven't an lcd for this computer, so ubuntu don't start, but goes in safe mode and freeze. How I can avoid this problem. Thanks.

You should really have used a "Server" CD as this does not install the graphical stuff, but you can disable the automatic startup of this by deleting a file:

```
sudo rm /etc/rc2.d/S30gdm
```

If you need to run the graphical interface you can start it manually by:

```
sudo startx
```

---

### Post by jimv on 2009-01-22
>Hi everyone. I bought a new server and I've installed ubuntu 8.10 on it, but i haven't an lcd for this computer, so ubuntu don't start, but goes in safe mode and freeze. How I can avoid this problem. Thanks.

Ubuntu (and Windows and Mac) will start up just fine without a monitor connected.  You've got some other kind of problem.

---

### Post by rcolson9333 on 2009-01-22
Hey, So i might have a similar problem.

I setup 8.10 server with Gnome desktop on a KPC.  Been SSHing and VNCing into it no problem.  Then I remove the monitor, SSH sudo shutdown -r now.
and the KPC reboots.  But there is some X error because I can't get a VNC session to start for another computer.
So i plugged in a monitor and got an error box requesting and "OK"
(errors were "
(EE)intel(0): no valid modes     and   
(EE)Srcreen(s) found, but non have a usable configuration"

I could use some guidance.
thx

---

