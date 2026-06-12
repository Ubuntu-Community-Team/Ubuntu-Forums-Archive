---
title: "Remote Desktop for Headless Server"
date: 2013-11-14
forum: Desktop Environments
---

### Post by Chris Calderon on 2013-11-14
I am planning on building a server and putting ubuntu server on it. I want to set it up so I can log into it remotely with something like TurboVNC, but I don't want to have a desktop running on the server. So I guess I'm asking if it is possible to run X11 in the background, and install gnome, GPU drivers, and virtualgl from a framebuffer console?

---

### Post by TheFu on 2013-11-14
If you are going to have a remote desktop, then the code that make a "desktop" will need to run on the server somewhere (just not with a GUI).

Rather than VNC stuff - take a look at FreeNX as the server. You will thank me for the security AND better performance. I use NX from around the world as a remote desktop for "productivity" applications. Works well enough from most hotels 10K miles away.

Oh, and completely forget about GPU anything. That has nothing at all to do with this sort of environment.

**Update - a day later after lots-o-reading.**
* There are methods to pass VGA cards through with certain hardware - VT-d is the core requirement with bios, MB, select video cards, and CPU support required.  Seems a few people have applied the necessary patches to make this work with nearly 95% GPU performance to a single VM. The hostOS needs to be connected to a different GPU (it seems).
* [http://www.virtualgl.org/About/Introduction](http://www.virtualgl.org/About/Introduction) provides some insight as to how TurboVNC+VirtualGL work. Interesting. They do not discuss security/tunneling at all and it appears that direct access to the GPU is necessary - so .., I have doubts about it working in virtual machine environments - which is the only way that I run/want remote desktops. Others may be happy to dedicate an entire physical machine to just 1 OS, not me.

So - anyway - there appear to be some smart folks attacking the performance issues for remote desktops from 2 more methods. I am curious.  I've used Spice+KVM for about a week, but ended up dropping back to NX.

---

### Post by sheridanm962 on 2013-11-15
A friend of mine runs a Ubuntu Server, we both can connect via OpenVPN and use PuTTY on Windows, I'm sure there are other ways of connecting as such too. 
The weird thing here is that he's running his server with a Radeon HD 7950, so I'm like "That's a waste...".

Anyway good luck with everything, at least you'll do better than me trying to figure out that I can't run something like VNC... Pointless.

---

### Post by ian-weisser on 2013-11-15
> **Chris Calderon said:**
> I want to set it up so I can log into it remotely with something like TurboVNC, but I don't want to have a desktop running on the server. So I guess I'm asking if it is possible to run X11 in the background, and install gnome, GPU drivers, and virtualgl from a framebuffer console?

Sure it's *possible*. You can install anything you want from a console. You can administer the server quite well from the console, too.
X11 really doesn't run "in the background." It's either on or off. You can remotely connect to an X session using SSH as well as VNC.
I find remote-display sessions across the internet to be a bit (annoyingly) laggy. Remote consoles, however, tend to be quick and responsive.

Most services designed to run on a server shouldn't require a GUI environment at all. That's why Ubuntu Server doesn't include one.
Most common home-server applications, like torrents, media,  gameservers, and backups, don't require a GUI on the server backend. The  GUI frontend on your local machine is usually capable of automatically  connecting to the remote backend quite seamlessly.

As said before, unless one of your applications is going to use a GPU, you won't be using it. If you generated super-high-quality video, then encoded it and sent it across your network, would your bandwidth be able to support networking that video to another machine? And would that machine be able to decode and render it?

---

### Post by Chris Calderon on 2013-11-16
Wait, how do desktop environments work? is X11 the same as x.org and x server?

VirtualGL / Turbovnc do all 3d rendering and/or gpu work on the server, then compress rendered images and send them through the network. It is supposed to be pretty fast.

---

### Post by ian-weisser on 2013-11-16
Right, X, X11, x.org, X server. There have been forks and merges and renames and more. But it's all X. Your desktop (Unity, KDE, etc) is on top of X. Your application is on top of that. If your application requires X, then you must install all of X.

VNC is fast on a LAN, or in the same subnet on the same network. Across subnets and the internet, through layers of routers and switches it gets slower and slower. Been there.
Remember that raw VNC is vulnerable - I always use an SSH tunnel. See [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

### Post by TheFu on 2013-11-16
> **Chris Calderon said:**
> Wait, how do desktop environments work? is X11 the same as x.org and x server?

VirtualGL / Turbovnc do all 3d rendering and/or gpu work on the server, then compress rendered images and send them through the network. It is supposed to be pretty fast.

Today was the first that I'd heard of VirtualGL.  Since I run most desktops inside a virtualmachine, direct access to the GPU just isn't an option ... at least it hasn't been until the VT-d stuff was added to CPUs, MB, and support for selected GPUs.  See my updated comment above.

Compression of rendered images has been part of remote desktops for years ... probably a decade. I remember reading about VNC around 2000 or was it 2002?  Regardless, it still sorta sucks.

See figure 2.2 here: [http://www.virtualgl.org/vgldoc/2_1_1/#hd003001](http://www.virtualgl.org/vgldoc/2_1_1/#hd003001) for a nice overview of the VirtualGL setup.

Just read that TurboVNC connections are unencrypted [http://www.virtualgl.org/vgldoc/2_1_1/#hd009006](http://www.virtualgl.org/vgldoc/2_1_1/#hd009006), so using a VPN or ssh tunnel is still a requirement. Regardless, I plan to test out this new set of remote access tools in the next few days, but if direct GPU access is required on the server-side, I am SoL.

---

