---
title: "Can I use the service dyndns.org at file hosts.allow"
date: 2009-04-27
forum: General Help
---

### Post by jordi7 on 2009-04-27
First of all, sorry for my english.
I'm using 3 PC's at work (1 with ubuntu and 2 with kubuntu) and i want to acces at these pcs from home. I have dynamic IP at home and i've created a DynDNS hostname wich always point to my ip.
I wrote this hostname (xxxxx.dyndns.org) in /etc/hosts.allow file but when i'm trying to connect from home at work, the server rejects me the connection.
First, ¿Is it possible use a  dyndns pointer in the file /etc/hosts.allow? If that's possible ¿where's the problem?¿What else i have to do?

thank you everyone

---

### Post by John Cheng on 2009-04-28
It is unlikely that your hosts.access file is the reason why you cannot connect. From the man page (man hosts.allow):

```
       The access control software consults two files. The search stops at the
       first match:

       o      Access  will  be  granted when a (daemon,client) pair matches an
              entry in the /etc/hosts.allow file.

       o      Otherwise, access will be denied  when  a  (daemon,client)  pair
              matches an entry in the /etc/hosts.deny file.

       o      Otherwise, access will be granted.

```

At home - check for other possible blocks - routers, does your ISP block any ports, is the service you are connected to correctly configured.

---

### Post by jordi7 on 2009-04-28
Thankyou for your answer.

The problem is that if I write my dynamic ip (xx.xx.xx.xx) in the file hosts.allow then i can acces withou problems the pc work from home. But if instead i write the dns host (myuser.dyndns.org) in the file hosts.allow, then i can't acces the pc work from home, and de dns host (myuser.dyndns.org) is linked to my ip! (xx.xx.xx.xx).
Therefore I think the problem is how i write the dns host (myuser.dyndns.org) in the file hosts.allow.

---

### Post by John Cheng on 2009-04-28
I see. Does that mean you have something in /etc/hosts.deny that would've blocked the connection (i.e., ALL: PARANOID)? I was not expecting that.

Looking at the man pages again, matching host names requires a "leading dot". So your entry should look like

```

ALL: [COLOR="Red"]**.**[/COLOR]myuser.dyndns.org

```

Did you have a leading dot in the name?

Also, just to be careful, please run 

```
nslookup myuser.dyndns.org
```

On the server to make sure "myuser.dyndns.org" into the right IP on that machine.

---

### Post by max_power on 2009-04-28
make sure you firewall is not blocking inbound connections. also, make sure you set up port forwarding on your router.

---

### Post by jordi7 on 2009-04-30
> **John Cheng said:**
> I see. Does that mean you have something in /etc/hosts.deny that would've blocked the connection (i.e., ALL: PARANOID)? I was not expecting that.

Looking at the man pages again, matching host names requires a "leading dot". So your entry should look like

```

ALL: [COLOR=Red]**.**[/COLOR]myuser.dyndns.org

```Did you have a leading dot in the name?

Also, just to be careful, please run 

```
nslookup myuser.dyndns.org
```On the server to make sure "myuser.dyndns.org" into the right IP on that machine.

I run nslookup myuser.dyndns.org, and it shows the correct IP. But I tryied with:

```

ALL: [COLOR=Red]**.**[/COLOR]myuser.dyndns.org

```

and does not work either. It doesn't work with or without the dot, but it works with the dynamic ip... but myuser.dyndns.org is pointing correctly to the IP!
I can't understand where is the problem.. what else can i try? Thx!

---

### Post by John Cheng on 2009-05-01
Like I pointed out previously, I would suspect you have something in /etc/hosts.deny or DNS lookup that could be causing your problem. However, without knowing more about your system, it is difficult to suggest anything new.

---

### Post by jordi7 on 2009-05-04
> **John Cheng said:**
> Like I pointed out previously, I would suspect you have something in /etc/hosts.deny or DNS lookup that could be causing your problem. However, without knowing more about your system, it is difficult to suggest anything new.

Well, the file /etc/hosts.deny has only the line:

```
ALL:ALL
```

---

### Post by John Cheng on 2009-05-04
Sorry, it looks like you were using the right configuration. The problem is something else....

I just realized why this doesn't work for you. The problem is that your server is not able to lookup the hostname from the IP address. In your case, your server sees the IP address of connection, but it doesn't know that IP belongs to user.dyndns.org. In fact, when it looks up the hostname for your IP, it will get a very different name than user.dyndns.org. Try it youself with

```

nslookup user.dyndns.org

```

Unfortunately, it is very unlikely you will be able to get reverse IP lookup tp work (read this [[COLOR="RoyalBlue"]_article_[/COLOR]]("https://www.dyndns.com/support/kb/reverse_dns_in_custom_dns.html").  from dyndns.org) :(

Perhaps, instead of relying on /etc/hosts.acces and /etc/hosts.deny for security, you can use a combination of firewall and ssh for your security needs?

---

