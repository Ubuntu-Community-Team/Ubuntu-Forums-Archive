---
title: "[Unsolved] Whitelist &quot;fglrx&quot; in Compiz-Fusion 0.6.2"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by Supersaiyan.IV on 2007-10-30
Hey

Successfully compiled compiz-fusion, and it runs fabulous on the 8.42.3 AIGLX ATI driver. But I can only start compiz fusion from shell using:

```

LIBGL_ALWAYS_INDIRECT=true compiz --replace --sm-disable --indirect-rendering ccp &

```

I've put this as a startup script in Sessions, but it won't work. Therefore I think the driver whitelisting is not working properly.

~/.config/compiz/compiz-manager
```

WHITELIST="fglrx"
SKIP_CHECKS=yes
LIBGL_ALWAYS_INDIRECT=true

```

This file might be the remains of the old compiz-manager that was built into Gutsy. I want to know how to bloody locate the proper file, since Gutsy doesn't have a good file search function to save it's life.

Any ideas?

---

### Post by SorinN on 2007-11-02
Yep, 

the correct path for Gutsy :  /etc/xdg/compiz/compiz-manager

---

