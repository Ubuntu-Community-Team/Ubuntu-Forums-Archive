---
title: "Remote desktop into Windows 2003 running Terminal Services?"
date: 2006-04-14
forum: Desktop Environments
---

### Post by drfox on 2006-04-14
I have a Windows 2003 network at work and I log in using Remote Desktop/Terminal Services. Can I have a RDC connection with Ubuntu, and see and interface with Windows programs running on my server?

Larry

---

### Post by ronmarley1 on 2006-04-14
Larry,
I can't remember if it's installed by default, if it is, Click on Applications, Internet, Terminal Server Client.  If it's not, click on Applications, Add Applications.  Enter your passord and the click on Internet, More programs... and check the box next to Terminal Server Client and the click Apply.  This app. uses RDP and VNC protocols.

---

### Post by drfox on 2006-04-15
Thanks Ron! That worked like a charm. Can you help me connect to my office VPN (running Windows 2003 Server) from home (running Ubuntu)? 
I've loaded pptp-config and can connect to my VPN router, but only as Root. When I log in as a user, I can't write a pptp config file. Even as Root, I'm not sure of the settings in RDC to log on to my network when I'm connected with PPTP.

Thanks in advance.

Larry

---

### Post by ronmarley1 on 2006-04-17
[QUOTE=drfox]Thanks Ron! That worked like a charm. Can you help me connect to my office VPN (running Windows 2003 Server) from home (running Ubuntu)? 
I've loaded pptp-config and can connect to my VPN router, but only as Root. When I log in as a user, I can't write a pptp config file. Even as Root, I'm not sure of the settings in RDC to log on to my network when I'm connected with PPTP.

Thanks in advance.

Larry[/QUOTE]

I'm not sure I can help here.  We have a Cicso VPN, and I could not get the the Cicso client to work.  So, I switched to PPTP and (after quite a bit of work) was able to connect to our PIX box.  However, I was never able to browse the servers on the network.  I got busy with a couple of other projects, and since I was able to VPN in with Window$ without problems, I quit playing around with it (for now).  Maybe this link will help?  [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)
Maybe post a seperate thread to this forum?
Good luck, and sorry I can't help more.

---

### Post by hankyknot on 2007-07-25
have you tried hamachi?

---

