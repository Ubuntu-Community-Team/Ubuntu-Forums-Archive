---
title: "Remote connection to  ubuntu 7.10"
date: 2008-02-27
forum: Desktop Environments
---

### Post by cskalyan on 2008-02-27
Hi Folks,

I have installed Ubuntu 7.10 recently. I am trying to connect to my ubuntu machine remotely. Here is what I was trying to do.

1.I took the dyndns account and got the hostname.domainname.

2. In Ubuntu hosts table I have added this entry with the ip address.

3. I have enabled Remote Desktop in Ubuntu.

When it comes here is what I have.

CableModem - --> D-Link 524 Wireless Router -- > Ubuntu PC


Wireless router has assigned the ip 192.168.0.101 to my ubuntu PC.



From another windows work station, If I use Putty and try to connect to the hostname.domainname what I got from dynDNS it fails.

I am able to SSH remotely with the ip 192.168.0.101

Also. I enabled the Portforwarding in the router. Settings are as follows:

Virtual Server

SSH 

PublicPort:22
Private Port :22
Private ip: 192.168.0.101
Protocol:TCP.

Please help me on this.

---

### Post by OffAxis on 2008-02-27
> From another windows work station, If I use Putty and try to connect to the hostname.domainname what I got from dynDNS it fails.

I am able to SSH remotely with the ip 192.168.0.101

From within the Local Area Network, right?

Instead of trying to connect to the hostname.domainname, try using the WAN IP of your router explicitly. Hit up [http://whatismyip.com](http://whatismyip.com) if you don't know (or just check in your router configuration). Feed that IP into putty and see if it'll connect.

---

### Post by cskalyan on 2008-02-27
I tried that option. Same result.

I did a nslookup of my hostname.domainname and it displayed the ip address.

I have tried to connect using that ip address.

---

### Post by OffAxis on 2008-02-27
nslookup returns the entry from dynDNS; which may itself be faulty.

Try looking up your WAN IP on the router or at that website.

If it's the same, then it's an issue with your port forwarding at the router.

---

### Post by cskalyan on 2008-02-27
Thanks for the response.

Actually WAN ip and the ip returned from the link you have provided are the same.

Could you please me know if there is any URL you know of to do the port forwarding for D-Link DI-524 model.

I googled and got the link from portforwarding.com and followed the instructions, still not working as expected.

---

### Post by OffAxis on 2008-02-27
> Actually WAN ip and the ip returned from the link you have provided are the same.
Sorry, I should have been clearer; I meant the WAN IP and the one returned from the nslookup.

If those are the same then you should retrace your steps;

**Check the server**

check that your server is still 192.168.0.101
```
ifconfig
```
check that port 22 is forwarded to it in the router setup
check that it is 'Always' forwarded (in the setup screen)

**Check the client**

make sure putty is still using port 22
make sure there's no errors when entering the server's WAN IP

login to the server from the private IP (192.168.0.101) just to make sure that the sshd is running (or you can run **ps -C sshd** on the server) 
and then try to hit the WAN IP.
There's no issue of being on the LAN when trying to hit the ssh server's WAN IP; it should work.

As for the router setup how-to, that's about the best you'll find. There's not much to it. There's just some trivial oversight or type-o that you're making in the process, that's all.

As a last ditch effort you could try enabling UDP and TCP on port 22 (even though ssh only uses TCP).  You could also forward all the ports to the server and see what happens. NOT THAT YOU SHOULD LEAVE IT THAT WAY, but it may help when troubleshooting. There could be also be a bug in the router regarding this, so make sure you're running the latest firmware.

---

### Post by cskalyan on 2008-02-27
Thank you very much..

I am at work. When I go back home, I will test and post the reply.

Appreciate your help.

---

### Post by cskalyan on 2008-02-28
I am able to connect using my dynDNS hostname.domainname from a remote machine using Putty.

Only thing I changed in the router was to make the Protocol type to Both instead of settings as TCP only.


One last question I have before marking this thread as solved.

How to get the static ip from the wireless router and what's the best way to set  in  Ubuntu. Everytime I restart my machine I am getting a new ip.

Yesterday I rebooted and the ip got changed from 192.168.0.xxx to 192.168.0.yyy

---

### Post by OffAxis on 2008-02-28
within the router setup you can probably assign an ip based on MAC address of your machine (check under the DHCP section, maybe the Advanced tab). 
If you need your machine's MAC you can check under the 'Status' or 'Connected Devices' for it (or run **ifconfig **on your server; it's the HW address value in the top line).

Alternatively, you could disable DHCP on your router and set up a static ip on the server with the Network Manager. As long as your gateway ip is that of your router it should be able to find the internet. It's a little more cumbersome (because every computer you connect would have to have a static address and the gateway defined). The easiest way is definitely option 1 above.
ip:192.168.0.101
subnet:255.255.255.0
gateway:192.168.0.1

---

### Post by cskalyan on 2008-02-28
Thanks

Will try that option.

---

### Post by cskalyan on 2008-02-28
Any ideas on this!!

I am able to connect to my linux box remotely from another windows box at home using hostname.domainname I got from dynDNS, where as I am not able to connect from my office network.

---

### Post by OffAxis on 2008-02-28
The ports at your office may be blocked.

If you have any other servers (like http or ftp) running on your machine (and forwarded through your router) you could try reaching those with your web browser or ftp client.

You could try a port scan on your office network, but that's a bit more obvious that you're looking for holes.

What it'd do is switch your ssh server port (in **/etc/ssh/sshd_config**) to 443 (this is usually kept open for https traffic). 
Restart your ssh server, forward that port through your router, try connecting from the LAN side (with a local address and then the dyndns entry), and then try from the office.

---

### Post by cskalyan on 2008-02-28
Dude... man!!

Thanks..

Awesome. This information really helped. I am able to connect from my office network now and also in LAN.

I really really appreciate your help.

Cheers

---

