---
title: "SSH appears to need Desktop login"
date: 2021-08-31
forum: Desktop Environments
---

### Post by Geoff_Lane on 2021-08-31
Folks,

I am based in UK and have a friend in California.  Few years back I sent up a spare laptop as an SSH server and dlna server, I look after this setup via ssh login and VNC if required.

Strangely, if her computer needs to reboot I cannot login to ssh unless she logs in to her desktop.  On all my RaspberryPi devices, even if they have a desktop I don't need to be logged in, is this a setting I have mistakenly set?

Actually, I am wondering if it is a WiFi issue, maybe WiFi doesn't connect until desktop enabled.

Geoff

---

### Post by TheFu on 2021-08-31
ssh doesn't require any users logged in locally.  I seldom, login on more than 2 computers - a desktop and a laptop.  The other 20 are all over ssh only.
If the system is booted and sshd is running, a remote connection should be possible barring firewalls or whole drive encrypted storage that is waiting to be opened. Of course, the sshd system needs to have a static IP and the router needs to forward a port to that static IP correctly.

For wifi issues, that could be it. There are 2 ways to setup wifi. Either always on via a service or using a GUI. If you used the GUI, then it probably won't work until the userid controlling the wifi connection has enabled it.  The non-GUI method would be through netplan on 20.04 and later systems.  Someone else will need to help if that's the case.  I don't use wifi much.

---

### Post by ActionParsnip on 2021-09-01
Is the server side set to a static IP?

---

### Post by Geoff_Lane on 2021-09-02
> **ActionParsnip said:**
> Is the server side set to a static IP?

It is but from memory I think that may be via a fixed DHCP address via the router rather than fixed in the Ubuntu system.

I know in the past I have set fixed IPs in /etc/network/interfaces   then I think the system evolved to prefer /etc/dhcpcd.conf

Reluctant to fiddle too much as at least at the moment I can access it most of the time.

Geoff

---

### Post by Geoff_Lane on 2021-09-02
> **TheFu said:**
> 

For wifi issues, that could be it. There are 2 ways to setup wifi. Either always on via a service or using a GUI. If you used the GUI, then it probably won't work until the userid controlling the wifi connection has enabled it.  The non-GUI method would be through netplan on 20.04 and later systems.  Someone else will need to help if that's the case.  I don't use wifi much.

Heard of netplan but not looked in to it much.  Tended to fix IPs in the past using /etc/network/interfaces or /etc/dhcpcd.conf

Geoff

---

### Post by TheFu on 2021-09-02
I've never used /etc/dhcpcd.conf.
Sorry.
Good luck to you.

---

### Post by TheFu on 2021-09-02
Just saw this cautionary tail about using DHCP: [https://www.anvilsecure.com/blog/dhcp-games-with-smart-router-devices.html](https://www.anvilsecure.com/blog/dhcp-games-with-smart-router-devices.html)

---

### Post by Geoff_Lane on 2021-09-06
I do tend to use an alternative port for the internet traffic then convert via the router plus use an ssl file for login.

Geoff

---

### Post by rsteinmetz70112 on 2021-09-06
I have Ubuntu computers I log into regularly via ssh and none of them require a user to be logged in. Most of them are wired connections but I do have a couple of wifi connections and they don't require a user to be logged in to access them.
I have used DHCP a lot in the past, back when it took real work to get it to work. I've never had it cause this kind of problem, usually it just fails to work. These days I configure Ubuntu for static IPs and mostly let the ISPs router handle it for windows clients.
/etc/dhcpcd.conf is a file on the DHCP server. If the Ubuntu computer acting as a DHCP server? If the router is the DHCP server, as I recall that file doesn't do anything much on the DHCP client.
/etc/network/interfaces is the old way of configuring the network on Ubuntu, the new way is netplan, I still haven't quire figured it out.

I think to help we'll need more information about you remote setup, includi9ng the Internet connection..

---

### Post by Geoff_Lane on 2021-09-07
> **rsteinmetz70112 said:**
> I have Ubuntu computers I log into regularly via ssh and none of them require a user to be logged in. 


I think to help we'll need more information about you remote setup, includi9ng the Internet connection..

None of my Raspberry Pi devices require any kind of desktop login to access via SSH

As for the remote Ubuntu I am reluctant to fiddle too much it may be very difficult to remedy if I lose connection.  I already added some settings to the /etc/network/interfaces file and now cannot connect at all.  Hopefully I can talk the remote owner through deleting what I added in that file.

Last time I looked I connected ssh -D (proxy) and viewed the remote router, noticed the IP was a persistent DHCP address allocated by the router.  Normally I fix IP of server devices via the computer's file system, cannot recall why we ended up with router giving the fixed IP, plus of course there is port redirection as connection made on a non standard port.

I may just accept the required login and set that to be auto

Geoff

---

### Post by TheFu on 2021-09-07
/etc/network/interfaces was deprecated a few years ago.  Netplan with YAML is the current method.

As for running on non-standard ports, I let the router to port-translation for me, so inside my networks, ssh is on port 22/tcp.  But from the outside world, they have to hit something like port 59022/tcp or 60022/tcp to hit two different internal machines.  The router port forward does the translation.  This way, the defaults for fail2ban are good just from installing it.

With a raspberry pi, I could see where letting the router provide DHCP would be good, assuming you can securely remotely administer the router.

I supported my Mom from 7 hrs away for years over an ssh connection - with an NX remote desktop if necessary.  I would only do major changes the day before we'd travel for a visit.

---

### Post by Geoff_Lane on 2021-09-12
I cannot recall why the router is set to allocate the address, the only time I have ever done that that I recall is on my own network with some Alexa IoT devices otherwise I'd always do it on the device.

All my R-Pi devices (five permanent on network) are all allocated addresses via the device, not router.  Must admit all this /etc/network/interfaces - dhcpcd.conf - netplan - Network-Manager, Networking.service confuses the hell out of me.  I generally achieve my objective but often with a few errors ironed out along the way.  The joys on Linux.

Geoff

---

### Post by TheFu on 2021-09-12
> **Geoff_Lane said:**
> I cannot recall why the router is set to allocate the address, the only time I have ever done that that I recall is on my own network with some Alexa IoT devices otherwise I'd always do it on the device.

All my R-Pi devices (five permanent on network) are all allocated addresses via the device, not router.  Must admit all this /etc/network/interfaces - dhcpcd.conf - netplan - Network-Manager, Networking.service confuses the hell out of me.  I generally achieve my objective but often with a few errors ironed out along the way.  The joys on Linux.

Things change over time.  That is a constant with Linux.
*interfaces* has been around since the early 1990s.  It had been updated to become more capable over time - and to break things.  *resolv.conf* was around in 1993 for where to setup DNS.  Around 2011, someone decided that editing *resolv.conf* was too hard, so they created *resolvconf* ... a tool that could read parts of *interfaces* for dns-* entires, then modify the *resolv.conf*.  It got confused for non-trivial setups and often broke.  I started purging *resolvconf* then and went back to manually controlling the *resolv.conf* as Dog intended.  I still do that.

Network-Manager was created to make network controls more "Windows-like" - which I suppose is good for typical end-users.  It never worked well for my needs, so within the first 10 minutes of any new install, I purge it and all related tools. On desktops or servers, that's fine - I can setup *interfaces* as needed.  

New installs of 18.04 used netplan YAML files, but upgraded 18.04 systems retain the interfaces.  Netplan couldn't handle the non-trivial network setups that I needed until the fall of 2019 - so ~18 months after it was put into an LTS release and forced onto the world.  When it finally started working, I was so happy ... until I found some other tiny detail it couldn't handle (Or I couldn't figure out).  That's where I was until around the fall of 2020. I think netplan can do all that I need today, but have avoided any complex setups.

Around 18.04 (I'm not sure exactly when), systemd-resolved was introduced to replace the always broke resolvconf.  It wasn't any better.  Now I purge both *systemd-resolved* and *resolvconf*, and take over manual control of the *resolv.conf* as Dog intended.

So ... for things that don't move, all of this is a do-once-and-forget solution.
Laptops are different.  They move around and to be useful outside our home networks, they need to support DHCP.  Perhaps network-manager has improved, but I'm so used to wiping it from the systems, another solution was needed.  In the Ubuntu world, network manager has been used so long now that people forget there are 5 other similar tools.  conman and wicd are probably the most popular.  Conman is what many raspberry-pi systems use.  I'm not exactly thrilled with it.  **wicd-curses** is a TUI version of wicd and doesn't do much automatically, but it can be setup to use either wifi or wired and completely understands when to prefer one over the other - never allowing both concurrently.  I've been using wicd-curses since around 2011 on my laptops.  The setup isn't hard and it "just works" after that.

Anyway, that's what I think that I know.

*dhcpcd.conf* - I have no idea why you'd care or even know about that, unless you run a DHCP server on Ubuntu. 99.9% of people here will let their router be the DHCP server, so there's no need to touch dhcpcd.conf.  I don't have that file on my systems.  There is a dhclient program that gets leases from the DHCP server on the network, but that is unrelated. Best to just forget about dhcpcd.conf.

---

### Post by Geoff_Lane on 2021-09-14
Interesting, so many options to achieve the same end result.

Oddly, although my main computer is a laptop running 20:04 it is the R-Pi devices that I tend to fiddle with network wise.  Very similar to Ubuntu (Debian) but don't think they use Network Manager, let alone netplan.

Geoff

---

### Post by TheFu on 2021-09-14
Different distributions have different network configuration methods.  Even if they seem to do it using the same tools, there are usually slight differences.
The raspbian-based distros I've used all used **conman**.  I've never seen that on any Ubuntu.

---

