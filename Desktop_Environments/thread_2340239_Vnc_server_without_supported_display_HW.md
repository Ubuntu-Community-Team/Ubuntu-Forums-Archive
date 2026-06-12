---
title: "Vnc server without supported display HW??"
date: 2016-10-16
forum: Desktop Environments
---

### Post by rick3332 on 2016-10-16
I am trying to setup a headless box with no  graphics HW. It is to be accessed via VNC. I am running lubuntu-desktop because it is resource light.

- How SHOULD/can this be done?
- can this be done so that I get some type of GDM login?
- The server needs to run non-gui most of the time to preserve resources, but have gui enabled/disabled from cli via ssh as needed and hopfully without reboot.


This question is for an Orange pi PC running Armbian Xenial. I upgraded the kernel to 4.7.3 to provide (mostly?) stable btrfs, but lost the display driver (not yet available in 4.7.3, only in the armbian legacy 3.4 (android?) H3 kernel). 

On other boards I have used x11vnc to access the native X running on HW. Without a working display HW X will not start and that strategy will not bear fruit. 

I chose to try tightvnc-server. I have not been able to figure out how to get it to work like the native server (start at boot and let user login.)

I did eventually manage to make it work by running tightvnc-server as a specific user through ssh.

Ideas?

---

### Post by TheFu on 2016-10-17
No login GUI.  The ssh connection/tunnel will be the credentials. Don't use VNC directly, always go through an ssh tunnel.

VNC is one option. Use the --localhost option on the server to ensure nobody that doesn't use an ssh-tunnel can connect. VNC network connections aren't sufficiently secure. No encryption. ssh-tunnel is needed.

Or use x2go.  It uses the NX protocol which includes ssh by default.  For most people, x2go/NX is 2-3x faster than VNC.

I have ZERO clue what an Orange Pi is.  If it is low resources, use ssh, not any GUI.  Plus ssh is needed for all these solutions anyways, so get that working before trying x2go, which uses the same port for connections. It will also honor ssh-keys, if you have them.

---

