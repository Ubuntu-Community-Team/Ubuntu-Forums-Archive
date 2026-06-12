---
title: "Setting up Ubuntu with basic browsing over Ethernet?"
date: 2005-07-28
forum: Desktop Environments
---

### Post by fannypad on 2005-07-28
I'm soon to install Ubuntu onto a machine I'm making for a very cash-strapped friend.

The system will be connected to the net via an Ethernet ADSL modem/router.

Now, having never used any form of Linux before, what would making sure I get connectivity involve in this case? I'd love to assume it would be as easy as plugging in the network cable and letting DHCP do its thing as on WinXP, but if only all things were as clear cut as that.

So, to achieve connectivity via Ethernet, what exactly needs to be done in Ubuntu?


Many thanks in advance for any help :)

---

### Post by Shiven on 2005-07-28
during the install process you'll be asked a couple of things:

Does this server use DHCP?
What is your gateway IP?
what is your dns ip?
what is your host ip?

if you can answer yes to the first one, it will automatically configure itself.... but that doesn't always work. as a backup:

Your gateway ip is your router.
your dns ip is also your router (every router i've worked with handled dns, so this should work)
host ip needs to be like: the same as the router ip +1 (for example: if your router ip is 192.168.1.1 (like mine is) set your host to 192.168.1.x, where x is any number between 2 and 254. try to make sure it doesn't conflict with another computer either, because that will cause problems).


I know i've probably gone over board, but i tried to make everything as clear cut as i could, hope that answers your problems.

- Shiven

---

### Post by fannypad on 2005-07-28
So with a clean installation set to DHCP, everything should be plug and go.

Many thanks for the info, much appreciated :)

---

### Post by joncisco on 2005-07-29
One other thing is that when I installed mine, before I was able to connect to the network I had to enable my network adapter....sorry but I can't remember off the top of my head where to go for it but I do know that I found it pretty easily....

---

### Post by oldlucky on 2005-07-29
Hi can anyone tell me how to disable my dsl conection on startup through ethernet, i would like to enable it manually if i can.

Cheers

---

### Post by Shiven on 2005-08-01
disabling it on startup isn't quite so easy... and i don't know what you mean by 'disable'..

if you remove the gateway address from your network file, then you can't browse the internet, but you aren't physically disconnected...

if you want a physical disconnection, you might want to look into rp-pppoe or somesuch (i have little experiance with this).

---

### Post by Jenda on 2005-08-07
Hello, Ubuntu folks.

My friend has an ADSL Ethernet connection too. Ubuntu did not set it up at startup, though. When I went to Administration>Networking>Ethernet>configure and selected DHCP, it simply did not work. Can anyone help me, please?

---

### Post by Shiven on 2005-08-07
[QUOTE=Jenda]Hello, Ubuntu folks.

My friend has an ADSL Ethernet connection too. Ubuntu did not set it up at startup, though. When I went to Administration>Networking>Ethernet>configure and selected DHCP, it simply did not work. Can anyone help me, please?[/QUOTE]

do it as a static connection then, really easy:

click where it says dhcp, and hit static IP

IP address: should be like this xxx.xxx.xxx.y where x is exactly the same as the router ip (like mine, my router is on 192.168.1.1, my computer is on 192.168.1.2, the next computer is on 192.168.1.3 (etc))

subnet mask should be 255.255.255.0, unless you've got a bit of a different network (highly unlikely)

the gateway address should be your router ip (for my connection its 192.168.1.1)

and you're done.

two advantages to this method- routing/firewalling works really easily, as every ip stays the same, and your network is really easy to fix if something goes wrong, as you go "hrm, 192.168.1.65 is down, i'd better check that computer".

Disadvantages- no ip switching (so if someone malicious gets in and sets up rootkit of some sort, they know where to find what)... then again they can do the same with dhcp + a port scanner....

hopefully this helps

---

### Post by Jenda on 2005-08-08
[QUOTE=Shiven]do it as a static connection then, really easy:

click where it says dhcp, and hit static IP

IP address: should be like this xxx.xxx.xxx.y where x is exactly the same as the router ip (like mine, my router is on 192.168.1.1, my computer is on 192.168.1.2, the next computer is on 192.168.1.3 (etc))

subnet mask should be 255.255.255.0, unless you've got a bit of a different network (highly unlikely)

the gateway address should be your router ip (for my connection its 192.168.1.1)

and you're done.

two advantages to this method- routing/firewalling works really easily, as every ip stays the same, and your network is really easy to fix if something goes wrong, as you go "hrm, 192.168.1.65 is down, i'd better check that computer".

Disadvantages- no ip switching (so if someone malicious gets in and sets up rootkit of some sort, they know where to find what)... then again they can do the same with dhcp + a port scanner....

hopefully this helps[/QUOTE]
 Hmm... Thanks, but:
-It is a dual boot with WinXP. Does that matter?
-The helpdesk told us it's DHCP.
-How do I find out his router IP?
-only one computer using the connection (so far)

Jenda

---

