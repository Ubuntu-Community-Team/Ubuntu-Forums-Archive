---
title: "ssh question"
date: 2005-12-22
forum: General Help
---

### Post by rockit on 2005-12-22
Can an ssh server act as a complete proxy (bouncing all the traffic from a client out to the net) without having anything else like squid installed? I'm looking to tunnel all of my traffic over a (public) wireless lan (using port forwarding with an ssh client) and I just want to bounce that traffic from the ssh server to the internet.  Is this possible with just ssh? 

I've never used ssh before, so I wasn't sure if this is possible or not. 

Thanks ahead of time

---

### Post by amohanty on 2005-12-22
I think if all you want is to tunnel traffic.. umm how about stunnel. Designed specifically for this purpose:

[http://www.stunnel.org/](http://www.stunnel.org/)

HTH
AM

---

### Post by rockit on 2005-12-22
[QUOTE=amohanty]I think if all you want is to tunnel traffic.. umm how about stunnel. Designed specifically for this purpose:

[http://www.stunnel.org/](http://www.stunnel.org/)

HTH
AM[/QUOTE]

Hmmm...wasn't aware of that. Thanks for the suggestion.

Is it still possible to do this with ssh? 

SSH was just the first thing that came to mind. If anyone has suggestions on other ways to accomplish this, I'd appreciate them. I'm just trying to explore all the possibilities at this point.

---

### Post by amohanty on 2005-12-22
The _right_ way to do what you want is stunnel, since (as I mentioned) it was designed to secure pretty much any kind of TCP connection. I think you can do it using ssh but the only implementation I have seen used some pretty fancy footwork to accomplish it. Unfortunately I dont have the kind of knowledge to be able to advise you about that.

HTH

---

### Post by rockit on 2005-12-22
[QUOTE=amohanty]I think you can do it using ssh but the only implementation I have seen used some pretty fancy footwork to accomplish it. Unfortunately I dont have the kind of knowledge to be able to advise you about that.

HTH[/QUOTE]

So is stunnel pretty easy to setup?

---

### Post by amohanty on 2005-12-22
> So is stunnel pretty easy to setup?

The only right answer I can give is... it depends :)
I suggest you go throught the docs and try some things. If you hit a wall at some point of time, I would be more than glad to help.

AM

---

### Post by rockit on 2005-12-22
[QUOTE=amohanty]The only right answer I can give is... it depends :)
I suggest you go throught the docs and try some things. If you hit a wall at some point of time, I would be more than glad to help.

AM[/QUOTE]

My only question with stunnel, then, is: is it realistic to forward ALL traffic from a client to the server using it? I really just want *all* ports forwarded. The reason I ask is because it looks as if each program has to be ssl capable for it to work with stunnel? I'm probably wrong...

---

### Post by amohanty on 2005-12-22
Do you have specific destination on the internet in mind?

Essentially (I am assuming) you want all traffic between your client (eg laptop) and server (eg home server) to be secured via ssl even if you communicate over a public wireless LAN. Is that correct?

If so I am not sure I understand what you mean by forward all traffic from a client to the server. If you are communicating via stunnel soem good examples are here:
[http://www.stunnel.org/examples/](http://www.stunnel.org/examples/)

Basically you would have an SSL enabled server daemon on your home server and would communicate it from your client.

> The reason I ask is because it looks as if each program has to be ssl capable for it to work with stunnel?

No each program does not have to be ssl capable. Take a look at the examples link above and the FAQ.

HTH
AM

---

### Post by SickTwist on 2005-12-22
If *all* the ports are being forwarded, then wouldn't the computer just work as a repeater? What would be the reason to even have the computer doing this? The only thing I can think of is using it to examine network traffic.

If you wish to filter traffic, that is different entirely. You should probably look into iptables.

---

### Post by rockit on 2005-12-22
[QUOTE=amohanty]Do you have specific destination on the internet in mind?
[/QUOTE] Not really, I just want all of my traffic (smtp, pop, http, https, dns, various messenger clients etc..) to be tunneled to the server. 
> 
Essentially (I am assuming) you want all traffic between your client (eg laptop) and server (eg home server) to be secured via ssl even if you communicate over a public wireless LAN. Is that correct?
That is exactly correct. The wireless lan in question doesn't use WEP etc... 
> 

If so I am not sure I understand what you mean by forward all traffic from a client to the server. If you are communicating via stunnel soem good examples are here:
[http://www.stunnel.org/examples/](http://www.stunnel.org/examples/)

Basically you would have an SSL enabled server daemon on your home server and would communicate it from your client.
This is where I'm somewhat confused...does the stunnel daemon have to be configured for *every* service I want to use? 


> 
No each program does not have to be ssl capable. Take a look at the examples link above and the FAQ.

HTH
AM
OK, that was part of my confusion. 

Thanks for all your help.

---

### Post by rockit on 2005-12-22
[QUOTE=SickTwist]If *all* the ports are being forwarded, then wouldn't the computer just work as a repeater? What would be the reason to even have the computer doing this? The only thing I can think of is using it to examine network traffic.[/QUOTE] The reason is because I want to tunnel all of my unencrypted traffic (which is about 99.9% of all my traffic) over an unencrypted public wireless lan back to my "server" at home which would then just bounce/proxy/forward all of that traffic out to the net. Yes, basically it would be acting as a repeater. The difference is between an unencrypted (insecure) link (wireless network) and an encrypted link on a "secure" network.

---

### Post by amohanty on 2005-12-22
> does the stunnel daemon have to be configured for *every* service I want to use? 

Well in a way yes, you would have to _start_ every daemon that uses the network (eg mail server, proxy, etc)  via stunnel. There is no configuration required as such.

If all you want to do via the proxy is to surf the web, read mail and chat, why not use VNC or something like that. Again the examples show how to do that too. Basically you would remote into the box and use the server itself.

HTH
AM

---

### Post by rockit on 2005-12-23
[QUOTE=amohanty]Well in a way yes, you would have to _start_ every daemon that uses the network (eg mail server, proxy, etc)  via stunnel. There is no configuration required as such.

If all you want to do via the proxy is to surf the web, read mail and chat, why not use VNC or something like that. Again the examples show how to do that too. Basically you would remote into the box and use the server itself.

HTH
AM[/QUOTE]

VNC was my original plan until I realized that I didn't have any modern hardware to spare that would run a modern GUI well. The "server" would be in the form of a pentium 166 w/ 64 megs of ram (not much of a server, lol). Someone in another forum suggested using ubuntu/kubuntu with the -server parameter so it didn't install X (I was thinking debian before that suggestion). That's why ssh was my first thought...most (or at least many) distros have it ready to go out of the box. I was just trying to utilize low resources more than anything.

---

