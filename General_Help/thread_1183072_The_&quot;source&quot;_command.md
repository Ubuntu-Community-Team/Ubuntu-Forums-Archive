---
title: "The &quot;source&quot; command"
date: 2009-06-09
forum: General Help
---

### Post by The Switch Blade on 2009-06-09
$ source $iraf/unix/hlib/irafuser.csh
bash: /iraf/iraf//unix/hlib/irafuser.csh: line 10: syntax error near unexpected token `else'
bash: /iraf/iraf//unix/hlib/irafuser.csh: line 10: `else if (-f /etc/SuSE-release) then'

what should I do instead?

---

### Post by baseface on 2009-06-09
source is for bash. you are running source on csh scripts. try "rehash" instead.

---

### Post by The Switch Blade on 2009-06-09
bash: rehash: command not found

---

### Post by baseface on 2009-06-09
dude, why are you running csh scripts from bash? it doesnt work.
you need to be using csh to run csh scripts.

---

