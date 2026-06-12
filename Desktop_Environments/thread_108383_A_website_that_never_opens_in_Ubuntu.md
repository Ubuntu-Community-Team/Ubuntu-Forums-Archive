---
title: "A website that never opens in Ubuntu"
date: 2005-12-25
forum: Desktop Environments
---

### Post by anil_robo on 2005-12-25
Hi all, I just discovered a weird problem using Ubuntu. I can't open [www.123greetings.com](www.123greetings.com) for some reason!

I tried disabling firestarter firewall, disabling modem firewall, using another browser, and even running windows under vmware ubuntu. Nothing worked. But the same site opens well when I boot in real windows. Can someone please try it through their ubuntu box and let me know if they can open it?

Thanks in advance! I just neeed to know "yes" or "no" :)

---

### Post by djheadley on 2005-12-25
I copied and pasted the link into Firefox and it came up ok, well slow but I have dialup.

djheadley

---

### Post by varunus on 2005-12-25
I'm on broadband, and it came up quick for me.

I have no idea what's causing your problem...what system are you running?  Have you customized it any based on howtos here?  What extensions do you have if you're using firefox?  Or what plugins if epiphany?

---

### Post by antidrugue on 2005-12-26
Yep, works for me.

Have you tryed the usual clear cache/cookies?

Not opening in any of your browsers?

I use Firefox 1.5

---

### Post by dcstar on 2005-12-26
[QUOTE=anil_robo]Hi all, I just discovered a weird problem using Ubuntu. I can't open [www.123greetings.com](www.123greetings.com) for some reason!

I tried disabling firestarter firewall, disabling modem firewall, using another browser, and even running windows under vmware ubuntu. Nothing worked. But the same site opens well when I boot in real windows. Can someone please try it through their ubuntu box and let me know if they can open it?

Thanks in advance! I just neeed to know "yes" or "no" :)[/QUOTE]
There is no DNS address for "www.123greetings.com" on my system, there is one for "123greetings.com" but there is no webiste that responds there either.

I tried Fifefox and Epiphany, so it ain't just you.......

---

### Post by anil_robo on 2005-12-26
[quote=dcstar]There is no DNS address for "www.123greetings.com" on my system, there is one for "123greetings.com" but there is no webiste that responds there either.

I tried Fifefox and Epiphany, so it ain't just you.......[/quote]

I use firefox 1.0.7 with Breezy 5.10. And I just cant open [www.123greetings.com](www.123greetings.com) or [http://123greetings.com](http://123greetings.com) with firefox, internet explorer running with vmware-installed XP, or Opera. I can't even ping - it says "UNknown host".

Is something wrong with my system? I setup fresh install of Breezy 2-3 days back! :(

---

### Post by antidrugue on 2005-12-26
Try to ping their name:
```

ping -c 5 www.123greetings.com

```

Or directly their IP address:
```

ping -c 5 72.36.229.58

```

Does this work in your browser: [http://72.36.229.58](http://72.36.229.58)

?

---

### Post by bagel on 2005-12-26
Working fine, only wanted to mention that the adress resolves to 70.86.193.19 here :) 

(Are you in China, possibly? ;) )

---

### Post by anil_robo on 2005-12-26
[quote=bagel]Working fine, only wanted to mention that the adress resolves to 70.86.193.19 here :) 

(Are you in China, possibly? ;) )[/quote] 
Interestingly, both the IP addresses you gave me work, and they go to the same page! :)
I'm in USA (TX).

Why would this website open with IP address, but not with the www name? And what can I do to correct it?

---

### Post by bagel on 2005-12-26
This seems like a DNS problem to me. Since it works under Windows for you, have you possibly forgotten to enter the DNS-Server of your ISP somewhere? Or have you player around with your DNS settings?
It seems strange to me, since that's the only page causing problems?!

---

### Post by anil_robo on 2005-12-26
[quote=bagel]This seems like a DNS problem to me. Since it works under Windows for you, have you possibly forgotten to enter the DNS-Server of your ISP somewhere? Or have you player around with your DNS settings?
It seems strange to me, since that's the only page causing problems?![/quote]

1. I'm on a fresh install of Breezy, and I'm not geek enough to change the DNS settings myself.

2. I see there's only one DNS server listed (192.168.1.254) and only one search domain listed (gateway.2wire.net).

3. The same page was opening correctly in my last install of Breezy, and there too I didn't change any DNS stuff. It was all automatic then, just like this time.

4. Do I need to add something to the DNS settings? If yes, then ***WHAT?***

---

### Post by antidrugue on 2005-12-26
The file /etc/resolv.conf as your DNS lookup configuration. It is possible in your case that you have to enter it manualy. For example, if you have a router at adresse 192.168.0.1, you'll enter that:
```

search
nameserver 192.168.0.1

```

So you enter DNS servers in order of those you want to use. So "search" first,  and then if you don't have a router:
```

search
nameserver 127.0.0.1

```

It is possible that your ISP a DNS server for you, you'll have to ask them those addresses.

---

### Post by Lambert on 2005-12-26
If you're using dhcp then there's nothing to change as dhcp populates the resolv.conf file.

If you are having no problems except with 1 site then the problem is not on your side. It's on the nameserver side. The database doesn't have an entry to resolv 123greetings.com to an ip address or that entry is corrupted. And it's not forwarding to another nameserver to resolv.

This may correct it's self the next time the nameserver syncs with a ROOT-nameserver. You may also want to contact your isp and ask them to check their nameserver and give them the domain (123greetings.com) that's not being resolved. There may be a problem with the server that needs to be corrected.

---

### Post by antidrugue on 2005-12-26
[quote=anil_robo] But the same site opens well when I boot in real windows. 
[/quote]

Given that information, it cannot be a problem on the ISP's side.

---

### Post by d1337 on 2005-12-26
Oddly, I cannot access that site using the www-address either, but can using the ip address from post# 7.  What is your ISP?  I rely on SBC for my DSL connections.  I ask because while I am not in TX, I am in AR which is relatively close.  It's likely that we would use similar nameservers if you are on SBC.  My thought is that the site has some issues.

d1337

---

### Post by heart_reaver on 2005-12-26
All the good one says for DNS, to add to it just check your flash install as per

[http://makuchaku.info/amnesty/](http://makuchaku.info/amnesty/)

---

### Post by anil_robo on 2005-12-26
[quote=d1337]Oddly, I cannot access that site using the www-address either, but can using the ip address from post# 7. What is your ISP? I rely on SBC for my DSL connections. I ask because while I am not in TX, I am in AR which is relatively close. It's likely that we would use similar nameservers if you are on SBC. My thought is that the site has some issues.

d1337[/quote]

I'm on SBC Yahoo DSL too! :confused: Are we beginning to get somewhere? :rolleyes:

---

### Post by Lambert on 2005-12-26
[quote=antidrugue]Given that information, it cannot be a problem on the ISP's side.[/quote] 
Point missed and point taken. 

In post 7 there was a reccomendation to ping using domain name and ip address. I didn't see an answer yet where that was done.

What are the results with that.

If you can ping with both commands and get succesful results then it's not on the isp side.

A couple other tests you can do.

from terminal type this command

```
host www.123greetings.com
```

You know a couple of the ip addresses for 123greetings from this thread so open and edit this file

```
sudo gedit /etc/hosts
```

and add some lines so they look like this.

70.86.193.43 [www.123greetings.com](www.123greetings.com)
67.18.34.242 [www.123greetings.com](www.123greetings.com)

the /etc/hosts file is a local file that can be read for name resolv. If a nameserver can't resolve a name it then reads this file to check.

---

### Post by cs378 on 2005-12-26
wow

thats weird, i never knew websites don't work like that

the 123greetings.com does not work for me, but the ip address did

no wonder some ppl say they cant access my website lol

---

### Post by dcstar on 2005-12-26
[QUOTE=antidrugue]Given that information, it cannot be a problem on the ISP's side.[/QUOTE]
No necessarily, if the resolved DNS was previously cached in Windows, but had changed since that time when a new Linux lookup was tried, then you will get exactly this outcome.

DNS is a essentially distributed database where changes can take quite a while to replicate through the chain of DNS servers that may supply the information a particular lookup utilises. To make it use network resources efficiently (and be more resilient to various problems), lookups use cached data from servers rather than going to the source of a DNS entry all of the time.

You can do a DNS lookup for a site right now, and then in a minute that site could be totally removed, but you may not see that change until the Expire time on the original entry ticks over and all the DNS servers try and refresh the data with the "Canonical" information. That can take days sometimes.

---

### Post by antidrugue on 2005-12-26
[LEFT][LEFT][FONT=Arial][SIZE=3]Well, in that case, just go in windows, clear DNS cache, and try again the site, we'll be fixed. So in command prompt, windows:

```
[FONT=monospace][/FONT]
ipconfig -flushdns

```

Then try again the site.
[/SIZE][/FONT] [/LEFT]
  [/LEFT]

---

### Post by anil_robo on 2005-12-27
> **Lambert]In post 7 there was a reccomendation to ping using domain name and ip address. I didn't see an answer yet where that was done. What are the results with that.[/quote] I'm able to visit the site by its ip address in firefox, but the domain name fails 100% of the times.

> If you can ping with both commands and get succesful results then it's not on the isp side. I'm able to ping the ip address but "unkown host" when I ping the domain name [www.123greetings.com]("http://www.123greetings.com")

> from terminal type this command

```
host www.123greetings.com
```  
Here's what I got:
```
akumar@rakshak:~$ host www.123greetings.com
 said:**
> You know a couple of the ip addresses for 123greetings from this thread so open and edit this file

```
sudo gedit /etc/hosts
``` 
and add some lines so they look like this.

70.86.193.43 [www.123greetings.com]("http://www.123greetings.com")
67.18.34.242 [www.123greetings.com]("http://www.123greetings.com")
 
That's fine, but there could be several other websites I may not be able to open in Ubuntu, so how do I know if firefox spits an error message - does that site exist, or is it just that Ubuntu isn't able to resolve the domain name?

---

### Post by dcstar on 2005-12-27
[QUOTE=anil_robo]I'm able to visit the site by its ip address in firefox, but the domain name fails 100% of the times.
......
That's fine, but there could be several other websites I may not be able to open in Ubuntu, so how do I know if firefox spits an error message - does that site exist, or is it just that Ubuntu isn't able to resolve the domain name?[/QUOTE]
It's nothing to do with Ubuntu, it's one site with a bad DNS entry.

---

### Post by anil_robo on 2005-12-29
How do I correct that bad DNS entry? The DNS server listed is **gateway.2wire.net** which I know is the default gateway for my router. When I reboot the same machine in windoze XP, 123greetings.com opens perfectly! But when I open it in Ubuntu, it never opens! (Connection refused)

---

### Post by anil_robo on 2005-12-31
Manual solution:

I corrected the website DNS entry by adding this to my hosts file:

 70.86.193.43 [www.123greetings.com]("http://www.123greetings.com/")
 67.18.34.242 [www.123greetings.com]("http://www.123greetings.com/")

Done!

Thanks everyone for help! I appreciate it very much! Have a great year! :)

---

