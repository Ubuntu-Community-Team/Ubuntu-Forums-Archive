---
title: "[SOLVED] Too much Space inserted by a space!"
date: 2008-06-23
forum: Desktop Environments
---

### Post by underwater on 2008-06-23
Hello,

I have a weird problem all of a sudden.  It appears that, out of nowhere, my spaces are HUGE!  In other words, when I press the spacebar, instead of a normal space I get a space that is the size of like maybe 10 spaces!  It isn't actually inserting that many spaces, it is just that a single space has grown huge!

---

### Post by lisati on 2008-06-23
> **underwater said:**
> Hello,

I have a weird problem all of a sudden.  It appears that, out of nowhere, my spaces are HUGE!  In other words, when I press the spacebar, instead of a normal space I get a space that is the size of like maybe 10 spaces!  It isn't actually inserting that many spaces, it is just that a single space has grown huge!

Is it happening in just one context (such as Open Office writer) or in everything?

---

### Post by underwater on 2008-06-23
> **lisati said:**
> Is it happening in just one context (such as Open Office writer) or in everything?

I thought it was everything, including GTK apps, but now I'm not so sure.  It might just be Mozilla type apps.  At first I thought it was all apps because Liferea also had the problem, but I just realized that the rendering for Liferea is probably done through mozilla somehow.

---

### Post by lisati on 2008-06-23
> **underwater said:**
> I thought it was everything, including GTK apps, but now I'm not so sure.  It might just be Mozilla type apps.  At first I thought it was all apps because Liferea also had the problem, but I just realized that the rendering for Liferea is probably done through mozilla somehow.
I'm not sure what settings to check for GTK apps....

---

### Post by underwater on 2008-06-23
Ok, I happened to find the problem in a bug listing reported by Debian people. The workaround for the fix was to purge

pango-graphite

I did this with

```
sudo aptitude remove --purge pango-graphite 
```

In case this comes up in the future

---

### Post by bpedman on 2008-06-24
oh my goodness!!! you are a life saver...I somehow messed up firefox 3 and all the spacing was HUGE...this fixed it, thanks!

---

### Post by MatthewPlanchard on 2008-06-29
Thanks for this solution!

I had installed pango-graphite while trying to get the stackswitch plugin to install for Compiz. When I went to do a 'make', it told me that pangocairo.pc was not found.

At first I just installed all the pango packages I could find, and eventually learned about the command 'apt-file search' and used that to get the right library.

Thanks again for your help!

---

