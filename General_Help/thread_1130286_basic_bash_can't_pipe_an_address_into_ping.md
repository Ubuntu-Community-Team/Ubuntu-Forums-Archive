---
title: "basic bash: can't pipe an address into ping?"
date: 2009-04-19
forum: General Help
---

### Post by chappel on 2009-04-19
I'm trying to learn more about bash and pipelines by coming up with a quick way to ping a default gateway.  So far I've got:

$route | grep default | cut -c 17-32

which spits out the default gateway, but I can't pipe that into 'ping':

$route | grep default | cut -c 17-32 | ping

just gives me the same as typing 'ping' (without an IP address).

I noticed the same thing if I do:

$echo 192.168.1.1 > test.txt
$cat test.txt | ping 

What am I missing?  I suspect it's something blindingly obvious...

---

### Post by mali2297 on 2009-04-19
The address is a command line argument for ping. It is not read from standard input, so piping does not work. Instead, try
```

ping $(route | grep default | cut -c 17-32)

```

---

### Post by chappel on 2009-04-19
Awesome!  that works.  I think I understand why, but I'll have to play with it some more.   

Thanks.

---

