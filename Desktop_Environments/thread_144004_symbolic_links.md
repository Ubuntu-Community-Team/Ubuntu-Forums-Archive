---
title: "symbolic links"
date: 2006-03-13
forum: Desktop Environments
---

### Post by lex1 on 2006-03-13
I have opened a directoy /var/lb/mixmaster/mix where the fliles are written in red with a black filter over them linking them to another directory, If I try to open mix.cfg with emacs and save the file it gives the comand not such file or directory

mix.cfg - >/etc/mixmaster/rem.conf
update.conf - >/etc/mixmaster/update.conf


lex1:D

---

### Post by 5-HT on 2006-03-13
mix.cfg looks like a symlink to /etc/mixmaster/rem.conf (it's just a placeholder pointing to that file).

If you want to edit it, try editing the target (/etc/mixmaster/rem.conf) with emacs.
The same applies to update.conf

HTH

---

