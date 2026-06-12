---
title: "Saving a hardware compatabillity report?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by challis on 2006-07-12
Hi

Is there anyway on the livecd to save a hardware compatabillity report to a flash drive?

Where I work I have access to a range of laptops, and may be able to run the dapper live cd. However, it is unlikely i'd be able to put it on the network, so i'd need to save the report to submit from home.

Right now, i'd have access to ~30 different toshiba models, and also a couple of acers.

Cheers,

Adam

---

### Post by gsdefender on 2006-07-12
I'm not sure I have correctly understood your question, but if you want, say, to keep a log of the features your current system sports, you could do a 

```
for $a in cmdline cpuinfo crypto devices dma interrupts iomem ioport meminfo misc modules; do cat /proc/$a >> /tmp/report; echo **** >> /tmp/report; done
```

I think you can also find the files in /var/log/* useful.

---

### Post by challis on 2006-07-12
If my memory serves me right, as im at work at the moment, there was a tool in ubuntu which you could use to report back what hardware works under ubuntu and what doesnt.

But as far as i know, this software sends the info to a server across the net, and if i can test ubuntu with the livecd on these machines, I will not be able to place them on our network.

I'd like to do this as it would be my way of giving back to the community.

I've a feeling that command line you gave me would be overkill, as I wouldnt know what would be useful to people.

Adam.

---

