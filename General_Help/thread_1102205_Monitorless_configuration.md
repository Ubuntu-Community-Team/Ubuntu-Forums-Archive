---
title: "Monitorless configuration"
date: 2009-03-21
forum: General Help
---

### Post by samthecat on 2009-03-21
Hello,
  new here.  I have loaded Ubuntu 8.10 on a spare pc that I want to access remotely via vnc from a winPC.  The setup works as I had hoped with one exception.  The ubuntu machine seems to require that a monitor is connected at boot otherwise it runs in a low res graphics mode.  Is there a way I can force the machine to boot and run the xserver at a specific configuration ?  I'd really like to run the configuration with no mouse / keyboard and monitor......

Sam

---

### Post by cariboo on 2009-03-21
The easiest way to solve your problem is to stop X from starting and using ssh + X forwarding. To stop X from starting disable gdm:

```
sudo update-rc.d -f gdm remove
```

to x forward an applacation:

```
ssh -X user@server
```

then at the prompt of the remote computer type the name of the aaplication you want to run.

You will need to install openssh-server on the headless computer in order to use ssh.

Jim

---

### Post by samthecat on 2009-03-21
Jim,
  Can I remote the desktop this way ?  Do I run the window manager as the apllication ?

Sam

---

