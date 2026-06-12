---
title: "Can SSH/ping server by IP, but not by hostname?"
date: 2009-06-05
forum: General Help
---

### Post by Nixie Pixel on 2009-06-05
Hello, I recently changed ip addresses on my network, after installing a new router. My address range went from 192.168.0.x to 192.168.1.x.

My Ubuntu Server's static IP changed from 192.168.0.69 to 192.168.1.69. I can ping/SSH the Server at the new IP address with no issues. However if I try to ping/SSH to the hostname, it is being resolved to 192.168.0.69.

Where should I be looking for this, and why did it not automatically update when I changed IP addresses?

Thanks!

---

### Post by bacardiandwatermelon on 2009-06-05
sounds like the dns is still pointing to the old one to me.. You may have to restart you router or flush your dns if reaching it from a windows machine..

---

### Post by Nixie Pixel on 2009-06-05
I rebooted my router, and I am connecting from multiple linux boxes, all with the same problem.

What could be the issue?

---

### Post by The Cog on 2009-06-05
Have a look at your /etc/hosts file to see if the hostname is listed there. If it is, correct it. If not, have a look at /etc/resolv.conf to see who is providing the DNS lookup service.

---

### Post by Commander_Keen on 2009-06-05
> **Nixie Pixel said:**
> Hello, I recently changed ip addresses on my network, after installing a new router. My address range went from 192.168.0.x to 192.168.1.x.

My Ubuntu Server's static IP changed from 192.168.0.69 to 192.168.1.69. I can ping/SSH the Server at the new IP address with no issues. However if I try to ping/SSH to the hostname, it is being resolved to 192.168.0.69.

Where should I be looking for this, and why did it not automatically update when I changed IP addresses?

Thanks!

Hi.. Question.
 Since you bought a new router, why not just log into the router and change the IP address back to 192.168.1.x, instead of useing x.x.0.x?

---

### Post by Nixie Pixel on 2009-12-05
Thanks for the help, and sorry I never responded to this.

My main goal was to figure out if and when Linux/Ubuntu automatically can resolve a hostname to an IP address on the local network, and when the hosts file has to be updated manually.

Can someone help me understand the difference between Linux and Windows in this regard?

Thanks!

---

### Post by amturnip on 2009-12-06
> **Nixie Pixel said:**
> My main goal was to figure out if and when Linux/Ubuntu automatically can resolve a hostname to an IP address on the local network, and when the hosts file has to be updated manually.

Can someone help me understand the difference between Linux and Windows in this regard?

There needn't be any difference... You can use Samba to participate in a Windows workgroup network.  

Another way to avoid editing many /etc/hosts files is to set up a NIS server.

---

