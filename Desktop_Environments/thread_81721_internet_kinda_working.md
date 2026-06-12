---
title: "internet kinda working"
date: 2005-10-25
forum: Desktop Environments
---

### Post by pacoo2454 on 2005-10-25
hey
ive been using ubuntu for about a week now and i love it so far but just recently  ive been having some problems with the internet

at first it worked fine, i could connect to the internet no problem and everythign was great but when i came home from school today it was totaly gone. i restarted hoping this would fix the problem but now all i can do is geton gaim and access the ubuntu forums, nothing else. i tried google on both my linux and windows box to make sure it wasnt down or anything or to see if it was just MY internet but it works find on my windows box. ive searched and i havent really found anyone with this same problem.

thank you!
-jeff

---

### Post by migueljacq on 2005-10-25
Hi, I've got two questions for you:

1) Are you on dialup or DSL?

2) Are you running some sort of firewall (i.e Firestarter)

---

### Post by pacoo2454 on 2005-10-25
im on dsl
and im not behind any firewall

like it said, it worked fine earlier today, then when i got home it just wasnt connecting

it can log into gaim and ubuntuforums

---

### Post by sam hassell on 2005-10-25
I'd suggest you have not configured DNS correctly. 

This would explain why Gaim is still working (IM relies on IP Addresses as opposed to domain names i think). It is still strange that you can see the forums... oh well..

Test your DNS settings at the command prompt by typing:

```
ping google.com
```

If this fails to return an answer, try:

```
ping 216.239.37.99
```

If the results are similar to what is shown below, your pc can see google.com, but does not recognise it's domain name.

```
PING 216.239.37.99 (216.239.37.99) 56(84) bytes of data.
64 bytes from 216.239.37.99: icmp_seq=1 ttl=232 time=330 ms
64 bytes from 216.239.37.99: icmp_seq=2 ttl=232 time=331 ms
64 bytes from 216.239.37.99: icmp_seq=3 ttl=232 time=362 ms
```

If this is your problem, try changing the DNS address by drilling System>Administration>Networking and choosing the DNS tab.

HTH.

---

### Post by pacoo2454 on 2005-10-25
ok
well i did ping google.com and got the same results that you posted, so i went into the System > Networking > DNS but im not to sure what to do here
everything seems to be fine, the DNS servers that are listed are the ones that my modem sets up

the search domain is domain.actdsltmp if that means anything

---

### Post by bionnaki on 2005-10-25
you get dns addresses from your isp right?

---

### Post by pacoo2454 on 2005-10-25
omg i got it working!
i switched the order of the servers listen with the DNS my isp gives me on top and then the one my modem sets up on bottom.

thanks for all the help and im really excited about using linux, very noob friendly community
:p

---

### Post by NewWithoutClue on 2005-10-25
This community is great!:)

Paul.

---

### Post by sam hassell on 2005-10-25
what an obvious solution (NOT) :p 

Glad to be of assistance!

---

### Post by pacoo2454 on 2005-10-25
yeah, i dont really know why it would matter but i guess it does, hope this helps anyone else that may get the same problem as me! id love to give back to this great place!
jeff!

---

### Post by migueljacq on 2005-10-25
actually i had a friend who had a similar problem with the dns, we had left some sort of local test nameserver in there and it was at the top. came back and couldn't get online - seems it's not just a list but an order of priority.
interesting, anyway glad to hear it's working

---

