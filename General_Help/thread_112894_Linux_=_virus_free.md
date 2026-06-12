---
title: "Linux = virus free?"
date: 2006-01-05
forum: General Help
---

### Post by sbasak on 2006-01-05
If I surf Internet through Ubuntu shall I be free of viruses?

Or I still need to use an anti virus & fire wall?

---

### Post by earobinson on 2006-01-05
a simple search for security and you find lots on this

[http://www.ubuntuforums.org/showthre...light=security](http://www.ubuntuforums.org/showthre...light=security)
[http://www.ubuntuforums.org/showthre...light=security](http://www.ubuntuforums.org/showthre...light=security) <- good debate

however this is an on going debate

---

### Post by Sef on 2006-01-05
> Or I still need to use an anti virus & fire wall?

A firewall you really should have.  Linux is harder to hack into than windows, but it still can be hacked.


> If I surf Internet through Ubuntu shall I be free of viruses?

If you run a Microsoft products through a program (wine, crossover, etc.) or use an email client, you need an anti-virus.  Even if linux can't get viruses, it still can pass them on.    So far there are no viruses for linux in the wild.   Though there were a couple of worms for apache server.

---

### Post by Rinzwind on 2006-01-05
earobinson: it gives an error 404 :(

I wish we had virusses. I want something to do :(

---

### Post by earobinson on 2006-01-05
[QUOTE=Rinzwind]earobinson: it gives an error 404 :(

I wish we had virusses. I want something to do :([/QUOTE]
lol so join a team, or program, or document.

lol i cut and paste that from this link [http://www.ubuntuforums.org/showthread.php?t=112480&highlight=security](http://www.ubuntuforums.org/showthread.php?t=112480&highlight=security) and the links got broken along the way.

this should work[QUOTE=earobinson]a simple search for security and you find lots on this

[http://www.ubuntuforums.org/showthread.php?t=9836&highlight=security](http://www.ubuntuforums.org/showthread.php?t=9836&highlight=security)
[http://www.ubuntuforums.org/showthread.php?t=98912&highlight=security](http://www.ubuntuforums.org/showthread.php?t=98912&highlight=security) <- good debate[/QUOTE]

---

### Post by sbasak on 2006-01-05
If I use Linux only for net surfing, email & Open Office use and mount Windows parition only as read only, do I still need worry about virus/hack etc?

---

### Post by ibook-linux on 2006-01-05
I was curious about the same thing so I scanned the hell out of my new ubuntu system and found every port blocked by default. It allowed pings but nothing else. So that means you should be fine, it will find the door but find it closed. I installed the firewall firestarter and repeated the process. Now all of my ports are not only closed but also stealthed. This is very cool, it means they will not even find a door. It did allow pings by default but I turned that off.

As for viruses I think linux is safe. I think I read a stat that last year had over 3,000 new viruses for windows and 30 for linux but none of the linux ones got past the lab stage. There are linux virus scanners avaliable for download if it really makes you feel better.

---

### Post by almostlinux on 2006-01-05
you need not...there are very few security vulns found in ubuntu and those found are fixed very quickly patched

make sure you have strong login passwords (like 'passcoDe$') and also stay updated

---

### Post by hobbit1983 on 2006-01-05
Hi sbasak,

In response to your second post If you are mounting your windows partition Read Only then you should be pretty safe from Windows viruses.

I would strongly recommend a firewall in particular a hardware firewall that performs NAT (Network Address Translation) as that "hides" your IP address from the rest of the internet and so makes any attempt to hack your machine a lot harder.

As for linux virus' I've used ubuntu for a while and not seen anything.

Hope this helps

---

### Post by magnusbb on 2006-01-05
But there are rootkits for Linux which can destroy your system. When first a Linux system is attacked, it is extremely vulnerable. It is important to know this.

---

