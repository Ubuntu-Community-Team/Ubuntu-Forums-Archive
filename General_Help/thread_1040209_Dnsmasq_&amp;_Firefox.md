---
title: "Dnsmasq &amp; Firefox"
date: 2009-01-15
forum: General Help
---

### Post by redilyn on 2009-01-15
Hey,

Just got a question.

I have dnsmasq setup and when I run dig domain the first time it will be approx 100ms second time it will be 0ms.

So heres the question.

I was browsing the ubuntuforums and decided to check to see if firefox was using dnsmasq.

So I went to the terminal and typed

```

dig ubuntuforums.com

```

The first time was approx 100ms second time was 0ms

It seems to be that firefox is by passing the dnscache otherwise it would have been 0ms on the first dig.

Does that sound correct? If so how can I make firefox use the cache.

---

### Post by Chlorhydrikk on 2010-05-18
Sorry if the topic is old but it had no answer.
Try pressing CTRL + F5 !

---

### Post by redilyn on 2010-05-18
That just refeshs the page... Doesn't have much to do with the dnsmasq cache.

It also doesn't change the results.

Open ubuntuforums.com
Then dig ubuntuforums.com - Response time 100ms
Now dig ubuntuforums.com again - Response time 1ms

So firefox is not using dnsmasq cache at least as far as I can tell.

I gave up on this a looong time ago :)

---

### Post by odejoy on 2010-11-28
> **redilyn said:**
> So firefox is not using dnsmasq cache at least as far as I can tell.

I gave up on this a looong time ago :)

Can some Firefox/dnsmasq guru please shed light on this?

I am facing the same problem and it is killing me!
Why won't firefox dns queries be routed via dnsmasq? :frown:

---

### Post by bodhi.zazen on 2010-11-28
You have to configure firefox to use it:

[http://ubuntuguide.net/speed-up-web-browsing-in-firefoxopera-using-local-dns](http://ubuntuguide.net/speed-up-web-browsing-in-firefoxopera-using-local-dns)

See the last few screen shots.

---

