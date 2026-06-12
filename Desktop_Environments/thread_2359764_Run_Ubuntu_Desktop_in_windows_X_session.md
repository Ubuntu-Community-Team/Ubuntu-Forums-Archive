---
title: "Run Ubuntu Desktop in windows X session"
date: 2017-04-27
forum: Desktop Environments
---

### Post by ob2s on 2017-04-27
Hi,
I installed MobaXterm (win10) and from a putty ssh'ed terminal exported my display to run an xterm terminal window. I then ran startx from the  xterm session and got this below but no desktop. Is this possible ? to run the ubuntu desktop in an X session ? I also tried running startx from the ssh window and eventually received this --> xauth:  timeout in locking authority file /home/admin/.Xauthority
Thanks

X.Org X Server 1.17.1
Release Date: 2015-02-10
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-77-generic x86_64 Ubuntu
Current Operating System: Linux ubun2 3.19.0-80-generic #88~14.04.1-Ubuntu SMP Fri Jan 13 14:54:07 UTC 2017 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-80-generic.efi.signed root=UUID=630de5db-ce56-4656-97ed-461e0f82f1f3 ro quiet splash vt.handoff=7
Build Date: 13 May 2015  04:35:05AM
xorg-server 2:1.17.1-0ubuntu3~trusty1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Apr 27 08:53:19 2

---

### Post by TheFu on 2017-04-27
Welcome to the forums.

Running any desktop that requires direct access to 3D accelerated GPU isn't easy.  Most people don't try.  For remote X, usually running LXDE or XFCE4 or Mate desktops is recommended.  You can make LXDE place panels on the left side of the screen with whatever programs you like.

It isn't clear, but please be certain to always tunnel X/11 traffic though either a full VPN or ssh tunnels.  There is an easier way to do this that works with ssh security from anywhere in the world. It is 2-3x faster than RDP.  x2go.  There are clients for Linux, OSX and Windows.  I use the Linux and Windows clients almost every day from across the room and halfway around the world.  Though inside the same LAN, I usually just use Linux to Linux for X/Windows stuff. Much easier and no funny non-standard X/Windows servers involved.

Rather than run some funky X/Server under Windows, I decided that running a tiny Linux desktop distro with X inside a virtual machine would be better.  It is. No surprises.  Ask if you are interested.

But ... none of this will help make Unity or KDE run well over a remote X.

---

### Post by ob2s on 2017-04-27
Thanks, maybe it would be easier to remote desktop in ? Is there a util that I can use to do that ? Thanks

---

### Post by TheFu on 2017-04-27
**x2go**, but you can't use Unity with it.  3D accel needs direct access to the hardware and that just isn't possible over a network link.  
Well, that isn't entirely true, but there are complex requirements to get it working. SPICE is the protocol. To my knowledge, it only works with KVM VMs.

On the same LAN, your best bet is to run a light Linux inside a VM (assuming you won't dump Windows), and use normal X11 remote features. Over a WAN or unsecured WAN, then X11 isn't a good choice.  x2go is the best solution I've found.   But none of these will support Unity or any desktop that requires 3D accel GPU access.

---

### Post by sp40140 on 2017-04-28
I wonder if something like TeamViewer would work for your use case or not!

---

