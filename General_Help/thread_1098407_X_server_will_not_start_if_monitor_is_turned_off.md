---
title: "X server will not start if monitor is turned off"
date: 2009-03-17
forum: General Help
---

### Post by fireman71 on 2009-03-17
Hello everyone,

I have a problem that I haven't been able to figure out yet. I have Hardy on a desktop that is going to become a file, print and local lan server. I have all that setup and working fine so far. I am wanting this to be a headless box that I control via VNC primarily and SSH alternatively. I have the SSH part working fine.

My problem is that when the machine is started/booted up/rebooted and the monitor is not plugged into it or is turned off X Server seems to start but the generates a message about starting in low graphics mode and just sits there until I connect a monitor, click continue and then restart X. This means that I can log in via SSH but cannot log in through VNC until I connect a monitor which is what I am trying to avoid.

xorg.conf seems to be configured fine since everything woks flawlessly when a monito is connected and turned on during bootup.

All assistance is greatly appreciated.

---

### Post by cariboo on 2009-03-17
The way X is configured in Ubuntu, it needs a monitor connected in order for the server to start. I would suggest disabling GDM and use X forwarding if you need gui apps to do anything.

Using X forwarding you can use gui apps without having to start X. For X forwarding in a terminal type:

```
ssh -X user@server
```

then once logged on type the name of the application in the terminal eg:

```
nautilus
```

You can also use sftp and scp for file management. Open up Nautilus and in the address bar type:

```
sftp://user@server
```

your home directory on the server will open in Nautilus.

To stop gdm from starting at the prompt on your server type:

```
sudo update-rc.d -f gdm remove
```

Jim

---

### Post by ruel- on 2009-03-17
X server get settings from your display(monitor).. so if you want to use it with X in the right tuning, you must include a monitor...

---

