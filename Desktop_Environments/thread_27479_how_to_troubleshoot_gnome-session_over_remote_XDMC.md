---
title: "how to troubleshoot gnome-session over remote XDMCP?"
date: 2005-04-16
forum: Desktop Environments
---

### Post by goofrider on 2005-04-16
I used to connect to my Ubuntu server (Hoary preview) from my PC using XDMCP, which worked fine. However now it stoped working (posibly because of Hoary final release??)

Basically, I start my X server on the PC connect to GDM, which works fine. but as so as I logged in, it only shows a blank color background. 


Then I tried using X forwarding over SSH, but I don't know how to start gnome-session from the SSH shell. I get this erorr if I use the cmd "gnome-session" in the SSH shell with no args.
```

$ gnome-session
Xlib: connection to "localhost:10.0" refused by server
Xlib: Client is not authorized to connect to Server

(gnome-session:7739): Gtk-WARNING **: cannot open display:

```

Running xterm within the SSH shell worked as expected: it shows xterm on the X server on my PC. So at least I know X Forwading worked fine.

I also tried starting a KDE session (by choosing KDE when I log into GDM) from my PC over XDMCP (with or without SSH tunneling), and that worked fine. 

So how do know what's wrong with gnome-session? Where can I find gnome-session log files?

---

### Post by goofrider on 2005-04-16
[QUOTE=goofrider]I used to connect to my Ubuntu server (Hoary preview) from my PC using XDMCP, which worked fine. However now it stoped working (posibly because of Hoary final release??)

Basically, I start my X server on the PC connect to GDM, which works fine. but as so as I logged in, it only shows a blank color background. 


Then I tried using X forwarding over SSH, but I don't know how to start gnome-session from the SSH shell. I get this erorr if I use the cmd "gnome-session" in the SSH shell with no args.
```

$ gnome-session
Xlib: connection to "localhost:10.0" refused by server
Xlib: Client is not authorized to connect to Server

(gnome-session:7739): Gtk-WARNING **: cannot open display:

```

Running xterm within the SSH shell worked as expected: it shows xterm on the X server on my PC. So at least I know X Forwading worked fine.

I also tried starting a KDE session (by choosing KDE when I log into GDM) from my PC over XDMCP (with or without SSH tunneling), and that worked fine. 

So how do know what's wrong with gnome-session? Where can I find gnome-session log files?[/QUOTE]
 Somehow gnome-session over SSH X Forwarding is working again. Still can't get gnome-session to start when I log in over XDMCP though...

---

### Post by nad on 2005-04-16
Have you tweaked your gdm.conf file yet? Your session log files are in /var/log/gdm/.

As far as your permissions issue, see the xhost man page for starters. From the xterm on display 10, issuing the command ' xhost + ' will remove _all_ authorization for this display.

Dan M

---

### Post by hamiltjr on 2005-04-18
I've been having this same issue, has anyone come to any resolve with it?

---

### Post by goofrider on 2005-04-19
[QUOTE=nad]Have you tweaked your gdm.conf file yet? Your session log files are in /var/log/gdm/.

As far as your permissions issue, see the xhost man page for starters. From the xterm on display 10, issuing the command ' xhost + ' will remove _all_ authorization for this display.

Dan M[/QUOTE]


Forget about the permission issue or GDM conf, since I can connect to GDM from my PC using XDMCP query (without SSH tunneling), and login with GDM. (The X11 over SSH permission issue was totally isolated and I no longer have the problem).

I still don't get a Gnome desktop after GDM login, just a blank burgandy background. GDM log showed nothing.

OK I just disabled Firestarter (which I recently installed) and it worked fine now. Which is weird 'cuz it still works when I enable Firestarter again, restart the X server on my PC and login again via GDM.

Why would Firestarter block remote X? Since the X server is the one that should be aceepting incoming connections, and Firestarter/iptables was configured to permit all outgoing connections.

FWIW, GDM log showed nothing other than some startup time warnings about font registrations. kern.log didn't show any local connections being blocked by iptables either until I diasable Firestarter and re-enable it.

Anyways, it seems to work OK now...

---

