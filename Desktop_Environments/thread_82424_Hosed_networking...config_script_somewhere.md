---
title: "Hosed networking...config script somewhere?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by maruchan on 2005-10-26
Hi,

After installing Breezy over Hoary, I noticed that Synaptic couldn't talk to all the repositories, so I did a forum search for the problem. I saw a bunch of terms like "router blah blah static DNS blah blah" so I installed these three recommended packages using apt, edited a file containing nameserver information (don't remember what it was), and *now*, after all that, I suddenly cannot network or surf the web at all. Ouch.

Is there a script out there that will autodetect and configure the network for me? I have no idea what I did or how to fix it, and I get this feeling it will be a bugger to fix manually. (If someone knows what I did and wants to tell me how to fix it, that's fine too)

Thanks for any help!

---

### Post by Kyral on 2005-10-26
Hmm, look in /etc for backup files....

They usually have either ~ in front or .bak appended...

---

### Post by maruchan on 2005-10-26
Thanks, it's good to know that. I'm pretty sure I changed the edited file back to what it was before, and it didn't change anything...I'm wondering if installing those three networking apps was what did it.

How do you restart the network from the console?

---

### Post by Kyral on 2005-10-26
```
sudo ifdown <interface>
```

then

```
sudo ifup <interface>
```

Interface is usually eth0

To see if it worked just
```

ifconfig
```

And if you see an IP Address it usually means it worked

---

### Post by maruchan on 2005-10-26
Ah, I think the file I edited was: /etc/resolv.conf

---

### Post by Kyral on 2005-10-26
Well, does it work now </Stupid Question>

---

### Post by maruchan on 2005-10-26
Ok...thanks for the info, Kyral...I am going to print this out and reboot into Ubuntu when I am reasonably confident I can fix it.

I found the names of the three apps I installed:

1. resolvconf
2. pump
3. dnsmasq

Should I remove these? Could they have caused this problem?

---

### Post by maruchan on 2005-10-26
Okay Kyral...I rebooted and suddenly everything works except this, at startup:

"reloading postfix config....failed"

Is this something I can fix?

Thanks for the help!

---

### Post by maruchan on 2005-10-26
Okay...updated system, rebooted and Postfix loaded up just fine. This is so cool, everything works now! :D

---

