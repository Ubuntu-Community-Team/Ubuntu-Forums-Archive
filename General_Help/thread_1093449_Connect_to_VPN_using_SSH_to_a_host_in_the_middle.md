---
title: "Connect to VPN using SSH to a host in the middle"
date: 2009-03-11
forum: General Help
---

### Post by hornairs on 2009-03-11
Hi everyone

I would like to connect to a corporate VPN network from my current ISP which actively blocks VPN connections (a university). Right now I am VNCing to another box outside this network, from there connecting the VPN and then from there RDPing to the hosts I need to work with. This sucks.

What I want to do is use that external host to transport my VPN traffic through an SSH tunnel, so I can create the VPN connection from my local box to the corporate site and just route it through this tunnel so it won't be blocked.

I have root on my local box and on the remote box, but not at the company. I think if I did at the company I would just tunnel right to them and VPN in as describe in a multitude of places on the web, but there is no SSH server there. So I think the solution I've described above would work, but feel free to point out others!

Also, the server has a 100Mbps port and I'm on university LAN at 100Mbps also, so do you think I'll notice any slowdowns?

---

