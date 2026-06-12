---
title: "Aterm character set problem"
date: 2006-04-28
forum: Desktop Environments
---

### Post by Mizutsuki on 2006-04-28
I've had this persistant issue that I'd love to get cleared up if I could.  I like using aterm but certain programs end up looking very strange, most notably gcc (which puts out just a ton of garbage characters in the middle of more meaningful stuff) and ncurses based aps (which do all kind of strange things.)  See the attached picture to understand what it is that I'm talking about.
Any thoughts on how I might fix this?
Thank you,
Stephen Cilley

---

### Post by Mizutsuki on 2006-04-29
*bump*

---

### Post by Mizutsuki on 2006-04-30
*bump* *bump*

---

### Post by Mizutsuki on 2006-04-30
I resolved the problem by adding the line
export LANG=en_US
to both my ~/.bashrc and my ~/.profile

Best of luck,
Stephen Cilley

---

### Post by paganini on 2006-06-04
Your problem is that aterm does not support the UTF-8 character set. When you set the charset variable before invoking aterm, you're in fact telling aterm to uso ISO-8859-1 instead of UTF-8. A more permanent solution would be to use:

[INDENT]dpkg-reconfigure locales[/INDENT]

And use ISO-8859-1 as your default charset.

Note that this will **not** work in dapper! Dapper requires you to change /var/lib/locales/supported.d/local to contain "en_US ISO-8859-1" and re-run locale-gen.

-- Paga

---

