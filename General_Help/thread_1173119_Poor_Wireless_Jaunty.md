---
title: "Poor Wireless Jaunty"
date: 2009-05-29
forum: General Help
---

### Post by Gibbs on 2009-05-29
Ever since upgrading I've had a really poor wireless strength (and connection speed). On Windoze it runs as expected. I've tried running nm-applet with ndiswrapper (which is what I used prior to the upgrade) but it doesn't connect for some reason.

I know this post is pretty vague but does anybody have any pointers?

---

### Post by prem1er on 2009-05-29
What type of wireless card are you using?

```
lspci
```

---

### Post by TeoBigusGeekus on 2009-05-29
Get rid of gnome network manager and install wicd.

---

### Post by Gibbs on 2009-05-29
> **TeoBigusGeekus said:**
> Get rid of gnome network manager and install wicd.

Thanks, seems to have improved. Still 25% signal from a router 2 meters away is pretty poor. Ah well, 10x better :)

Edit: Actually I think the signal is bugged but still the connection speed has improved.

---

### Post by Gibbs on 2009-05-29
Double post...

Wicd is brilliant, the connection strength is at 90+%. Only problem is it disconnect every 20 seconds and reconnects. Any idea why that could be? As you can imagine that's very annoying.

Edit: Unticking "Use dBm to measure signal strength" seemed to do the trick. All sorted, thanks again.

---

