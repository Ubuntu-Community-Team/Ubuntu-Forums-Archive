---
title: "[SOLVED] RAM Metering: Why So Much Discrepancy?"
date: 2008-12-25
forum: General Help
---

### Post by Mark76 on 2008-12-25
Seriously. Top says I'm using nearly all available RAM, whilst GKrellm says I have over 500 MBs left. And htop disagrees with both

What's up with that?:confused:

---

### Post by Greyed on 2008-12-25
On the top display how much do your buffers/cache add up to?  :popcorn:

---

### Post by Mark76 on 2008-12-25
469180 Kilobytes

---

### Post by imtheguido on 2008-12-25
While on the topic of RAM I am slightly curious, why does the system use so much of my RAM in cache? Doesn't that mean that if there is a spike and a need for that ram, that it may not be able to dump the cache fast enough to access what it needs and cause a crash? I may be totally wrong here, but if someone could please explain it would be awesome. And sorry that I cant help your problem! >.<

---

### Post by cooldude on 2008-12-25
if i remember correctly...the operating system grabs most of the unused ram in cache/buffers so some programs report it as being used. Some programs recognize that fact and automatically show it being free like gkrellm.

Even though this ram is in cache/buffers its basicly not being used.

---

### Post by Mark76 on 2008-12-25
So I can trust gkrellm but not top.

Thanks :)

---

### Post by cooldude on 2008-12-25
both are right but have to do some basic math to get the correct free ram in top

I believe cache+buffer+free=total amount free. Actually it does show it in top. if you check it has two free's the highest free includes cache & buffers in total amount.

---

### Post by cooldude on 2008-12-25
oops one free was for swap space, so strike that.

---

### Post by Greyed on 2008-12-25
> **Mark76 said:**
> So I can trust gkrellm but not top.

Thanks :)

No, you can trust both.  Po**tae**to, po**tah**to.  One reports the memory as used, the other reports it as free.  They're both right for the explained reasons.

---

### Post by Mark76 on 2008-12-25
Okay, thanks

---

