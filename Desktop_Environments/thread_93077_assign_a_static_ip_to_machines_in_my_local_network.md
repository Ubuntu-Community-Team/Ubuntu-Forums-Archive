---
title: "assign a static ip to machines in my local network"
date: 2005-11-21
forum: Desktop Environments
---

### Post by megamania on 2005-11-21
Sorry for this basic question - I've been searching for a solution (google and this forum), but I got hundreds of results and don't know which one fits my needs.

I have three computers (two with Ubuntu and a Mac Os X) connected to a router.
They get an IP address on a first-come, first-served basis (i.e. the first computer I turn on becomes 192.168.1.100, the second one .101 and so on).

I would like to have a fixed address for each computer, especially for my linux box hosting aMule.  :-)

Can you tell me what I should do or point me to a FAQ or HowTo? Even just telling me what I should search for (i.e. appropriate terminology) would help...

---

### Post by adwait on 2005-11-21
Umm.......why not just set the router not to function as a DHCP server in its control panel (probably accessed by pointing the browser to 192.168.1.1 or some address like this). Then set the static IPs for each machine. On Ubuntu this can be done at System>Administration>Networking. (or something to that effect.......sorry, I am not using Gnome)

---

### Post by drummer on 2005-11-21
Have a look through your router settings, my router can give the same IP to the same machine when it connects with DHCP (Netgear WGR614). Your probably should, but if not, you can turn off the DHCP server on the router and give each computer it's IP manually. In Gnome it's System > Administration > Networking. You can fill in the subnet with 255.255.255.0, just make it the same on each computer.

---

### Post by megamania on 2005-11-21
hmm. I have a Linksys wag54g wireless router. I know how to change its settings, but I'm very afraid of making a mess when I touch things I don't know.

When I'm back home, I'll try to assign a fixed ip address to each machine as you suggested me (gnome settings), then I'll try to set up the router accordingly.

I'll be back to let you know that I messed up!  :-)

Thanks,
gianfranco

---

### Post by megamania on 2005-11-21
One more thing that I thought about when re-reading your suggestions: I would like to have static ip's assigned to my machines, while still having dinamic ip's assigned to machines that are connected occasionally (i.e. when a friend comes with his/her own computer).

If I understand correctly, I should assign a static ip to my machines, "tell" my router that those IP's are reserved _and_ leave DHCP on for the other computers to be automatically configured, right?

---

### Post by fourchannel on 2005-11-21
correct.

the most reliable way is to find each machine's MAC address and tell the router to assign 

IP [www.xxx.yyy.zzz]("http://www.xxx.yyy.zzz") to MAC address 01:23:45:67:89

and so on, while leaving DHCP on to deal with entry/exit to the network.

---

### Post by drummer on 2005-11-21
Also first try just setting static IPs without disabling DHCP, now I'm not sure if having DHCP matters or not to static IPs.

---

### Post by megamania on 2005-11-21
thank you all for the comprehensive and quick help. It all looks much easier to accomplish now.

I'll try to set things up as soon as I'm back and will report!

---

### Post by drummer on 2005-11-21
@fourchannel, i agree.. probably the best way to do it if you can find the setting, should be there somewhere. The router shouldn't get messed up, just change back what you change, and remember the previous values.

---

### Post by tommythecat on 2005-11-21
What I do on my home network:
I have my router setup to use dhcp but to begin assigning addresses starting at x.x.x.100

Then I statically assign IP's to the systems that I would like to keep consistent IP's on (webserver, gaming server) starting at x.x.x.2 (1 is the router).

There is no need to disable dhcp on the router, clients with a statically assigned address will make no attempt to query dhcp for an addy.

That way you can still use dhcp on your network for any systems that do not require a static IP.

So if guests come to your house with laptops they will get an IP without any issues.

---

### Post by megamania on 2005-11-21
tommythecat,

that's exactly what I had figured out thanks to the suggestions above, BUT...

I have a Linksys wag54g version 2 router, and a strange thing happens: on the manual that I downloaded from the internet it says that on the basic setup settings, next to the "Enable / Disable DHCP" there's an "Advanced Settings" button which allows me to specify what IP address has to be reserved for what MAC address.

The problem is that I don't have that button! I don't know if it's an issue with Firefox, or if the manual refers to a previous version (I have the latest release with upgraded firmware).

I'm going to send an email to the customer support to find out what's going on, unless somebody here has a clue...

---

### Post by dcstar on 2005-11-21
[QUOTE=drummer]Also first try just setting static IPs without disabling DHCP, now I'm not sure if having DHCP matters or not to static IPs.[/QUOTE]
Some DHCP servers "test" if the IP address is already in use before they try and allocate it - otherwise the only issue is a DHCP server double-allocating an address already in use.

If your DHCP server is set up to allocate 30 IP addresses, just put any static addresses outside of that particular range - the DHCP server will not care!

If your DHCP server allocates addresses in a whole subnet, (and you don't want to muck around with its settings), just allocate any static addresses at the top end of the range - it is highly unlikely you will plug in enough devices to force your DHCP server to need to get up to that area.

---

### Post by thumbsoup on 2005-11-21
Just wanted to say that I have a Linksys wireless router, and set a static IP due to aMule and related programs.  I have 2 computers on the router, one Ubuntu and one Windows.  My Ubuntu computer has aMule.  I left the router set to DHCP, and set my Ubuntu to a static IP using Network Tools.  The Windows computer I left as DHCP.  So far no problems, doesn't matter which computer I boot first, it just seems to work.  And I can actually get a decent download speed in aMule now.

This is what I did:
Applications -> System Tools -> Network Tools
- change "Network device" to my connection, "Ethernet interface" for me.
- then click "Configure" button, which asks for password
- typed in the static IP.
- default subnet mask fills in automatically
- put in my router IP address as Gateway
- remembered to forward ports thru the firewall

I know little about networking, so it wasn't until I found a post on this forum that I learned to set my Ubuntu computer's Gateway IP address to the address of my router.  Doh.

---

