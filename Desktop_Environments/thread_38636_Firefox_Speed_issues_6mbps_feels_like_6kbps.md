---
title: "Firefox Speed issues 6mbps feels like 6kbps"
date: 2005-06-01
forum: Desktop Environments
---

### Post by byen on 2005-06-01
Hey guys.....
Im a brand new ubuntu convert and am pretty impressed as to how far this community has come..everything works perfect except for one big problem.

While using firefox my 6mbps connection feels like 6kbps!!! FOr example..it takes about 3-6 seconds to load..google.com! During windows use..it is as fast as it should be.. but on ubuntu its as good as a 6kbps dialup! downloads are superfast but its just regular browsing that sucks! IS there a proper way to fix this.

I spend a lot of time on the browser and I really need this! Help me out fellas!

thank you!

---

### Post by tread on 2005-06-01
Here's one suggestion:
In the URL bar go to "about:config"
Find the setting for "network.dns.disableIPv6", and set it to true.

---

### Post by byen on 2005-06-01
[QUOTE=tread]Here's one suggestion:
In the URL bar go to "about:config"
Find the setting for "network.dns.disableIPv6", and set it to true.[/QUOTE]
 thank you for the sugg. I did try that and I see a diff! but not much! still takes time loading pages.. here is what happens.. once i type a url... it looks like firefox stalls for a sec or2 and then the whole page shows up all at a time... say for instance I hit [www.ubuntuforums.org](www.ubuntuforums.org) ;-)  firefox seems to wait for about 2 secs before it actually reacts to the action and then the whole page loads at-once...
my question is why is it waiting before it loads the page?

Once again... I really appretiate the help guys!!!

---

### Post by shakin on 2005-06-01
Which of these does it say when it's stalling?

- "Looking up <domain name>" 
- "Waiting for <domain name>"
- "Transferring data from <domain name>"

That will tell us where the problem is. My bet is on the first one, which points to a DNS issue.

---

### Post by byen on 2005-06-01
Yup! it is the first one.. so i guess it is a dns issue? what should my next step be?

---

### Post by tread on 2005-06-01
nice timing for this howto :)
[http://ubuntuforums.org/showthread.php?t=38646](http://ubuntuforums.org/showthread.php?t=38646)

---

### Post by shakin on 2005-06-01
[QUOTE=tread]nice timing for this howto :)
[http://ubuntuforums.org/showthread.php?t=38646](http://ubuntuforums.org/showthread.php?t=38646)[/QUOTE]

That how-to is misleading. Read my post on the second page about changing the nglayout.initialpaint.delay setting to zero. In short: don't do it because it will slow down your page rendering time. Pipelining is the only useful tweak unless you want to do some memory tweaks (though they're of questionable value).

Anyway, no browser tweak in the world is going to make your DNS server respond quicker. You have to change to a different DNS server and luckily your ISP probably provides you with two or three options.

Find the Networking app in the Administration menu. You may need to setup your computer to use a static IP to get this to work between reboots or you can probably prevent /etc/resolv.conf from being overwritten by changing the permissions on it. One of the Networking tabs is for DNS. Write down the IPs of those servers and the order they're in. Now remove them and enter them in a different order. The first server is garbage, so toss it. If you have three DNS servers, put the last one in the first place. Once you're done, just quit the Networking app by clicking 'okay' and see if Firefox is faster.

---

### Post by tread on 2005-06-01
Oh, ok .. thanks for the info shakin. I hadn't read the howto cos I use opera, and dont have dns issues. But I'll read your comments a bit more carefully.

---

### Post by byen on 2005-06-01
[QUOTE=shakin]That how-to is misleading. Read my post on the second page about changing the nglayout.initialpaint.delay setting to zero. In short: don't do it because it will slow down your page rendering time. Pipelining is the only useful tweak unless you want to do some memory tweaks (though they're of questionable value).

Anyway, no browser tweak in the world is going to make your DNS server respond quicker. You have to change to a different DNS server and luckily your ISP probably provides you with two or three options.

Find the Networking app in the Administration menu. You may need to setup your computer to use a static IP to get this to work between reboots or you can probably prevent /etc/resolv.conf from being overwritten by changing the permissions on it. One of the Networking tabs is for DNS. Write down the IPs of those servers and the order they're in. Now remove them and enter them in a different order. The first server is garbage, so toss it. If you have three DNS servers, put the last one in the first place. Once you're done, just quit the Networking app by clicking 'okay' and see if Firefox is faster.[/QUOTE]
 I only have one DNS server listed. Oh boy am I lost :-(

---

