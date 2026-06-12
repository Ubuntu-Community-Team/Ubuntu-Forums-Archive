---
title: "Remote Desktop"
date: 2022-11-07
forum: Desktop Environments
---

### Post by Shibblet on 2022-11-07
Looking for some good "Remote Desktop" software that will let me log-on to my home PC (Kubuntu 22.10) from a browser.

Suggestions?

---

### Post by coley9225 on 2022-11-07
Hello shibblet.
What are you planning to use for the browser, your PERSONAL laptop, public computer,(library, inet cafe, etc), and to what end.

I am far from expert status, but public computer sounds like a bad idea, for security reasons. If your own laptop, I would install openssh on your home system, and ssh in from your laptop from wherever your at. If I'm not mistaken, you can set both systems up for x11 forwarding if you need the graphical ability. If that is an option, I would also go with passwordless login(ssh key) to further reduce the possibility of a compromised password from a "public wifi".

Again, I am no where near an expert, but seems risky to me to use a "browser based" method of connecting to your home system. Cheap and easy to just buy a 'cheap' laptop, set up a linux OS, and use ssh for connecting, based on my readings on the forums and internet searches, for security reasons.

Good luck, and stay secure.

---

### Post by Shibblet on 2022-11-07
> **coley9225 said:**
> Hello shibblet.
What are you planning to use for the browser, your PERSONAL laptop, public computer,(library, inet cafe, etc), and to what end.

I am far from expert status, but public computer sounds like a bad idea, for security reasons. If your own laptop, I would install openssh on your home system, and ssh in from your laptop from wherever your at. If I'm not mistaken, you can set both systems up for x11 forwarding if you need the graphical ability. If that is an option, I would also go with passwordless login(ssh key) to further reduce the possibility of a compromised password from a "public wifi".

Again, I am no where near an expert, but seems risky to me to use a "browser based" method of connecting to your home system. Cheap and easy to just buy a 'cheap' laptop, set up a linux OS, and use ssh for connecting, based on my readings on the forums and internet searches, for security reasons.

Good luck, and stay secure.

I want to be able to log-in from any PC.  If I am at a friends house, use his.  If I have my laptop, use that... etc.

---

### Post by coley9225 on 2022-11-07
From my understanding, Windows now has bash available, though I wouldn't know how to use it(linux only for 3 years now). If that's the case, and your friend has windows, use bash and ssh into home, most secure way, afik. If your friends use linux, then even easier. From what I've read, there is also an option to use your phone(if android) to access you server/home computer. If your like me, that's no good, can't see anything smaller than an elephant... text and keyboard too small...lol.

That said, please wait for other, more knowledgeable folks, duckhook, thefu or someone, before making a decision. I'm still 'wet behind the ears' on computing.

Anyhow, best of luck.

---

### Post by coley9225 on 2022-11-07
Years of dumb stuff(working for a living) kinda cooked most of my brain, but the few remaining cells had a thought. Consider possibly make a live usb w/persistence with your credentials. You can set up your usb with whatever you need, carry it in your pocket,and it would be usaable on any almost pc you happen to be around. Reboot to the usb, log in, and run from there.

Just another random idea, but worth thinking about.

---

### Post by QIII on 2022-11-07
> **Shibblet said:**
> I want to be able to log-in from any PC.  If I am at a friends house, use his.  If I have my laptop, use that... etc.

Oof!   I don't think you will be surprised for me to tell you that about 98% of scenarios I can see here are monumentally bad ideas, will you? 

There is a valid technical issue asked here, so go ahead.  But, ouch!  Danger, Will Robinson!

Carry on.

---

### Post by TheFu on 2022-11-08
> **QIII said:**
> Oof!   I don't think you will be surprised for me to tell you that about 98% of scenarios I can see here are monumentally bad ideas, will you?  

I agree, mainly with the browser aspect.  Allowing a web browser access to your internal LAN without any level of network authentication first is a bad idea.  HTTPS isn't security, it is privacy for the connection, not thing more.

However, if you use a full VPN like wireguard or Libreswan, then authenticate to the home VPN server before gaining access to the remote desktops inside, I'd say go for it.

OTOH, 'x2go' has clients for Linux, MacOS and Windows, uses ssh-based authentication and performs 2-3x faster than VNC or RDP all through an ssh tunnel.  So ssh with keys can be used for network authentication.  I've used x2go from 5 continents to access my home desktop like I was there (not for video or music), but everything else.  I've even connected to my Linux desktop, then ran an RDP client from it to a Windows system and it worked great, all through that same ssh tunnel.  Plus, we know how to secure ssh already, so there's no fancy new stuff necessary.  OTOH, x2go isn't a web server. It is a client/server that uses the NX protocol.

Where x2go fails is when a different client is mandated, say Android. I haven't looked recently, but there wasn't an Android client last time I looked.
But compared to RDP or VNC, x2go is like daytime vs night.  The performance is THAT much better.

About 5 yrs ago, there was a web-based remote desktop tool called guacamole. [https://guacamole.apache.org/](https://guacamole.apache.org/) Hopefully, that security nightmare died, though you could use it through an ssh-tunnel via a SOCKS5 proxy.  I access internal LAN web servers when remote all the time using an ssh-socks-proxy. This is actually fine for listening to streamed audio from my collection at home, but it isn't a full remote desktop.  I've posted my proxy script here a few times over the years.

---

### Post by ActionParsnip on 2022-11-08
What do you want to do on the server that needs the full desktop session? What activities will you do on the desktop once logged in?

---

### Post by TheFu on 2022-11-08
> **ActionParsnip said:**
> What do you want to do on the server that needs the full desktop session? What activities will you do on the desktop once logged in?

He's been around here a long time and certainly knows about ssh already. 

Sometimes, a desktop is very useful when remote.  When I'm traveling, I take a minimal system with no important data on the trip (confidential data loss or stolen data is a major worry), then use x2go back into my home desktop to stay connected from anywhere, like I'm still back home.   If the remote connection is ISDN speed or better, that is sufficient for NX-based remote desktops doing office/admin work. Of course, direct ssh and ssh-based access is more network efficient.  Most Linux file managers support sftp:// URLs, so accessing data remotely isn't hard between those and sshfs and rsync.  But sometimes, we don't want the data local. It is safer back on the system, not traveling around with us.

To me, a remote webapp like Guacamole should never have been created due to all the security failures in browsers, webservers, and using a protocol that has so many likely attack vectors.  Basically, guacamole is like telnet or plain FTP and shouldn't be used since around 2000.  Obviously, opinions on that differ.

I run a honeypot webserver and see many thousands of attacked against it daily. There's no reason for anyone to access that server - none. It isn't published.  Anyone who does get there is looking for some back door into the network, by definition, and their web GET/POST commands show them being extremely nasty.  Right now, there are thousands of requests trying to gain access using the SSL error published last week.

Additionally, when I see thousands of HTTP requests like this from thousands of different IPs from different subnets around the world:
```
45.79.128.xx - - SOME-UGLY webserver LOGS
``` what should a security minded admin think?  The forum malicious posting checks wouldn't let me post the logged text above. 
Or this one:
```
185.83.144.xx - - SOME-MORE-UGLY webserver LOGS
```
There are thousands of *aws* URLs requests looking for configs, credentials, and the forever failed security of php-based webapps.  Right now, that 182.x.x.x subnet isn't being very nice to my honeypot.  About 500 other systems are sending the exact same http requests from all around the world.   They don't know it, but the honeypot website is 100% static and using read-only NFS storage. Even if they get passed the web server and gain full root access to the OS, they can't change a thing in the website.  ;)  of course, they could remount the nginx settings file system to be re-write and point to a different location on the server where they place their files, but that seems to be beyond most automated tools.

Average end-users have no idea what is happening over the internet with the constant cracking attempts that every website sees every second.  Don't put a remote access webapp on the internet.  Please.  Just don't.  The webapp will have bugs which can be exploited. The entire LAN will be hacked.  It isn't a question of "if", but "when".

---

### Post by Shibblet on 2022-11-08
> **ActionParsnip said:**
> What do you want to do on the server that needs the full desktop session? What activities will you do on the desktop once logged in?

Primarily use my home-based desktop software, and access my files.

For example:  A client calls me up when I am "away from the office," and has a couple of changes to a flyer that I have been working on.  Without having to leave where I am, I can log-in to my desktop, pull up the flyer files, make the changes, and then email proofs and products to the client.  In other words, use my home computer where and when I need it.

I always find myself saying things like "This would be so much faster if I were on my home computer..."  Instead of trying to patch-work something together on someone elses computer.

---

### Post by TheFu on 2022-11-08
> **Shibblet said:**
> Primarily use my home-based desktop software, and access my files.

For example:  A client calls me up when I am "away from the office," and has a couple of changes to a flyer that I have been working on.  Without having to leave where I am, I can log-in to my desktop, pull up the flyer files, make the changes, and then email proofs and products to the client.  In other words, use my home computer where and when I need it. 

While true, colors aren't exactly the same and never correctly reflect reality over any remote desktop.  None of them handle it well, especially over slower connections, say under 20Mbps symmetric.  Upload bandwidth on each side will be the limiting factor.  But I know you won't believe me until you see it for yourself.  For working on spreadsheets and sending emails, any of the remote desktop tools is fine with enough bandwidth.  x2go is just does more and better compression - it also allows finer control over the quality of the images that the other protocols don't provide.

As for accessing files, any Linux file manager can to that using sftp:// URLs or with winscp (also using sftp) from any Windows machine, provided ssh-server is installed and the needed port is opened and forwarded to the LAN system correctly.  Not hard, but not automatic either.  I've seen people get this setup in 3 minutes ( is was easy for them) and I know 2 people who couldn't grasp the idea of port forwarding and wasted over a year - without success.  1 guy had a head injury that left his mental capacity impaired like a stroke could and he was trying to deal with double-NAT.  Eventually, he moved and got an ISP that didn't require double-NAT and he got remote ssh working quickly.

If your ISP only provides private NAT'd IPs, usually on the 10.x.x.x subnet, also called "Carrier NAT", then you'll never be able to directly connect over the internet to your home.  There are other methods, but a VPS at a VPS provider will be needed, which is less than $5/month.  If you spin up a light VM and get good at setting up a VPN only when needed, I bet you could get that down to $1/month, since most of the time, you won't need the machine running or any local storage saved.  Spinning up a fresh VM is about 2 minutes of effort, patch it, then install and configure the VPN ... about 3 more minutes .... connect to that VPN from your HOME system to allow remote access and Bob's your Uncle.  You have a public IP that provides a route into your LAN at home.  Anyone using a cellular data connection should expect "carrier NAT".

---

### Post by Shibblet on 2022-11-14
I was able to get the computer setup using KRFB, and then connecting with a VNC Client.  This works great on my home network.

I just need to find a way to access this VNC connection from outside my home network at this point.

---

### Post by TheFu on 2022-11-14
[https://www.howtoforge.com/how-to-set-up-wireguard-vpn-on-ubuntu-22-04/](https://www.howtoforge.com/how-to-set-up-wireguard-vpn-on-ubuntu-22-04/)
or an ssh-tunnel.  The VPN is easier to use, harder to setup, for non-computer devices like tablets and phones.  The setup on a tablet/phone is just a QR-code with all the connection details. It is slick.

As for ssh tunnels for VNC, their must be 10,000 how-to guides for that.  But if you use x2go, then the ssh part is built-in and the compression is 2-3x faster than any RDP or VNC when tuned.  

Of course, both of these require opening a port for either the VPN or SSH connection and you'll need to know the current IP address for your home or setup something with a dynamic DNS provider like no-ip.

There are VPNs that will sponsor an internet server that can make the connections using some NAT trickery that enterprise firewalls block, but most home firewalls don't block (unfortunately).   There's an Ars Technical article about Nebula Mesh VPNs which describes this trick, so you understand the how and the, hopefully, the risks. Google finds it easily. I'm not suggesting that you use Nebula ... just read for the way they trick home routers to allow connections from any IP.  This is also how some corporate web servers gain access that we'd never want to allow to our LANS.  Google does it. Facebook, Twitter, DoubleClick and I'd be surprised if nearly all advertising companies don't do something similar.  This is why we can' trust just the firewall built-into the WAN router, but need a local firewall on all our systems.  The local OS "knows" which requests it made and can block anything that isn't truly a response.  The typical home  router cannot.

---

