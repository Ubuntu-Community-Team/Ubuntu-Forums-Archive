---
title: "Internet Problems Cann't Connect"
date: 2006-02-16
forum: Desktop Environments
---

### Post by FleetwoodMan1968 on 2006-02-16
****I'm not able to connect to the internet at all now was able to for about 10 min but at really slow speed's, my set up is as follows

computer - switch - router

i am able to ping google.com and my isp.  I am set up the same way on the windows machine that i am running but the ubuntu machine will not connect anymore always times out.  I would apperiate any help that i can get with this since i have 3 more computers in the house to set up with ubuntu.

---

### Post by yota on 2006-02-16
Hi,

please give us more details about your network config, type on terminal:
```

sudo su
cat /etc/network/interfaces
ifconfig
route
iptables -L

```
and paste here the results, so we can have a look.

---

### Post by handy on 2006-02-17
Have you turned off **ipv6** in Firefox?

My machine won't even connect unless I do the following in Firefox:

Enter **about:config** in the address field.

Then enter **ipv6** in the filter field.

Then double click on the entry to change it's boolean value to **true**.

That could be all you need, on some setups this is very powerful...

Post back if you do no good?

---

### Post by FleetwoodMan1968 on 2006-02-20
I'm actually on a different computer but all the ip address are correct according to my isp.  If you wouldn't mind telling me excatly what you need to keep me from typing all night long i would apperitae it 'cause i'm not entirley sure what you need, plus two of the commands you gave me previously do not work, maybe i'm misinturperting them.  Thank You for your response.

---

### Post by FleetwoodMan1968 on 2006-02-20
That was the trick, thank you very much!!!!

---

