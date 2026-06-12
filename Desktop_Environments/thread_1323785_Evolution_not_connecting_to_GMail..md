---
title: "Evolution not connecting to GMail."
date: 2009-11-12
forum: Desktop Environments
---

### Post by ProgramErgoSum on 2009-11-12
I am able to get Evolution connect to my GMail account from my home network. But, at work, I keep getting a 'Connection refused' message. Where do I start looking for the problem ?

---

### Post by dvlchd3 on 2009-11-12
Perhpas your work blocks the POP and SMTP ports.  I know I'm unable to download my Gmail messages from work.

Try tcptraceroute (you will need to install the 'traceroute' package by your favorite method. i.e. sudo apt-get install traceroute)

```

tcptraceroute pop.gmail.com 995

```

This will show you when the connection gets lost.  If it happens within your company's network, then your company blocks incoming SSL pop traffic...

---

### Post by ProgramErgoSum on 2009-11-14
Yes, I think, that is indeed the case here. Too bad.

Thanks for your time.

---

