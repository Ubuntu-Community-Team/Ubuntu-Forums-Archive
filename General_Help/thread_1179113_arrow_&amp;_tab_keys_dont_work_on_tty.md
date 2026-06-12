---
title: "arrow &amp; tab keys dont work on tty"
date: 2009-06-05
forum: General Help
---

### Post by krotus on 2009-06-05
Hi, I have problem with special keys on ttys and virtual consoles. For example up arrow prints ^[[A so I cant acces history and navigate on command prompt, tab just prints couple of spaces so I have no bash completetion. How can I fix this? Thx in advance.

---

### Post by The Cog on 2009-06-05
Maybe you ended up in sh instead of bash. Does the command **bash** work? If so, check your entry in /etc/passwd and make sure your login shell is /bin/bash and not /bin/sh.

---

