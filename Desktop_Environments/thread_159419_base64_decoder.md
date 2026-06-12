---
title: "base64 decoder?"
date: 2006-04-12
forum: Desktop Environments
---

### Post by enigma_0Z on 2006-04-12
I'm looking for a base64 decoder, a free one. Poking around in synaptic, tcllibs is supposed to have one, but I can't seem to figure out how to use it.

All I want to do is convert a string from base64 to ascii or at least binary. Is this even possible?

To make it a little more simple, here's an example command line that I would use:

```
decode -t base64 <base64 string stuff>
```

---

### Post by nemequ on 2006-04-12
There's probably a less bloated solution, but if you install php5-cli:

```
php -r 'echo base64_decode($argv[1]);' SGVsbG8sIHdvcmxkIQ
```

---

