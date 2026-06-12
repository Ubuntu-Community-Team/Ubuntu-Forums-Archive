---
title: "Disabling monitor detection for headless machines"
date: 2013-03-20
forum: Desktop Environments
---

### Post by DelMurice on 2013-03-20
I have several machines I've been trying to get working for use as a render farm.   However, been hitting a wall with then when they boot without a monitor, they won't start LXDE.  I tried GRUB_CMDLIME_LINUX_DEFAULT="quiet splash nomodeset" in the /etc/default/grub file, but it yielded no display at all, not even a text login prompt.

I'm running Lubuntu 12.10 x64 on several HP Compaq dc7800fdd's with c2d, 1gB ram and 80gb HD.  Everything works just fine if I boot with a display connected. But it's rather unfeasible due to space to have a monitor connected to every one of them.  Each one needs XFDE runniong so I can start Blender as render slave, and be accessible with VNC.

Any help would be much appreciated.

---

### Post by DelMurice on 2013-03-21
I think after getting a major headache over this for two days and reading for hours about fixes that didn't end up working.  I'm just going to install XP on all these machines and say bye to Linux altogether.   Whoever decided to make it so it won't work at all without a monitor needs to examine his logic, and maybe do some research on how people would use Linux.

---

### Post by DelMurice on 2013-03-21
Well just disregard the previous.  Still using lubuntu.  I didn't solve the problem but found a workaround for now. I just set the power to hibernate and made sure they won't auto-update. I tried using a simple frame-buffer XVFB with x11vnc, it worked for vnc, but lacked the opengl needed for blender.   But if anyone is looking for headless operation and not concerned about running blender can try this without hacking at anything.

$sudo apt-get install openssh-server openssh-client samba x11vnc xvfb

I included openssh so x11vnc can be started remotely if needed. Samba so it uses WINS resolution so you don't have to figure out the IP address, just use the name of the box. xvfb to provide x11vnc with a frame buffer.

just use your favorite ssh client (putty in my case) and type:

$x11vnc -forever -create -passwd <password>

It will provide you with a very basic X environment with only a xterminal, but you can start your favorite file manager by typing it at the prompt.
Getting gnome or whatever going on top of it is a little more than I care to explain (and figure out), but feel free to add to this.

---

