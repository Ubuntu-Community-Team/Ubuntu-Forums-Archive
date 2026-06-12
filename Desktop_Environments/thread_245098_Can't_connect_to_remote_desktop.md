---
title: "Can't connect to remote desktop"
date: 2006-08-27
forum: Desktop Environments
---

### Post by jbahr on 2006-08-27
I'm having some trouble connecting to my remote Win XP desktop.  I'm using Kvpnc to connect to my company's VPN.  According to the Kvpnc program it is connecting successfully to the VPN.  But, when I try to connect to my PC, I just can't.  To connect, I've used Krdp (using both an rdp:/ and a vnc:/ attempt - I have RealVNC installed and running on my work PC) and TSClient.  No success with either - just get a "timed out error".  I've even tried just pinging my PC, but it just hangs there doing nothing.  My feeling is that no matter what method I use to connect, I'm not going to be able to since nothing is even "seeing" my PC.  Can anyone give me some tips on what to try to get this working?  Thanks.

---

### Post by spin2cool on 2006-08-27
Can you access your work PC from an external windows box, after you VPN in?  Does your company block the ports that VNC uses?

---

### Post by jbahr on 2006-08-27
Yes, I can connect to my work PC using another Windows PC - I've done it both with Remote Desktop Connection and with RealVNC .  I have been using the settings on that PC to determine how to set things in Kvpnc and TSClient.  I noticed that on the Windows PC - which is running the Cisco VPN client - there is a check box to "Allow Local LAN Access" - which is checked, but I don't find a similar check box in Kvpnc (under the Cisco type).  Do you think that could be the problem?  If so, do you know how I can get Kvpnc to allow access to the LAN?  Thanks.

---

