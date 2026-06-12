---
title: "Evolution Exchange User Experience Terrible Lots of hangs"
date: 2009-07-18
forum: Desktop Environments
---

### Post by theglowblue on 2009-07-18
Anyone have trouble with Evolution Hanging when working with an exchange server? Is this common behavior or may I just have configured my account setting wrong? 

I am forced to used evo against exchange since my company does not enable pop / imap for their mail system, just exchange. 

It hangs for me many times a day, and I use "evolution --force-shutdown" to close the program get the sucker working again quickly

It seems to always do this if I disconnect from a network, and try to reconnect again (i am a road warrior so this happens many times a day, across many networks) But it is not isolated to this, it also happens while connected to the same network persistently. All of a sudden the client will go into neverland....behaving as if some network look up is timing out. 

Any tips and pointers dealing with evolution hangs would be great!

This is mostly a gripe post, but since I have not been able to find too many resources regarding this on the net, i thought i would post here.  

I am running jaunty with evo 2.26.1

My account is setup as so

Type = Exchange
username = first initial + lastname  eg (xlastname)
OWA URL = [https://mail.domain.net/exchange](https://mail.domain.net/exchange)
mailbox = firstname 

Thanks for any help

---

### Post by dc2447 on 2009-07-23
I can't help other than to say I get the same behaviour.

I can hang exchange everytime by searching my exchange inbox

Running evolution from a terminal produces no data and strace hangs my system, thus impossible to raise bugs

---

### Post by VitalBodies on 2010-01-14
Did you try this at the terminal:
```
gdb evolution
```
Then 
```
run
```
Evolution will start and you can watch the terminal for errors. 
If it crashes try this command for a back trace. 
```
(gdb) thread apply all bt
```

Also, does Evolution unfreeze if you reconnect to the internet?

---

### Post by claes.lillieskold on 2010-02-08
Yes. Evolution used to be one of the best email clients.
Perhaps adjusting to exchange was a bit troublesome.

Searching used to be very fast, and very accurate. It is no more.

And searching for addresses, usually hangs the program for about 2 minutes. This could problably be solved by caching the address book locally, instead of requesting it from the exchange server each time. But I'm just guessing about the implementation here.

Sorry about complaining, but Evolution used to be blazingly fast and nice, and the latest years development hasn't really impressed me.

---

### Post by Alexandre Putt on 2010-02-08
Have you tried updating it? Maybe it will help.

---

