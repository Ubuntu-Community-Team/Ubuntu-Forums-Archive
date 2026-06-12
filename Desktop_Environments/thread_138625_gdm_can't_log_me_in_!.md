---
title: "gdm can't log me in !"
date: 2006-03-02
forum: Desktop Environments
---

### Post by motu on 2006-03-02
hi there!
i've got a little problem with gdm, i can't log in.
gdm says it can't write my authorization file (which is .Xauthority), an it could be a spacedisk problem.
well it's not a space problem...
i've tried removing .Xauthority and .ICEauthority but it still the same thing...

any idea?

thanks

motu

---

### Post by motu on 2006-03-02
solved, it seems having chown /tmp/.X0* have changed everything....
strange ! i had already done that...

sorry for this useless thread guys

motu

---

