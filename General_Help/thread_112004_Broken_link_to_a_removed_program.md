---
title: "Broken link to a removed program"
date: 2006-01-03
forum: General Help
---

### Post by Snaip on 2006-01-03
Greets

After removing a compiled build of 'devilspie' I ran into a problem that there still exists a link of somekind into it.

snaip@hbkx:~$ devilspie
bash: /usr/local/bin/devilspie: No such file or directory

Whereas it should just say "command not found". I've searched from /bin, /usr/bin, /usr/sbin.. no luck. I ran a perl script used for searching broken symbolic links. 158 found, no devilspie. 

So I assume im missing a place in my search. Anyone? ;)

---

### Post by steve.horsley on 2006-01-03
try:
  which devilspie
and
 find / -name devilspie 2>/dev/null

---

