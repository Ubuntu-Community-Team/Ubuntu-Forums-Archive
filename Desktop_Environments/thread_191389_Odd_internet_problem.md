---
title: "Odd internet problem"
date: 2006-06-07
forum: Desktop Environments
---

### Post by Drakonik on 2006-06-07
I orignally posted this in the wrong forum, so I'm reposting here.

I installed Dapper Drake and everything went fine, and I didn't get any error messages or have any problems, until I set up my wireless network. I can access email via Evolution, and I can go to google.com, but that's it. Every site I've tried is inaccessible. I don't get the 'Couldn't connect to server error'. I just get an about:blank page. Is there soemthing wrong with what I did, or is there something wrong with Dapper?

---

### Post by Drakonik on 2006-06-07
(Legal?) bump.

---

### Post by jvictor on 2006-06-07
Is IPV6 disabled on ur machine, search the forum on how to do that

---

### Post by Drakonik on 2006-06-07
I'm 90% certain that I saw an option, and I'm 70% sure that it wasn't disabled. That comes to a 63% chance of me being right. I'll reboot, check, and report back.

Edit: IPv6 is enabled. Also, I can use Gaim and access all of my accounts. I am getting more and more confused by this. 'Tis a real headache.

---

### Post by Drakonik on 2006-06-07
*sigh* Bump'd again.

---

### Post by jvictor on 2006-06-07
Well I meant to disable it. It can make the system behave pretty wierd . Sorry for the mixup

---

### Post by Drakonik on 2006-06-07
I don't know. I read a thread about how IPv6 only messes things up if youconfigure it imporperly, and since i havne't configured it at all...

---

### Post by jvictor on 2006-06-07
Search the forum on "disable ipv6" do the steps, reboot. It should work fine

Another reason maybe that u need to give ur ISPs DNS server in etc/resolv.conf

---

### Post by Drakonik on 2006-06-07
I'll look it up and post back if it doens't work.

---

### Post by Drakonik on 2006-06-07
Okay. I know that it's NOT IPv6 that's hurting me.

The problem is, I don't know what else there could be. *sigh*

---

### Post by jvictor on 2006-06-08
Are u able to ping any random website ? If so try disabling ipv6 in firefox.

type about:config in the add bar

and set the value of network.dns.disableIPv6 to true

---

