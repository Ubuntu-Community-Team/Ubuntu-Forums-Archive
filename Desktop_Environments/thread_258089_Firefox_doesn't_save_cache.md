---
title: "Firefox doesn't save cache"
date: 2006-09-15
forum: Desktop Environments
---

### Post by Mike-Bell on 2006-09-15
I've noticed my firefox doesn't save data when closing it. I've got 200Mb for cache, but when I close it, nothing has been saved. In the cache options screen I don't have checked "Clear private data when closing firefox"

However, passwords, cookies, etc... are stored correctly.

Any idea will be really apreciated.

Thanks

---

### Post by editrix on 2006-09-15
I've never gotten a Mozilla browser to cache websites. I'm on dialup and use wwwoffle, which is marvellous. I'll assume it works if you're on DSL,too. Just install with Synaptic (or apt-get). Then, in FF Preferences,
General/Connection Settings set up your HTTP proxy to localhost on Port 8080.

---

### Post by radiojef on 2006-09-22
I cant get my Firefox to save the cache either...I have to beleive that others have it working. Everyone else can't just be dealing with it not saving...can they? Anybody got any good advice other than change browsers?

---

### Post by kerry_s on 2006-09-22
Did you guy's check about:conf in firefox and see if it's turned off.Look for this line-> browser.cache.disk.enable < should be true for on.
I have mine setup not to use disk cache, cause i have 1gig of ram and i want it to use that insted of the slower drive.

---

### Post by almostalive on 2007-09-15
I have the same issue..
@kerry_s, i checked the config, and it's enabled.

it saves files in the cache normally, but when i exit firefox, the cache gets deleted.. it's strange. firefox caching works fine on windows (i'm dual booting)

is wwwoffle a localized proxy that caches pages for you? hmm I guess i'll have to try it out. thanks

---

