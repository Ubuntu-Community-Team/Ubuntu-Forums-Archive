---
title: "Remote Desktop into Windows Xp"
date: 2006-06-06
forum: Desktop Environments
---

### Post by spyke01 on 2006-06-06
Hi guys, this has probally already been asked several times, but a search only showed setting up an ubuntu box for remote connection from winblows. My job uses XP, 200, 2003, and NT 3.11(dont ask why). I need to be able to access all of these via IP address and from my nix box. Ive seen rdesktop remote desktop(probally same app), and FreeNX mentioned, which one will get me what i need?

---

### Post by aysiu on 2006-06-06
I've had no problems with TightVNC (which is available for both Ubuntu and Windows), but I'd use that only if you're on the same local network.

---

### Post by cgjones on 2006-06-06
I would use Remote Desktop, since it is already part of Windows. Make sure that Remote Desktop is turned on on the machines you want to access.

**Internet** >> **Terminal Server Client**

---

### Post by Jason_25 on 2006-06-06
For XP, 2000, and 2003 you should use the terminal server client under internet.  It supports RDP, which is much faster than VNC.  I don't know what you would use for windows 3.1.

---

### Post by spyke01 on 2006-06-06
What about for VPN, i can install anything on these servers so tightVNC is out, terminal server looks like a good option, ill have to check it out. I had forgotten that the network has to be accessed via VPN, so now i gotta find a way to get a VPN client, im going to check and see if i can find one, cisco probally has one, but if anyone knows off the top of their head please let me know.

---

### Post by SuperMike on 2006-06-06
Look up rdesktop. And for the GUI to rdesktop command, lookup tsclient. Then, remember that XP needs to have this feature turned on in the System control panel or you won't be able to connect to it.

apt-get rdesktop
apt-get tsclient
rdesktop --help --> gives you options
tsclient --> fires up the GUI front-end to either VNC or rdesktop, your choice

No need to use VNC, which is the slower option.

---

### Post by musicinmybrain on 2006-06-06
[QUOTE=SuperMike]Look up rdesktop. And for the GUI to rdesktop command, lookup tsclient.[/QUOTE]

Tsclient is decent, but I highly recommend grdesktop as an rdesktop frontend. Try them both and use whichever you like better.

---

### Post by spyke01 on 2006-06-07
thanks alot m8s, i really like the grdesktop client thanks again

---

### Post by mgmiller on 2006-06-07
Just my 2 cents.  I use the terminal server client to connect to remote desktop at my work XP pro box.  I found that if you have the bandwidth, once the terminal server client window is displayed, but before you connect, on the general tab, under protocol, select the RDPv5 protocol, then go to the display tab and select under colors, use specified color depth and change it to High Color (16 bit).  Once you make the connection, the session is exactly like a remote desktop session done from another Windows XP box.  No new packages are needed and it works great.  
On an aside, how did you get the VPN to work?

---

### Post by spyke01 on 2006-06-07
haven't got VPN working yet, still looking for one

---

### Post by alaman on 2006-06-07
Cisco has a VPN client - 
[http://www.cisco.com/en/US/products/sw/secursw/ps2308/index.html](http://www.cisco.com/en/US/products/sw/secursw/ps2308/index.html)

You may need an account to download.  It works fine in Breezy (I haven't tested it in Drake yet).

---

### Post by spyke01 on 2006-06-07
[QUOTE=alaman]Cisco has a VPN client - 
[http://www.cisco.com/en/US/products/sw/secursw/ps2308/index.html](http://www.cisco.com/en/US/products/sw/secursw/ps2308/index.html)

You may need an account to download.  It works fine in Breezy (I haven't tested it in Drake yet).[/QUOTE]
hmm they want you to pay for it, i think not!

heres 2 i found real quick

**KDE:** [http://home.gna.org/kvpnc/en/index.html](http://home.gna.org/kvpnc/en/index.html)
**Gnome:** [http://fedoranews.org/mediawiki/index.php/Fancy_GUI_for_your_Cisco_VPN_client](http://fedoranews.org/mediawiki/index.php/Fancy_GUI_for_your_Cisco_VPN_client)

---

### Post by SuperMike on 2006-06-07
[QUOTE=spyke01]haven't got VPN working yet, still looking for one[/QUOTE]

Try vpnc. It's command-line. I've written "gvpnc" (GNOME front-end for VPNC) but I need to give this project to another programmer to manage and grow it.

I love vpnc and use it a lot.

---

### Post by alaman on 2006-07-21
I've actually switch to vpnc as well.  It works great.  I did have initial issues because I included a the space at the end of the line on the group name (dumb mistake)...once I deleted it - I've not had an issue.

---

