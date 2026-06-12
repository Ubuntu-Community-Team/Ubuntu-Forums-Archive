---
title: "Very Strange FireFox Problem"
date: 2006-08-25
forum: Desktop Environments
---

### Post by lonelypauly on 2006-08-25
I Just did a clean install of Dapper/Gnome and dl/installed all 163 or so of the updates.  I started Firefox and was unable to connect to any website. The Ubuntu home page URL that comes up is a local file.  I've restarted the computer after the updates, but to no avail.  I am scratching my head over this as the internet connection obviously works fine.

This is my moms machine...i told her how cool and easy to use ubuntu is...LOL.

Any ideas?

---

### Post by FuriousLettuce on 2006-08-25
Can you ping websites? If so, can you connect to them straight afterwards in Firefox? For instance, if you do

```
ping www.ubuntu.com
```

can you then use firefox to get to ubuntu.com? If so, it might be worth disabling IPv6 in Firefox:

Type about:config in Firefox, then find the entry **network.dns.ipv6disable** and double click on it to set it to true. Can you then get into other websites?

---

### Post by RobCampbell on 2006-08-25
You may have a problem with your nameserver. i.e. not having one. If you type this into firefox, what do you get? It's Google's IP address so you should get to google.com if your network connection is working but you have no nameserver. 

[http://72.14.221.104/](http://72.14.221.104/)

The IP address of your nameserver should be in your /etc/resolv.conf
e.g. mine contains the wireless router's ip address

search cablemodem
nameserver 10.0.1.1

---

### Post by RobCampbell on 2006-08-25
Also, please state the problem more clearly next time. From what you've written, one might think that you're simply having problems changing the home page preference in Firefox. I was assuming you know how to do that (Edit>Preferences>General) :-)

---

### Post by lonelypauly on 2006-08-26
Rob,

How should I have worded it?  

I'm going to try what you all mentioned today...*crosses fingers.

---

### Post by Lorian on 2006-08-26
> **lonelypauly said:**
> How should I have worded it?
Depends what the problem is ;)

---

### Post by phosty on 2006-08-26
Hi,

I too had a problem getting internet connection with a fresh (1st time ever) install of Ubuntu. I tried the suggestions of Furious Lettuce and found I could ping websites but not view them in Firefox. When I disabled IPv6 in the about:config Firefox it works. So I am pretty happy.

However, could you explain why this was an issue? Wouldn't it be more sensible to have Unbuntu install with IPv6 disabled as default? Or is this error just perculiar to a minority of people (I don't think I have an odd setup - I connect via a router)?

Anyway, thanks for the tip. Just got to search these forums now to find out if I can setup my RocketRaid 1640 card in Ubuntu!

Cheers

---

### Post by lonelypauly on 2006-08-26
I disabled IPv6 and everything is fine now.  Thanks for your input guys. 

What is IPv6 anyway?

---

### Post by mgmiller on 2006-08-27
> What is IPv6 anyway?
IPV6 is the "next generation" of internet addressing.  Currently we use IPv4 which is 4 numbers seperated by a .  (for exapmple, 72.14.221.104)As the internet grows, we are running out of unique numbers, so they are going to a scheme that allows more numbers.  Kind of like going from 6 digits to 7 in US phone numbers and then adding a 3 digit area code and then adding more area codes as we ran out of phone numbers.

---

### Post by fragos on 2006-08-27
The network can exist with both IPv4 and IPv6 running at the same time.  Virtually no one uses v6 at this time.  The default install tries v6 on every call to DNS and if a v6 DNS server doesn't answer it tries v4.  The v6 time out causes delays.  DNS returns an IP v4 or v6 which then works directly without time outs.  The goal was to insure Linux worked with both and assuming that IPv6 would replace v4 there would over time be no delays.

---

