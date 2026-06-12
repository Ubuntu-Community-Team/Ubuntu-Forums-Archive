---
title: "FROM ubuntu remote desktop TO windows xp"
date: 2005-11-17
forum: Desktop Environments
---

### Post by holiday on 2005-11-17
I want to use Ubuntu  to run my XP workstation at work. I have done this using TNVC from a Fedora installation, but see that Ubuntu has a 'Remote Desktop' feature. However from what I can see in the Ubuntu feature's configuration, and all the googling hits I've found, are for XP remote desktop TO ubuntu.  

I don't mind installing TNVC at all, but I'd rather use a Ubuntu standard if one exists. 

Does one?

---

### Post by Roman27 on 2005-11-17
How about turning on Windows Remote Desktop?

You can do that by right-clicking on *My Computer*, then click on *Properties*, and go to the *Remote* tab in the *System Properties* window.  If you are using Windows XP Professional, you should have an option under *Remote Desktop* to **Allow users to connect remotely to this computer**.  Selecting this option will turn Windows XP Pro into a single user terminal server.  You'll have to use VNC or something else if you're using Windows XP Home Edition.

On the Ubuntu side, you merely have to go to *Applications* -> *Internet* -> *Terminal Server Client*.  You can use the RDPv5 protocol and enter in the IP address or name of your Windows XP Pro PC.  That's all there is to it!

---

### Post by holiday on 2005-11-17
Thank you. Terminal Server Client, of course. 

I have enabled Remote Desktop on my windows machine, but when I try to use TSC I still can not connect using the address provided by my RD config screen. 

I have tried all the protocols. Perhaps I need to install something other to connect? Or perhaps I need to connect to the VPN first? I have been through the VPN install with other distros and find it tedious. I may have to go through that again, but prefer the more simple solution your reply suggests is possible. 

I hope I'm missing something.

---

### Post by dbott67 on 2005-11-17
I have successfully done this on a number of machines, although I install UltraVNC on the Windows computers.  I normally don't use the XP remote desktop, as it 'blanks' the host computer screen (for security reasons) and I typically use it for remote assistance.

Anyhow, there are a few possiblities:

1. If it's only for you to access, the you can use XP's remote desktop (although it's only available in XP Pro, not Home version).  Make sure that any software and hardware firewalls are configured to allow the RDP port (3389, I think) traffic through.

2. If you want to interact with another user remotely, then you'll need to install one of the VNC variants (Tight, Ultra, Real, etc.) and make sure that ports 5800 & 5900 are not blocked.

The other major benefit of VNC is that you can install it on virtually any platform (OSX, Windows 95-XP, Linux... Commodore64... oops)

-Dave

Here's a screenshot from this past summer of me connecting from my Ubuntu 5.04 computer (at work) to my home OSX computer and a Windows 2000 lab computer at work.

---

### Post by Roman27 on 2005-11-17
[QUOTE=holiday]...  I have tried all the protocols. Perhaps I need to install something other to connect? Or perhaps I need to connect to the VPN first? I have been through the VPN install with other distros and find it tedious. I may have to go through that again, but prefer the more simple solution your reply suggests is possible.  ...[/QUOTE]

There's no need to try any other protocol other than RDPv5.  That's the protocol used by Windows XP Remote Desktop and any other current and updated Microsoft Terminal Server.

You will definitely need to make sure that you can communicate with the other machine.  The details of that are up to you and your network layout both at home and work.  One way to do it might be to simply open the RDP port 3389 (as dbott67 mentioned) to allow incoming traffic to reach your Windows XP machine at the office.  Another way would be as you suggest to create a VPN tunnel into the company network somehow.  There are many different network setups out there.  But whatever you choose, you'll need to be able to have direct communication with the Windows XP machine over port 3389 in order to use the solution I presented.

---

### Post by RikoW on 2005-11-18
I connect regulary from my laptop running Ubuntu to my desktop PC at work running  XP. RDP connections are enabled on the windows side. On Ubuntu I use rdesktop via the terminal server client or via grdesktop as GUI.

When I want to connect from home, I have to use a VPN connection to work to be able to access by desktop PC (or any other terminal server) as they are behind a firewall, that blocks all traffic from outside the work network.

Maybe, that is the case for you also?

I had no problem installing and setting up the CISCO vpn client which is distributed through out IT department.

Cheers,

            Riko

---

### Post by holiday on 2005-11-30
Ok so when connected to my employer's VPN, I *can* get a TSC session.  Wonderful! Thank you. 

However : pptpconfig reports  this 

#modinfo: could not find module ppp_mppe, but I thought ppp_mppe was in pptp_linux??? And it does not appear in apt-cache search. There doesn't seem to be a problem.

However another issue : On connection, pptpconfig *overwrites* my /etc/resolv.conf with what I assume to be the VPN's DNS. Since my employer is on a different ISP, this disables my email - small issue, but an annoyance.  How do I fix that?

---

### Post by holiday on 2005-12-02
Ok so I made a copy of my /etc/resolv.conf before making the vpn connection, and then after making the connection I go 
# cat /etc/resolv.conf.bak >> /etc/resolv.conf

And I'm whole again...

Also, I have to say that when my laptop came back from the shop, I had a TSC to my work XP workstation running in fifteen minutes. It would have been less if I'd remembered sooner -duh- my firewall. 

Good work, Ubuntu.

---

### Post by holiday on 2005-12-02
Oh did I mention that one of the things that makes Ubuntu a great distro is this community.

---

