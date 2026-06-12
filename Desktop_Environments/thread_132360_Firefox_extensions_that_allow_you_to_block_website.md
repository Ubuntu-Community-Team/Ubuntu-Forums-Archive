---
title: "Firefox extensions that allow you to block websites?"
date: 2006-02-18
forum: Desktop Environments
---

### Post by chimera on 2006-02-18
Does anyone know a good firefox extension that allows you to block firefox from displaying certain websites?

---

### Post by ember on 2006-02-18
Hmm ... what befenit would that have? Anyway, you can block all elements from a site with Adblock/Plus.

---

### Post by chimera on 2006-02-18
Because I don't want a certain person who uses my computer to view certain websites.

---

### Post by ember on 2006-02-18
Well, I suspected that - yet, this person can easily disable your blocking of that site, so I recommend setting up a proxy and blocking the page there or look for such a technique in your router.
You also may use /etc/hosts and enter something like 
[www.block-this-site.com](www.block-this-site.com)             127.0.0.1

---

### Post by Bragador on 2006-02-18
If the person really want to see that webstite, she'll go to a friend's house and see it, ot go restart the computer in safe mode and see it.

You can't hide information, you can only delay the inevitable.

---

### Post by chimera on 2006-02-18
ember, could you explain the /ect/hosts method in detail?

Bragador: I'm not hiding information, I'm protecting from lies.

---

### Post by curtis on 2006-02-18
[QUOTE=ember]Well, I suspected that - yet, this person can easily disable your blocking of that site, so I recommend setting up a proxy and blocking the page there or look for such a technique in your router.
You also may use /etc/hosts and enter something like 
[www.block-this-site.com](www.block-this-site.com)             127.0.0.1[/QUOTE]
I would suggest using 0.0.0.0 rather than 127.0.0.1, as then it just does not load rather than timing out.
And you are null-routing it, rather than pointing it to localhost.

---

### Post by bjweeks on 2006-02-18
or they could disable the firefox extension.

---

### Post by chimera on 2006-02-18
[QUOTE=curtis]I would suggest using 0.0.0.0 rather than 127.0.0.1, as then it just does not load rather than timing out.
And you are null-routing it, rather than pointing it to localhost.[/QUOTE]


Thanks, that worked.

And they can't even disable the block without knowing my password (which they need to edit /etc/hosts):-D

---

