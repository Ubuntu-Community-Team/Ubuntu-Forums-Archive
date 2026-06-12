---
title: "Increase Vino Resolution"
date: 2009-04-08
forum: General Help
---

### Post by dotJoel on 2009-04-08
Hi Guys,

Curious, if I have an LCD plugged in to the box then when I VNC in to the box it shows the resolution the screen is running at.  However if I boot up the box with no monitor attached and VNC to it then I get the 800x600 resolution and can not increase it above this.

Any suggestions or help on how to increase the VNC resolution of Vino?  My main monitor runs at a high resolution, I would like to at least increase the VNC to 1280.

Regards,


Joel

---

### Post by cariboo on 2009-04-08
Because your system is starting without a monitor attached it goes into bulletproof X mode. the only way to get a higher resolution is to leave a monitor connected.

If you are just using a few applications, why not use X forwarding. To use x forwarding you have to install openssh-server on your remote computer. then when you want to run a program on the remote system open a terminal and type:

```
ssh -X user@remote_computer
```

once at the prompt just type the name of the program nad it will forward that program to your desktop eg:

```
firefox
```

You can also use sftp to manipulate files by type in the address bar of Nautilus:

```
sftp://user@remote_computer
```

this will open the file manager on your desktop with the remote computers file tree in it.

Jim

---

