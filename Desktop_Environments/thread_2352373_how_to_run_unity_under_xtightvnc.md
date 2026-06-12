---
title: "how to run unity under xtightvnc"
date: 2017-02-11
forum: Desktop Environments
---

### Post by Skaperen on 2017-02-11
i would like to run *unity* (or *xfce* or *lxde* or *cinnamon*) under *xtightvnc*.  i plan to run many instances of it (locally, on my servers, in the cloud) and switch among them from remmina.  **how should i do this to get them running?**  i will be scripting this in *python* and using *ssh* and/or *openvpn* to make the connections more secure.

---

### Post by TheFu on 2017-02-13
Could I convince you to look at x2go instead?  x2go uses the NX protocol which includes ssh by default.  It feels 2-3x faster than any VNC I've seen.  There are a few different NX implementations available for Linux, but they aren't compatible with each other - freenx and NoMachineNX and x2go are the most well-known.  I've tried all. x2go works best, by far.

Smart to use ssh/openvpn for any vnc-based solution. 

I've never used remmina.  x2go has a friendly GUI to setup and run different connections from the client.  ssh keys are honored.  The only downside to x2go is the limited compatible clients.  OSX, Windows, and Linux work, but there aren't any iOS or Android clients.

As for Unity - that DE requires access to GPU hardware. Virtual desktops don't allow that access so the well-proven path is NOT to attempt running Unity.  KDE, XFCE, LXDE, and plain window-managers like openbox, fvwm, and others do work well.  [http://wiki.x2go.org/doku.php/wiki:repositories:ubuntu](http://wiki.x2go.org/doku.php/wiki:repositories:ubuntu) has the PPAs you'd want to use.  There are instructions for the client and server setups there.  Get ssh working between each client to the server before you start. ssh setup is NOT included in the x2go stuff, but required.

I cannot help with VNC stiff except to say, make certain the VNC server used the --localhost option. This will prevent any connections that aren't going through a tunnel and ending on the remote machine from connecting.  Then only 1 inbound port needs to be opened and secured.  If you use ssh + ssh-keys + fail2ban, the security is effectively done. Don't allow password-based authentication on the internet. Be certain to disable that in the sshd_config file after everything is setup and working.

---

### Post by Skaperen on 2017-02-15
i will have a look at x2go.  i am not committed to much other than everything is linux.  i don't understand where *openvpn* fits into this.  i will be initially running everything on the same machine then the same LAN. the final thing will have parts in the cloud making use of the *openvpn* infrastructure i have now which i can launch any time i need it (up to 105 *openvpn* tunnels interconnecting 14 regions plus 14 more connecting my LAN to each cloud region).  the cloud-to-cloud parts are in AMIs and ready to go.

the vpn stuff is for multiple desktop capacity, not remoting, but some remoting among my desktops is inevitable.

---

### Post by TheFu on 2017-02-15
Don't need a VPN with x2go. ssh is built-into the protocol which provides the tunnel and authentication for the remote-desktop.

My rule of thumb about this stuff is ... openvpn is for end-users who need everything encrypted and ssh is for admins who know what is and isn't encrypted.  If you want people to have all their traffic routed through a remote system, then you need openvpn. If just the remote desktop needs to be encrypted, then NX is all you need since it has ssh built-in (which cannot be disabled to my knowledge).

You'd have to do some testing, but I'd think that x2go + openvpn will be slower than openvpn + VNC.  I'm positive that x2go is faster.  Double tunnels ssh+openvpn are almost always slower.

BTW, I've accessed my remote x2go from 5 continents. Having it in the local region really isn't necessary.

For an admin-like person, ssh, x2go, scp, sftp, rsync generally provide all the security necessary between different systems. There are CLI and GUI tools for each (except x2go, which is a GUI since ... well, it provides a remote desktop). These tools are a way of life for Unix admins.  They can be thought of as ad hoc VPNs available on any system running sshd.  Hoping from system to system to system is trivial AND secure.

I should also be clear - I've never run more than 1 x2go session at a time. My purpose for using it is to get access to my data from anywhere in the world in a secure manner. My current location is the only suspect - not my remote server.  Any security required by the remote server running my "desktop" is a completely different thing and setup outside the x2go stuff.  Effectively, when using x2go, everything is now happening on/from the remote system.  x2go, based on NX, only needs an ssh port opened and secured. Certain things like audio and local printing want a reverse ssh port available to work, but there are other methods for those things.

BTW, x2go can be run inside a crouton chroot under ChromeOS on a cheap intel-based chromebook. These things can be picked up for $70-100 now.  I believe this is the single most secure networked, laptop, configuration in the world today, provided you don't login to any google accounts on the chromebook and only use the guest account. The security provided by chromeOS is substantial when tied to the TPM chip used by most chromebooks.  The only issue I've had is that google pushes out OS updates whenever they want and there isn't any way to stop (or delay) it if the machine connects to the internet. Those pushes can make crouton fail and need to be updated at very inconvenient times.

Alas, I'm assuming travel for you which may not be the situation like it is for me.

---

### Post by Skaperen on 2017-02-17
does *NX* just make a connection over *SSH*?  that sounds like just a secure connection and not a true tunnel (which emulates a point-to-point network circuit).  any protocol that runs over *TCP* can be run over *SSH* or *STunnel* to get a secure path without a tunnel like *OpenVPN* makes.

making a connection over *TCP* which *SSH* or *STunnel *can do, allows using the many tools to make connection paths go many ways (such as _*TCP over HTML*_).  even *OpenVPN *can do *TCP* as an option, although such tools exist for *UDP* which is preferred for *OpenVPN.*

---

### Post by Skaperen on 2017-02-17
do you know anything about the NX protocol compared to VNC?  it is my long term goal to make a multiplex switcher that works inline of the VNC protocol (so i wonder if this could be done with NX).  it would listen for connections.  once connected it would watch client mouse motions near an edge spot where it would float out a menu that has buttons for target places (hosts/servers/ports).  one click and a connection is make to that place and activity traffic is passed between that place and the client.  the menu will time out in a few seconds and float back off the edge.  or the client can click again to connect to another place or move th mouse to bring the menu back out.

---

### Post by TheFu on 2017-02-18
Most companies looking for a remote desktop connection manager would deploy oVirt from Redhat, methinks.  It does remote SPICE desktops over TLS into a server farm.  oVirt is a beast to run and maintain, however.  OTOH, oVirt is very simple for end-users and I've been impressed by the performance when seeing my peers use it. They tend to be running 20+ physical servers with hundreds of VM clients in a true VDI setup.  Citrix sells something like this for their Xen-VDI stuff too.

Feel free to read the x2go code if you want to know how it works at a detailed level.  I just know that it feels 2-3x faster than any VNC+VPN and I know that ssh is secure enough for my requirements.  

Everyone I know that got it working says it is like night and day compared to VNC. x2go from 12K miles away doesn't completely suck. I know that too.

There is a downside. x2go doesn't have tablet iOS or android implementations. It may not have been ported to ARM systems running Linux either. I dunno. The Windows and Linux client implementations are solid. Don't know about OSX.

---

### Post by Skaperen on 2017-02-19
remmina supports NX.  so i could do both.  it also does RDP, though i think i will have little use for that.

---

