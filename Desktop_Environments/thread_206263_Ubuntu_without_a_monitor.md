---
title: "Ubuntu without a monitor"
date: 2006-06-29
forum: Desktop Environments
---

### Post by banzai on 2006-06-29
Ok guys ive just setup a small linux ubuntu system and basicly i want to use it as a remote server with no monitor, and connect to it via VNC.

If i boot with my monitor connect, the screen res is 1024 (what i want it to be) i can then connect via vnc and use it at 1024.

however if i boot without a monitor plugged in the screen res goes to 680 (or whatever the low figure is) and i vnc cant connects at this side.

So how can i boot without a monitor and get it to work at 1024

Any help valued

Thanks

---

### Post by digs on 2006-06-29
RDP allows you to select a resolution but vnc doesn't. You can try to delete all the resolutions info in xorg.conf except 1024 and see if that works.

---

### Post by banzai on 2006-06-30
tryed that and nothing, what RDP and where can i find it

---

### Post by brian99 on 2006-06-30
I have this same problem with a slightly different twist. I have two machines connected to one monitor and keyboard and mouse via a KVM switch. When I boot Ubuntu with the KVM switch connected to the Ubuntu machine it boots in a high resolution 1280 x 1024 but if I boot Ubuntu with the KVM switch pointed to the other machine (like not having a monitor connected) Ubuntu boots in a resolution of 640 x 480. It is like if if doesn't recognize the monitor it assumes a low resolution. 

btw, RDP is Remote Desktop Protocol and is Microsoft's answer to VNC. In Windows XP  it it under Accessories / Communication. In Ubuntu it is Applications / Internet / Terminal Server Client. Then on the screen select RDP or RDPv5. 

bp

---

### Post by spelingchampeon on 2006-06-30
[QUOTE=brian99]I have this same problem with a slightly different twist. I have two machines connected to one monitor and keyboard and mouse via a KVM switch. When I boot Ubuntu with the KVM switch connected to the Ubuntu machine it boots in a high resolution 1280 x 1024 but if I boot Ubuntu with the KVM switch pointed to the other machine (like not having a monitor connected) Ubuntu boots in a resolution of 640 x 480. It is like if if doesn't recognize the monitor it assumes a low resolution. 

btw, RDP is Remote Desktop Protocol and is Microsoft's answer to VNC. In Windows XP  it it under Accessories / Communication. In Ubuntu it is Applications / Internet / Terminal Server Client. Then on the screen select RDP or RDPv5. 

bp[/QUOTE]
I get the same thing. I guess it polls for the monitor, then when it cant find one, the driver defaults to 640 x 480. Kind of annoying, but just the same, my other machine is WinXP.. and **IT** will lock up minutes after bootup when the monitor isnt selected to my WinXP machine on my KVM.

---

### Post by scxtt on 2006-06-30
i don't have a single problem VNC'ing b/t two boxes - all i do is specify the "-geometry" flag when starting the VNC server on the machine i want to VNC into ... this even works from an ubuntu host to an xubuntu VM ... i used to use it w/ windows as well using RealVNC's server to connect to my :0 XP OS ... my 1st attempt @ this was going from FC4 to FC3 on a server w/ no monitor (except on install) - never had a problem ...
[indent]$:> vncserver -geometry 1024x768 -depth 24[/indent]

---

### Post by iSAWaUFO on 2006-08-21
I think the problem described here is with using the vino-server, as described [on Ubuntuguide]("http://ubuntuguide.org/wiki/Dapper#How_to_configure_remote_desktop_.28not_secure.29") (section 14.1). Presumably, the user configures the system for auto login with remote desktop sharing enabled, then unplugs the monitor and boots the machine. This shares the frame buffer(??) of the graphics card to a VNC service, which allows someone sitting at the system monitor to remotely share his desktop with someone on a different system who connects using a VNC viewer.

I have this same problem and found that when I boot the system with monitor unpluged, the desktop is restricted to 640 x 480. Although if I boot the system with a monitor connected, I get a normal size desktop. Since I only have one monitor, this gets a little tricky. I think if Ubuntu can't recognize a monitor type when booting, it defines a default monitor size of 640 x 480, which is uncomfortably small. Like the other person, I tried mucking with the resolution config file to no avail.

I have found that if I logout of the console connected desktop and then ssh to the ubuntu 6.06 system and launch

vnc4server :1
DISPLAY=:1 x-session-manager &

this will create a virtual desktop of larger size (1024 x 768 is the default), which can be connected to with a VNC client. 

If I try launching x-session-manager while console login is active, I get an error.

To accomplish this, I had to install vnc4server and openssh-server packages, using the Synaptic package manager.

---

### Post by motin on 2006-10-08
There is a HOWTO on this matter here:

HOWTO: Control the gnome VNC vino-server from the command line - [http://ubuntuforums.org/showthread.php?p=1592684](http://ubuntuforums.org/showthread.php?p=1592684)

Appropriate guides could also be:

HOWTO: Set up VNC server with resumable sessions (already done in this thread mostly) - [http://ubuntuforums.org/showthread.php?t=191564](http://ubuntuforums.org/showthread.php?t=191564)

OR 

HOWTO: FreeNX on Dapper LTS 6.06 - [http://ubuntuforums.org/showthread.php?t=241651&highlight=freenx+howto](http://ubuntuforums.org/showthread.php?t=241651&highlight=freenx+howto)

FreeNX is faster than VNC.

---

