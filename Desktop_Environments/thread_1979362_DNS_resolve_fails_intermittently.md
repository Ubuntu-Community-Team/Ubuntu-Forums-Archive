---
title: "DNS resolve fails intermittently"
date: 2012-05-13
forum: Desktop Environments
---

### Post by middlechild on 2012-05-13
[SIZE=2]Workstation 12.04 64-bit, using Firefox and Chromium too. All updates currently applied.

[/SIZE][SIZE=2]Access a web page by name, like [www.google.com]("http://www.google.com") and it fails. Not every time, yet often enough to be frustrating. My wife has moved back to XP as it works every time. [/SIZE][SIZE=2]My network is 3 computers connected via a Linksys router to ISP. All three utilize DHCP for all network settings. The two Win* machines do not have issues utilizing all settings as provided by ISP with respect to resolving web site names.

[/SIZE][SIZE=2]I am OK with blaming ISP DNS servers. Have tried to move resolve to Google servers through resolv.conf but that is automatically generated so did not edit the file. Tried to add new DNS settings to the interface directly, and use DHCP for IP only, but that does not change the problem either.

Anyone have suggestions? I am home for the next week, so can work on this as suggestions are made.
Thanks
Middle[/SIZE]

---

### Post by middlechild on 2012-05-14
[SIZE="2"]/etc/resolv.conf currently only has "nameserver 127.0.01" as an entry. This file is being automatically generated. The interface itself ETH0 has two DNS server entries, 8.8.8.8 and 8.8.4.4 as secondary. The interface is set for DHCP Address only.  Is anyone else experiencing issues with DNS resolution of destination web pages?  [/SIZE]

---

### Post by hawkmage on 2012-05-14
The Desktop edition of 12.04 now uses dnsmasq and resolveconf.  The resolvconf daemon runs on its own but dnsmasq is running as a plug-in to Network Manager.  

Even though my DHCP service was sending out the name servers to use dnsmasq/NetworkManger was not using it.

The only way I was able to get a new install of 12.04 to use my internal DNS properly was to comment out "dns=dnsmasq" from the /etc/NetworkManager/NetworkManager.conf file. 

Install the full version of dnsmasq and add the lines defining my DNS to the /etc/dnsmasq.d/dnsmasq.conf file like this:
```
server=192.168.1.5
server=192.168.1.6
```

Then in the /etc/resolvconf/resolv.conf.d/base file I added my domain and search statments that I wanted in the /etc/resolv.conf file.

---

### Post by middlechild on 2012-05-14
[SIZE="2"] /etc/resolvconf/resolv.conf.d/base  can you post an example?  I can get the domain from my home router, but is any other entry required or a label on  the domain entry?  Thanks[/SIZE]

---

### Post by hawkmage on 2012-05-14
This will only be helpful if you you are having issues with resolving just the host name not using the fully qualified name.  If you can not resolve the fully qualified name this is not going to help you.

Here is what I have in the /etc/resolvconf/resolv.conf.d/base
```
domain mydomain.com
search mydomain.com
```
Of course the "mydomain.com" is not the real domain name.

---

### Post by roelforg on 2012-05-14
8.8.8.8 and 8.8.4.4 are google's dns servers, they should be fine.
But i set mine to the nearest dns-root-server (the k-rootserver in my case),
If those blow out, almost the entire dns-system goes belly up in ~48-72hrs (that's when caches timeout),
so i'm safe as those things have better uptime than google has on most of their servers.

---

### Post by middlechild on 2012-05-14
[SIZE="2"]No internal host names in use here. I am using web browsers like firefox and chromium to get to public web sites. The suggestion here to move to a basic DNS package has been applied. There is some improvement, but the error is still happening.

go to [www.reddit.com](www.reddit.com), and right click on three different links to open in tabs.  Usually all will open in separate tabs, no issue. But one time out of four none of the tabs are successful and all give an error that DNS has timed out.

It seems like such a simple problem, you just statically assign a new pair of DNS servers and move on. But this is proving to be anything but simple.

I'd welcome any and all suggestions, at this point it might not be a DNS issue, but error message perhaps is a red herring. I don't know.   [/SIZE]

---

### Post by middlechild on 2012-05-19
[SIZE="2"]This is really annoying, that so many web pages come back with DNS Lookup Failed.[/SIZE]

---

### Post by middlechild on 2012-05-24
My next action will be to wipe out 64bit Ubuntu and try 32 bit, although the logic behind that thought process is so convoluted as to be downright silly.  But I have to try something.

---

### Post by theevilsharpie on 2012-05-24
If you've set your DNS servers to Google's DNS, and you're still having problems with DNS not resolving? Either your ISP is mangling DNS traffic, or you've got an error with your DNS configuration somewhere.

You say that Ubuntu has problems resolving DNS, but Windows XP doesn't? What is the difference in their network configuration? If you set XP to use Google's DNS servers, does it have problems resolving DNS names?

You may want to run a network trace is Wireshark while performing a DNS lookup to see what it's doing when the DNS lookup fails.

Edit: There's not going to be any difference between 32-bit and 64-bit Ubuntu when it comes to DNS name resolution.

---

### Post by typhoon_tip on 2012-05-24
I had frequent problems with those DNS servers as well, with any version of Ubuntu.

Please try use these instead:
```
208.67.222.222
156.154.71.1

```

Use the Network Manager to edit your net config, set DHCP IP bu manual DNS, so you can enter the DNS into the field (two items separated by commas).

They should be open DNS servers as well. Especially the second one, is quite fast and accurate.

Cheers !

---

### Post by theevilsharpie on 2012-05-24
> **typhoon_tip said:**
> I had frequent problems with those DNS servers as well, with any version of Ubuntu.

Please try use these instead:
```
208.67.222.222
156.154.71.1

```

Use the Network Manager to edit your net config, set DHCP IP bu manual DNS, so you can enter the DNS into the field (two items separated by commas).

They should be open DNS servers as well. Especially the second one, is quite fast and accurate.

Cheers !

For the purposes of troubleshooting, I would advise against using resolvers that hijack failed DNS requests.

---

### Post by alex1973 on 2012-06-08
Have you found a solution?
I have this problem since I have tried to disable dnsmasq (by commenting the "dns=dnsmasq" line in NetworkManager.conf) and add some custom hosts.
Rolling back did not make a difference. I have 2 more ubuntus (32bit, upgraded from 11.10) which work properly.
My current installation is a clean 12.04-64bit.

---

