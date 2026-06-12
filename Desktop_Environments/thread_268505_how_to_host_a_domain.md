---
title: "how to host a domain"
date: 2006-09-30
forum: Desktop Environments
---

### Post by mitjab on 2006-09-30
i use this howto to install dns server
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4?](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4?)

now i want to host a domain in my server. How can i host it? I have my mitjab.com domain for few years but now i would like to host it in my server. I must know my dns to host it i think?
thx

---

### Post by djRobbieF on 2006-09-30
I'm not 100% sure what you're asking.  I take it you mean you're trying to set up a web server?  So have you installed apache ([httpd.apache.org/](httpd.apache.org/)) and stuff?  That'd obviously be the first step.  But you don't require a DNS server to host a web site.  I mean; you don't need YOUR OWN DNS server...  you'd just have to set up the domain in apache's httpd.conf.

---

### Post by mitjab on 2006-09-30
i know i already have this, but i would like to have my own dns server. maybe i write strange. I want to have my own dns server and that my domain will be at my dns server.

---

### Post by djRobbieF on 2006-09-30
Not to pass it off, but you should probably read the manual for whatever DNS software you are using.  Either that, or post specific questions related to your problem.

---

### Post by PriceChild on 2006-09-30
I use no-ip.com to point pricechild.no-ip.info to me occasionally when i need it.

You can pay for proper domains such as mitjab.com  to be directed to you also.

Pricey

---

### Post by djRobbieF on 2006-09-30
> **PriceChild said:**
> I use no-ip.com to point pricechild.no-ip.info to me occasionally when i need it.

You can pay for proper domains such as mitjab.com  to be directed to you also.

Pricey

That's only necessary if you're hosting it on a dynamic IP - which you wouldn't be able to do (properly) if you were trying to host a DNS server (DNS updates take up to 72 hours to propagate - so your server would often go offline for 72 hours).

So my guess is they're not looking for dynamic forwarding... unless I'm wrong, in which case your hosting your own DNS is a moot idea, unless you upgrade your line to static IP.

But my assumption would be that the user already has static IP, otherwise they wouldn't be able to set up a proper DNS server.

---

### Post by mitjab on 2006-09-30
yes i have static ip and i already register mitjab.com domain few years ago. I also use router.

i found this howto
[http://www.ubuntuforums.org/showthread.php?t=236093](http://www.ubuntuforums.org/showthread.php?t=236093)

must i use already registered domain like mitjab.com or i can just think out a new not registered domain?

I am using router
www              IN      A       192.168.0.2
mta              IN      A       192.168.0.3
ns1              IN      A       192.168.0.1

can i use for all 3 the same 192.168.1.5 (the same machine) and which port i must foward for ns1 and mta. www use 80 which port this 2 needs.

thx

---

### Post by mitjab on 2006-09-30
anyone?

---

### Post by pod25 on 2006-09-30
> **mitjab said:**
> anyone?

Do you mean you want to change your nameserver to point to you ?

---

### Post by mitjab on 2006-09-30
i want that other friends use my dns to host in my server. Becouse of this i need to enable dns server but do not know the answers for my previous question. hope you undesrtand.

---

### Post by pod25 on 2006-09-30
> **mitjab said:**
> i want that other friends use my dns to host in my server. Becouse of this i need to enable dns server but do not know the answers for my previous question. hope you undesrtand.

OK , we will do this bit by bit, step by step.

Do you want to host other peoples web-sites ?

---

### Post by mitjab on 2006-09-30
yes few of my friends and if you want i can host you too.

---

### Post by pod25 on 2006-09-30
> **mitjab said:**
> yes few of my friends and if you want i can host you too.
No I do not require hosting.
But to answer you initial question you need to install ispconfig.
Once installed this will take care of all your hosting needs.

---

### Post by mitjab on 2006-09-30
i do not want to install ispconfig, i am using webmin. I want to fix this without to install ispconfig.

i just do not know this
```

must domain be registered or not?
Can i use no-ip.com domain?

I am using router so which port must o foward for bind server?

www IN A 192.168.1.5
mta IN A 192.168.1.5
ns1 IN A 192.168.1.5

can i use for all three the same ip and the same machine?

```

---

### Post by pod25 on 2006-09-30
> **mitjab said:**
> i do not want to install ispconfig, i am using webmin. I want to fix this without to install ispconfig.
???  Well I use both. Webmin to administer my comp and ispconfig to administer my web server.
Is there a reason why you do not want ispconfig installed ?

---

### Post by ropers on 2006-09-30
mitjab: Please don't get me wrong -- I am not trying to flame you. However, I would like to make you aware that I personally found several of your sentences pretty unclear and extremely hard to parse. Like this one for example: [quote=mitjab]can i use for all 3 the same 192.168.1.5 (the same machine) and which port i must foward for ns1 and mta. www use 80 which port this 2 needs.[/quote]
You could try composing your questions in a text editor beforehand, then save them and go back to them later and re-read them. Being a stanger without prior knowledge of what you're trying to say, would you understand them? Are they reasonably close to being grammatically correct? I'm not trying to be a grammar Nazi, but punctuation, capitalization, and putting seperate thoughts into seperate sentences can be a Good Thing. The clearer and more legible your questions, the more likely it is that you will elicit helpful responses. Again, no offense intended.

---

### Post by mitjab on 2006-09-30
ropers no problem, i know that my english isn't perfect and i will try to write better now.

pod25 i install ispconfig but i do not like it. I do not like any control panel like ispconfig becouse it is not translated and it has many functions that i do not need.

I want to make my dns now but i do not know some things

```

must domain be registered or not?
Can i use no-ip.com domain?

I am using router so which port i must foward for bind server that it will be reachable? Apache use port 80.

can i use the same ip for all three services like this

www IN A 192.168.1.5
mta IN A 192.168.1.5
ns1 IN A 192.168.1.5


```

Hope that all of you understand me now.

thx

---

### Post by ropers on 2006-09-30
> **mitjab]must domain be registered or not?[/quote]

I'm not at all sure I understand. (Please be more verbose and give examples of what you actually mean. Help us to help you.) Any use of DNS requires that the domain you use be registered, unless you use a domain on a private network and/or intranet and that domain is not intended to resolve on the Internet. There are any number of registrars but very few offer free domains, and the ones that do mostly don't offer free second level domains but rather free subdomains. So yes, you gotta register and no, it's mostly not free. Whether you can use an existing domain depends on whether your current service provider allows you sufficient control over that domain to point it to another nameserver by IP (you'd put the IP of your new nameserver in there). If they don't allow that then you might consider switching to another registrar.

[quote=mitjab]Can i use no-ip.com domain?[/quote]
I'm not familiar with no-ip.com but I gather they are a dyndns workalike. I believe a previous poster has pointed out that combining a dynamic IP service with running an own DNS server might be a bad idea. However, if you only use your DNS server to resolve further subdomains to a second level domain name that's constantly hosted at the same fixed IP, then combining a dyndns service with running an own DNS server might work: While it does take a long time for DNS updates to propagate all across the Internet, in this case a surfer needn't wait for that to visit you: Other servers all across the Internet would already know that blahblah.tld is your domain and that your DNS server is authoritative for that zone. A prospective visitor of foo.blahblah.tld would be referred to you DNS server which would resolve foo and a visitor to bar.blahblah.tld would equally be referred to your own DNS server and so on.

EDIT: This would however sort of defeat the purpose of using a dyndns service said:**
> I am using router so which port i must foward for bind server that it will be reachable? Apache use port 80.
DNS uses TCP port 53 and UDP port 53; cf. [http://www.google.ie/search?hl=en&q=well-known+ports](http://www.google.ie/search?hl=en&q=well-known+ports)

[quote=mitjab]can i use the same ip for all three services like this

www IN A 192.168.1.5
mta IN A 192.168.1.5
ns1 IN A 192.168.1.5[/quote]

Yes. 

And to shove in a bit of a plug here, if you're running an Internet exposed server, have you looked at putting an OpenBSD-based firewall in between there? --> [www.openbsd.org](www.openbsd.org) 
You really can do wonders with the pf packet filter and its/OpenBSD's NATting, routing and bridging capabilities, and yes, of course it can run DNS and DHCP. (Sorry for this, I know this is the Ubuntu board, I just can help myself. ;-P)

---

### Post by pod25 on 2006-09-30
> **mitjab said:**
> 
Hope that all of you understand me now.
thx
Well to be honest not really.
From what I can gather, you want to be able to use your current domain to point to your comp ? that part should be easy, you should have a control panel at where you bought your domain from, there you can change all that needs changing.
But as for hosting web-sites for other people, well you are making life difficult for yourself unless you install a pre-configured web controller.

And as for those IP's you listed several times, well they are LAN IP's and not WAN IP's.
You need to research how to setup your BIND9 server and DNS server

---

### Post by ropers on 2006-10-03
> **pod25 said:**
> And as for those IP's you listed several times, well they are LAN IP's and not WAN IP's.
You need to research how to setup your BIND9 server and DNS server

Yea, those are [private IP ranges]("http://en.wikipedia.org/wiki/Private_network") which should obviously only ever be bound to your internal NIC. 

I don't know about Linux, but in OpenBSD you would use PF's NAT/RDR: [http://www.openbsd.org/faq/pf/rdr.html](http://www.openbsd.org/faq/pf/rdr.html) 
I suspect that there's also a way to do this with Linux, I just don't know it (yet?).

---

