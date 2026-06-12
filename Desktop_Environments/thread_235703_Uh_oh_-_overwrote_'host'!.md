---
title: "Uh oh - overwrote 'host'!"
date: 2006-08-13
forum: Desktop Environments
---

### Post by Sslaxx on 2006-08-13
Intending to copy a 'hosts' file to /etc, I managed to overwrite host instead. How system-breaking is this, and could someone post the contents of a normal host file? Thanks!

---

### Post by llamakc on 2006-08-13
There isn't one.

There's an /etc/host.conf though.

Here's mine:

```

order hosts,bind
multi on

```

---

### Post by kerry_s on 2006-08-13
Just put> 127.0.0.1  localhost <in it and it should work. My hosts file is to long to post since i use it for adblocking. The original only had that line and some ipv6 related lines.

---

