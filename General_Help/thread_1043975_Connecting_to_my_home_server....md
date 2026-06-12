---
title: "Connecting to my home server..."
date: 2009-01-19
forum: General Help
---

### Post by ooobooontooo on 2009-01-19
Hi,

So I have a server at home, and I had no trouble connecting to it from my laptop because it all within a network. However, now I'm away and I'd like to connect to it via ssh. The only problem is, our Internet provider uses dhcp to shuffle our ip address. So I can't simply just ssh into a certain ip address. I was wondering if there was a way for me to ssh into my box at home from anywhere on the Internet. I tried googling for stuff, but I wasn't really even sure what to look for. I think either VNC (Virtual Network Computing) or VPN (Virtual Private Network) might be the right path, but I wasn't really sure and I didn't want to do anything stupid before asking. My laptop is Hardy 8.04 and my server is Intrepid 8.10. Thanks in advance.

EDIT: Oh yeah, I also something about port-forwarding..is that the right path? Thanks in advance.

---

### Post by iaculallad on 2009-01-19
Try researching/reading on using [dnydns.com]("http://www.dyndns.com/") dynamic hosting services.

---

### Post by ooobooontooo on 2009-01-19
Is there a way to do it without third parties becoming involved? I hate looking at legal stuff. Thanks for the link though, if there are no other alternatives, I'll definitely look into it. Thanks in advance.

---

### Post by iaculallad on 2009-01-19
> **ooobooontooo said:**
> Is there a way to do it without third parties becoming involved? I hate looking at legal stuff. Thanks for the link though, if there are no other alternatives, I'll definitely look into it. Thanks in advance.

I can't think of other solutions rather than using dynamic hosting services to accomplish the task you're trying to resolve. Dnydns offers [free]("http://www.dyndns.com/services/dns/dyndns/") services without entering to it's legal stuffs.

---

### Post by ooobooontooo on 2009-01-19
Thank you very much for introducing me to Dynamic DNS. I think that's exactly what I need. But, I would like to ask one last time, is there really no way to tunnel directly to home network?

---

### Post by blackened on 2009-01-19
You might check into Hamachi. It acts as a VPN over which you can tunnel virtually anything. Just install it to both machines and use the private network address that it automatically sets up.

---

### Post by jimmy the saint on 2009-01-19
I may have missed something when I read about hamachi, but I didn't see anything that would suggest it solves the problem the op has.  It sounds like he would still need to have his current home ip address, which is always different.  If I read it correctly (which I may not have) it would turn his server in to the hamachi server, which means he would need to be able to connect to it, which means he needs his ip.

---

### Post by 3rdalbum on 2009-01-19
That's an interesting problem, but I have an interesting solution.

My workmate has an Ubuntu PC that I remotely administer. Whenever she needs me to Remote Desktop onto her screen, she double-clicks an icon on her desktop that retrieves "www.whatismyip.com" and sends an e-mail to me with her IP address. I use the website because that way I get the computer's external IP address, not the internal IP address.

You could have a script on the computer, say in /etc/rc.local, that retrieves the IP address in this fashion and e-mails it to a webmail account; or if you're handy with PHP and have some external web space you can have your home server send the data to a PHP script running on the external web server.

All this is dependent on whether you've got any programming or scripting skills, because I don't think there's any readymade program out there to do what I'm suggesting. I'd give you my program, except that I wrote it in a few minutes on my workmate's computer as a quick hack, and I didn't keep a backup copy.

Maybe I should properly develop this thing.

Hint: Somewhere in the comments for the "www.whatismyip.com" website is an address for a computer-readable version of the page; if you just grab the computer-readable version you can send the contents of it straight to the webmail address rather than have to parse out the content from the human-readable version.

---

### Post by blackened on 2009-01-19
> **jimmy the saint said:**
> I may have missed something when I read about hamachi, but I didn't see anything that would suggest it solves the problem the op has.  It sounds like he would still need to have his current home ip address, which is always different.  If I read it correctly (which I may not have) it would turn his server in to the hamachi server, which means he would need to be able to connect to it, which means he needs his ip.

Not quite. It works like this:

Computer at home running hamachi connects to secure hamachi server and establishes a VPN (with its own dedicated address, separate from machine's internal and external LAN addresses). Just as an example let's say hamachi assigns it a virtual network address of 2.0.0.1

Computer abroad running hamachi connects to same secure network and can see the virtual network address of computer at home. Just as an example let's say hamachi assigns it a virtual network address of 2.0.0.2

While the clients are both connected to the private network, either machine can tunnel protocols to the virtual network address of the other machine. 

E.g. 2.0.0.2 could ```
vncviewer 2.0.0.1
``` and vice versa

---

### Post by hyper_ch on 2009-01-19
> **ooobooontooo said:**
> I think that's exactly what I need. But, I would like to ask one last time, is there really no way to tunnel directly to home network?
you do directly tunnel into your home network by using dyndns.org or noip.com or or or

---

### Post by ooobooontooo on 2009-01-20
> You could have a script on the computer, say in /etc/rc.local, that retrieves the IP address in this fashion and e-mails it to a webmail account; or if you're handy with PHP and have some external web space you can have your home server send the data to a PHP script running on the external web server.
Yeah that's what I was actually think of doing. The Dynamic DNS servers all require for my server to update my ip address anyway, so I figured I'd use one of those applications (like ddclient) to just update it and send it to me via email...except I'm not too sure how safe email is...I can't think of how else to send it because my laptop is within a network I don't control. And I don't like asking third party websites for space because of all the legal stuff.

@blackend
Wouldn't the Hamachi server still require an IP address to set up the VPN? Also, won't the VPN need to reestablish itself every time the DHCP shuffles the ip address? Thanks though. I'll look into it.

EDIT: I looked at Hamachi and I don't think it's what I'm looking for. It seems all my data has to go through a central server and the source code is open...I don't really feel safe. Sorry, I'm paranoid. Thanks for the suggestion though.

EDIT: I meant the source code is NOT open.

---

### Post by blackened on 2009-01-20
> **ooobooontooo said:**
> EDIT: I looked at Hamachi and I don't think it's what I'm looking for. It seems all my data has to go through a central server and **the source code is open...I don't really feel safe.**

I really hope you meant that the source code is *not* open (which is true), otherwise that statement is both ridiculous and scary.

I understand how you feel about piping data through a centralized third party. Dyndns is probably the best solution. 

I have a a Linksys wrt54g that supports dyndns on the router. If you have the same, then you might poke around in your router settings and see what's there.

---

### Post by ooobooontooo on 2009-01-20
Thank you. I did mean the source code is NOT open. It would be very interesting if I wanted a closed code project for security reasons.

Do you think it would be safe to send my ip address over e-mail?

---

### Post by blackened on 2009-01-20
> **ooobooontooo said:**
> Thank you. I did mean the source code is NOT open. It would be very interesting if I wanted a closed code project for security reasons.

Do you think it would be safe to send my ip address over e-mail?

If you can automate it, then I don't see a problem with doing that way. The biggest thing will be to tightly lock down your ssh server at home. When I first started playing around with ssh my auth.logs were gigantic due to people port-scanning/brute forcing. Give ssh security a good looking into (time between login attempts, max login attempts before ban, etc.).

---

### Post by ooobooontooo on 2009-01-21
Thanks. I think I'll do it that way.

---

