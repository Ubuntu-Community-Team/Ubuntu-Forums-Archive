---
title: "service manager application in Lucid"
date: 2010-05-02
forum: Desktop Environments
---

### Post by murataht on 2010-05-02
Hello all,
since my upgrade to Lucid, I have not been able to find "service manager" application in the "system" -> "administration" menu. It had been there in Juanty, and it had helped me to configure which services (like mysql, apache ,etc) I would like to start with the system. I have searched it in "synaptic package manager", and it is not there. 
So my question is:
1) where can I find this nice application? (service manager)
2) If it is not there anymore, is there anything else that will do the same? Or should I call help for "command line" to achieve this?

Thanks

---

### Post by Anilm3 on 2010-05-03
It would be very interesting to know any alternative since there is no service manager anymore...

The only thing I can think of is going directly to the different RC directories, but there should be an application for that...

---

### Post by Anilm3 on 2010-05-03
I found a nice services manager called bootup-manager, you can find it using apt with the name bum.

---

### Post by lecadre on 2010-05-20
same problem, Can't find System -> Administration -> Services...

Funnily in the same distro (lucid) the 
System -> Adminstration -> Printing 
says when you use Troubleshoot that you should use 
 System -> Administration -> Services
to start CUPS if it is not running...

Early days hence I do not want to draw any conclusions yet about 10.04.

---

### Post by woofti on 2010-05-29
Let's hope it comes to the attention of those to whose attention such things must come. I'm having difficulty getting my Canon printer to work under Lucid and this isn't helping a novice like me.

---

### Post by hok00age on 2010-05-29
> **murataht said:**
> Hello all,
since my upgrade to Lucid, I have not been able to find "service manager" application in the "system" -> "administration" menu. It had been there in Juanty, and it had helped me to configure which services (like mysql, apache ,etc) I would like to start with the system. I have searched it in "synaptic package manager", and it is not there. 
So my question is:
1) where can I find this nice application? (service manager)
2) If it is not there anymore, is there anything else that will do the same? Or should I call help for "command line" to achieve this?

Thanks

Via command line:
1. Check status of all services
   ```
sudo service --status-all
```
2. Stop service
   ```
sudo service <service_name> stop
```
3. Start service
   ```
sudo service <service_name> start
```

Via GUI:
```
sudo apt-get install bum && sudo bum
```

Hope it helps
Regards :)

---

