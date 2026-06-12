---
title: "Need help with priority (&quot;nice&quot;)"
date: 2009-04-25
forum: General Help
---

### Post by lovinglinux on 2009-04-25
I'm trying to use "nice" to set a program priority, but I find the options confusing. The man page says it goes from -20 to 19. As far as I understood, a negative value will give more priority then a positive value :confused:

What I need is to setup Firefox and Avidemux so I can browse the web decently while encoding a video. I tried using these commands:

```
nice 19 avidemux
nice -20 firefox
```

but I don't see any difference from using 

```
nice -20 avidemux
nice 19 firefox
```

Regardless the settings a choose above, Firefox is still sluggish while encoding and the cpu load assigned to "nice" is always high.

On Windows I had an option to make the encoder work in the background. Is it possible to do that? I don't care if it takes a lot longer to enconde, as long as I can do other stuff without lag.

---

