---
title: "TorBlast?"
date: 2009-04-17
forum: General Help
---

### Post by andysuth on 2009-04-17
I'm journeying to a closed regime country in a years time (we won't mention the one), but all internet access is strictly monitored and foreign news websites and blocked.

Even "The Guardian", 

I can't read my favourite informative website "The Daily Sport" there.

I believe I can use TOR - "The Onion Router" and "Privoxy" to get onto the websites, as I've read it somewhere.

I've also seen a discussion of how to download entire websites and their sub-pages using WGET, on this forum archive:
[http://ubuntuforums.org/showthread.php?t=153766](http://ubuntuforums.org/showthread.php?t=153766)

Tor and Privoxy work fine (I use them at work quite often). But I'm not sure if Wget will work with TOR and Privoxy whilst in said country.

Has anyone any experience with this?

Will BBC allow me to download their entire website to read at a later date on my laptop?

(Internet access is free and wifi available at Starbucks and similar: I'll be using Linux Mint on an old laptop: already out there, so preferably something I can install and run).

-Andy.

---

### Post by andysuth on 2009-04-17
I've got the WGET command I want:

wget -r -l 3 [http://news.bbc.co.uk/text_only.stm](http://news.bbc.co.uk/text_only.stm)

however, this does not alter the paths of the "href" in the html, so I need to file edit that, not so bad because I can do it offline.

However because it has a link to the full site at the top of the page it also downloads the full site!

I need to know if this works through privoxy and TOR too, and don't know how to do that.

Any tips?

-Andy.

---

### Post by codeseer on 2009-04-17
Tor is slow. If you're going to want to look at more than 1-3 websites or if the websites are going to contain any heavy media, Tor isn't very useful. What you really need is an encrypted or "secured VPN" service; this would allow you to connect to the service, like you would a proxy or Tor, and your communications would be encrypted between you and that service; the service would essentially be grabbing the site content for you and sending it back encrypted.

Edit:

I don't endorse, nor have I tried any of these; however, they should get you started if you choose that path:

[https://www.secure-tunnel.com/]("https://www.secure-tunnel.com/")
[http://ipredator.se/]("http://ipredator.se/")

You can also just search "vpn service" on Google to find a wider range. You'll want to look for one that's not going to be blocked by your country and one that will fit your personal and financial needs; I don't think very many of them are free and if they are they have their share of problems.

Also, here's a start on using WGet with a proxy: [http://firdauslinux.wordpress.com/2009/01/07/how-to-use-wget-with-proxy/]("http://firdauslinux.wordpress.com/2009/01/07/how-to-use-wget-with-proxy/")

---

### Post by andysuth on 2009-04-17
I'm aware of the shortfalls of TOR (slow, etc), but thought this might be forgivable if it gets me past "the great firewall" and if I'm only downloading Text from BBC or Guardian or Times etc.

Would the VPN method get me through the web censoring?

-Andy

---

### Post by codeseer on 2009-04-17
> **andysuth said:**
> I'm aware of the shortfalls of TOR (slow, etc), but thought this might be forgivable if it gets me past "the great firewall" and if I'm only downloading Text from BBC or Guardian or Times etc.

Would the VPN method get me through the web censoring?

-Andy

Yeah, a VPN would get you through the censoring; provided they allow you to connect to the VPN's range of IP addresses. I think it's a lot more likely that Tor nodes would be blocked than VPN services. Ideally you would want to check for the ability to ping the VPN services and if possible take one up on a trial offer; this lets you be 100% sure and get a feel of the latency. If you're looking for only the text of news type websites, you may consider just using an RSS feed with an RSS client and proxying it through Tor.

---

### Post by andysuth on 2009-04-17
I might try the VPN of my work then.

My other idea is to get people to email me cut/paste news stories when I'm over there.

The downside is I'm not going to know if it'll work until I get out there.

-Andy

---

### Post by codeseer on 2009-04-17
> **andysuth said:**
> I might try the VPN of my work then.

My other idea is to get people to email me cut/paste news stories when I'm over there.

The downside is I'm not going to know if it'll work until I get out there.

-Andy

Well, now if you have a system where you are now that you can configure some things on, you may be able to get it to automatically download those resources for you and put them in an encrypted container then email them to you each day.

Like if it was a Linux system you could configure a bash shell script and set it as a cron job.

You could also connect to your home system, if you leave it running and remote control it to view the content. That is if viewing the content wouldn't alert the people at Starbucks. You could encrypt that if you wanted also. If you're interested in this method, take a look at these links:

[http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop]("http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop")
[http://www.go2linux.org/how-to-connect-to-your-PC-opening-the-firewall-iptables]("http://www.go2linux.org/how-to-connect-to-your-PC-opening-the-firewall-iptables")

---

